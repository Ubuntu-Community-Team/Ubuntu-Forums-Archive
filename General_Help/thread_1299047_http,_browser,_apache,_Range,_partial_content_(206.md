---
title: "http, browser, apache, Range, partial content (206)"
date: 2009-10-23
forum: General Help
---

### Post by mauricebis on 2009-10-23
Hi,
Until recently, I had my local server Apache2.2.8 working properly on Ubuntu Hardy and could display a web page through [http://localhost/mypage](http://localhost/mypage) (.php or .htm). 

Don't know what I did or not (possibly a recommended update), browsers no longer display the pages on localhost properly, it loads the first page if .php (so it isn't a php pb), but then doesn't display the rest properly (image files, css file...), if it's an .htm page, it isn't displayed. 

I had a look at the live headers exchanged, surprisingly, the GET for the CSS file is a Range request, to which Apache seems to answer properly with a 206 partial content response. Now, the browser (and it's true in the different browsers I've installed) doesn't seem to get the proper content. If I were working on-line, the initial GET wouldn't be a Range request but the full page and the browser displays it properly.

I cleared the caches. Still the same.

Any ideas as to where to look? Thanks.

I add an extract of the live headers exchange under FireFox:

GET /newwebab/index.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.14) Gecko/2009090216 Ubuntu/8.04 (hardy) Firefox/3.0.14 FirePHP/0.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive

HTTP/1.x 200 OK
Date: Fri, 23 Oct 2009 11:19:54 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.7 with Suhosin-Patch
X-Powered-By: PHP/5.2.4-2ubuntu5.7
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: text/html
----------------------------------------------------------
[http://localhost/newwebab/styles.css](http://localhost/newwebab/styles.css)

GET /newwebab/styles.css HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.14) Gecko/2009090216 Ubuntu/8.04 (hardy) Firefox/3.0.14 FirePHP/0.3
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://localhost/newwebab/index.php](http://localhost/newwebab/index.php)
Range: bytes=0-
If-Range: "14-36b8-46ee9ac2e6680"

HTTP/1.x 206 Partial Content
Date: Fri, 23 Oct 2009 11:19:54 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.7 with Suhosin-Patch
Last-Modified: Fri, 17 Jul 2009 16:56:42 GMT
Etag: "14-36b8-46ee9ac2e6680"
Accept-Ranges: bytes
Content-Length: 14008
Content-Range: bytes 0-14007/14008
Keep-Alive: timeout=15, max=99
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------

---

