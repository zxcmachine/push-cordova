ПУШИ ДЛЯ IOS ЧИТАЕМ ВНИМАТЕЛЬНО ОЧЕНЬ ВНИМАТЕЛЬНО
cordova plugin add cordova-plugin-firebase-messaging —> отсюда решаем все вытекающие проблемы которые появятся при установке
регаем Google.plist - как по документации
создаем init.js и туда фигачим 
export default () => {
    console.log('tokeng','sssssssssssssssssss')
    
    document.addEventListener('deviceready' , async () => {
        const requestPermission = await cordova.plugins.firebase.messaging.requestPermission();
        const token = await cordova.plugins.firebase.messaging.getToken()
        console.log(token,'sssssssssssssssssss')
        localStorage.setItem('fcm-token' , JSON.stringify(token))
    })
 }
как только xcode нам забилдил - добавляем файл google.plist прямо в корень через xcode в корень уже забилженного - важно!!
далее при билде в xcode добавляем файл google.plist в BuildPhases—>Compile Sources
вуаля - работает
