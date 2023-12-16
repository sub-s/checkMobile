# checkMobile
Mobile checked css add
접속한 디바이스가 모바일인지 피씨 인지를 체크해서 CSS를 동적으로 추가한다.

``
* 스크립트 에러나면 박살난다.
``

```
// css경로 
const mobileCSSPath = '../css/mobile.css';

// 디바이스 체크 함수
function isMobileDevice() {
    return /android|webos|iphone|ipad|ipod|blackberry|iemobile|opera mini/i.test(navigator.userAgent.toLowerCase());
}

// 동적으로 CSS 파일 추가
function addCSS(file) {
    var link = document.createElement('link');
    link.rel = 'stylesheet';
    link.type = 'text/css';
    link.href = file;
    link.id = 'dynamic-css';  // 모바일 CSS를 삭제할 때 식별하기 위한 ID 부여
    document.head.appendChild(link);
}

// 동적으로 CSS 파일 삭제
function removeCSS() {
    var cssElement = document.getElementById('dynamic-css');
    if (cssElement) {
        cssElement.parentNode.removeChild(cssElement);
    }
}

// 디바이스 체크 후 CSS 동적으로 추가 또는 삭제
if (isMobileDevice()) {
    addCSS(mobileCSSPath);
} else {
    removeCSS();
}
```

PC로 접속할 경우 Mobile.css를 remove를 한다.

