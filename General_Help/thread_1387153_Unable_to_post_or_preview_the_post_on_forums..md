---
title: "Unable to post or preview the post on forums."
date: 2010-01-21
forum: General Help
---

### Post by dakiru on 2010-01-21
Hi, everyone!

Now I am using Ubuntu Studio 9.10 amd64. I didn't setup or install anything, so it's clean installation.

The problem is that I am not able to post or to preview the posts on the forums, same as upload images to the image hosting sites (like imageshack). Even here, on ubuntuforums.org, I was unable to upload the the tiny .jpeg - Connection time out. On other forums (phpbb, for example) Firefox offers me to save or open the posting.php. I tried the different browsers after - no success.

Just to point out that I experienced the exactly same problem on the same PC under Ubuntu 9.04 amd64.

I really don't know what information to collect or where to look to solve this nasty problem. And after googling I have found just nothing.

Everything mentioned above works in Windows 7, Firefox, on the same PC but this is not a solution, is it? :D

Thank you for any tips! :)

---

### Post by lisati on 2010-01-21
You've managed to post a thread here. It's possible that part of the problem is that you might have been trying to post to an archive.

---

### Post by dakiru on 2010-01-21
> **lisati said:**
> You've managed to post a thread here. It's possible that part of the problem is that you might have been trying to post to an archive.

No-no, I know that archive is read only :) If you mean that..

Plus, it is the problem on all forums that I tried. I am able to log in, but not to post. Or edit my post that I wrote before.

---

### Post by philinux on 2010-01-21
> **dakiru said:**
> Hi, everyone!

Now I am using Ubuntu Studio 9.10 amd64. I didn't setup or install anything, so it's clean installation.

The problem is that I am not able to post or to preview the posts on the forums, same as upload images to the image hosting sites (like imageshack). Even here, on ubuntuforums.org, I was unable to upload the the tiny .jpeg - Connection time out. On other forums (phpbb, for example) Firefox offers me to save or open the posting.php. I tried the different browsers after - no success.

Just to point out that I experienced the exactly same problem on the same PC under Ubuntu 9.04 amd64.

I really don't know what information to collect or where to look to solve this nasty problem. And after googling I have found just nothing.

Everything mentioned above works in Windows 7, Firefox, on the same PC but this is not a solution, is it? :D

Thank you for any tips! :)

Are you behind a proxy?

---

### Post by dakiru on 2010-01-21
> **philinux said:**
> Are you behind a proxy?

I think no. No proxy on the router, no proxy in the network settings in Ubuntu.

Do I have to check something else? Thank you.

---

### Post by philinux on 2010-01-21
> **dakiru said:**
> I think no. No proxy on the router, no proxy in the network settings in Ubuntu.

Do I have to check something else? Thank you.

Ok. Can access the rest of the web ok?

And can you login ok and use say msn hotmail or other?

---

### Post by dakiru on 2010-01-21
> **philinux said:**
> Ok. Can access the rest of the web ok?

And can you login ok and use say msn hotmail or other?

Yes, all the websites I tried work perfectly. And ICQ (Empathy) and Gmail - works. Maybe the log from the Live HTTP Header (Firefox plugin) may help, while I try to post?

---

### Post by philinux on 2010-01-21
> **dakiru said:**
> Yes, all the websites I tried work perfectly. And ICQ (Empathy) and Gmail - works. Maybe the log from the Live HTTP Header (Firefox plugin) may help, while I try to post?

Ok then try this. In firefox, tools>clear recent history. Tick all the boxes to clear everything including cookies.

---

### Post by dakiru on 2010-01-21
> **philinux said:**
> Ok then try this. In firefox, tools>clear recent history. Tick all the boxes to clear everything including cookies.

Posting works here, but on other forums - not. 

Cleared the recent history, but still nothing.

---

### Post by dakiru on 2010-01-21
Now I entered the topic on the forum, where I wrote a post before and edited it. Before clicking "Submit" i cleared the Live HTTP Header log and a recent history in Firefox. Clicked "Submit" and from HTTP Header got this:


[http://www.google.com/uds/stats?r0=el%7Cjquery&nc=1264119476967_15028](http://www.google.com/uds/stats?r0=el%7Cjquery&nc=1264119476967_15028)
 
GET /uds/stats?r0=el%7Cjquery&nc=1264119476967_15028 HTTP/1.1
Host: [www.google.com]("http://www.google.com")
User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.7
Accept: image/png,image/*;q=0.8,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/content/auth](http://www.indigorenderer.com/content/auth)
 
HTTP/1.x 200 OK
Content-Type: image/gif
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: Fri, 01 Jan 1990 00:00:00 GMT
Date: Fri, 22 Jan 2010 00:17:53 GMT
X-Content-Type-Options: nosniff
X-XSS-Protection: 0
X-Frame-Options: SAMEORIGIN
Content-Length: 43
Server: GFE/2.0






Now it stucks for several minutes and offers to open or save posting.php after. Live HTTP Headers outputs this:






[http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=37c99e6b39342a953b255cdc171a6ee0&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=37c99e6b39342a953b255cdc171a6ee0&t=8020&p=90558)
 
POST /forum/posting.php?mode=edit&f=4&sid=37c99e6b39342a953b255cdc171a6ee0&t=8020&p=90558 HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com")
User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.7
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=37c99e6b39342a953b255cdc171a6ee0; __utma=259830354.217318231.1264119415.1264119415.1264119415.1; __utmb=259830354.12.10.1264119415; __utmc=259830354; __utmz=259830354.1264119415.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); SESS11e8347481e3a9a8a535c78b4c29f0cd=cc19300f29984e768d27fda7f2e729ca; DRUPAL_UID=2626
Content-Type: multipart/form-data; boundary=---------------------------8506852134417603361735966012
Content-Length: 1511
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="subject"
 
Re: Sofa scene
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="addbbcode20"
 
100
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="helpbox"
 
Tip: Styles can be applied quickly to selected text.
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="message"
 
Very nice scene !
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="attach_sig"
 
on
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="post"
 
Submit
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="fileupload"; filename=""
Content-Type: application/octet-stream
 
 
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="filecomment"
 
 
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="lastclick"
 
1264119815
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="creation_time"
 
1264119815
-----------------------------8506852134417603361735966012
Content-Disposition: form-data; name="form_token"
 
e94ad6bf5c6bbb59d79541a6a2485365c52b3b2e
-----------------------------8506852134417603361735966012--
 
HTTP/1.x 200 OK



I don't really know if this info is helpful to spot the problem..

P.S. The same thing happened now, when I tried to post this here on ubuntuforums. Even after clearing the recent history it offers me to save newreply.php

I tried Arora browser after, cleared the recent history too, but still - no success. I switched to Windows 7 and posted. This seems to be a long game :popcorn:
Thanks a bunch for any possible tips :)

P.P.S. The dialog window:

---

### Post by dakiru on 2010-01-22
Tried Ubuntu 9.10 Live and the exactly problem appears: web, IM, gmail, forum browsing and logging in those forums - ok, posting, post previewing etc. - not.

---

### Post by dakiru on 2010-01-22
Ok, now I tried the same topic editing in Win7, Firefox. To compare Live  HTTP Headers output. Submitting the change was OK and the output of this action is:



[URL="http://www.google.com/uds/stats?r0=el%7Cjquery&nc=1264165046084_15007"]```
[/URL][http://www.google.com/uds/stats?r0=el%7Cjquery&nc=1264165046084_15007](http://www.google.com/uds/stats?r0=el%7Cjquery&nc=1264165046084_15007)

GET /uds/stats?r0=el%7Cjquery&nc=1264165046084_15007 HTTP/1.1
Host: [www.google.com]("http://www.google.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: image/png,image/*;q=0.8,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/content/auth](http://www.indigorenderer.com/content/auth)
Cookie: PREF=ID=e80a0cb4532c4723:U=e9494be5cacb9adc:TM=1261779479:LM=1261854422:GM=1:S=AVeIxA2DtUht3Vli; NID=31=Qz85AtowBCtF5RREUCw5X-eK2bLwBSWoaPDlfUc3_GLTavFaOfsPKv8poVmTWIyOeYtoskB2RtoYPS5SpDCioQe0Zd8vrna81rDQ6ePWCAZlFlgu3t3W-4mTKe_bi9op; rememberme=true; SID=DQAAAJEAAAAaMoJ6WeP2s2IZ5x8lvVIm-R_NwEOxmQBd8LsUR7LFH5LHfvLFK-UdJkEeDIxM9IlPRHG43uQ_YLQXZXCG-Ku4jY1YXjNx_LY6CXIYynKwVoANQIDvSDlZsRjv1n71KrfPTZtmCwP4EYMxQYtS23tKGZRFKFr78NpKIGRr_CO9_4T2gydAskgSbeuicTiSRDZFJ-pzPpreZEjg1vSdH7L7; HSID=AJGJtarRmknQrPWQ9

HTTP/1.x 200 OK
Content-Type: image/gif
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: Fri, 01 Jan 1990 00:00:00 GMT
Date: Fri, 22 Jan 2010 13:57:26 GMT
X-Content-Type-Options: nosniff
X-XSS-Protection: 0
X-Frame-Options: SAMEORIGIN
Content-Length: 43
Server: GFE/2.0
----------------------------------------------------------
[http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558)

POST /forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558 HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
Content-Type: multipart/form-data; boundary=---------------------------9374110204596
Content-Length: 1331
-----------------------------9374110204596
Content-Disposition: form-data; name="subject"

Re: Sofa scene
-----------------------------9374110204596
Content-Disposition: form-data; name="addbbcode20"

100
-----------------------------9374110204596
Content-Disposition: form-data; name="helpbox"

Tip: Styles can be applied quickly to selected text.
-----------------------------9374110204596
Content-Disposition: form-data; name="message"

Very nice scene !
-----------------------------9374110204596
Content-Disposition: form-data; name="attach_sig"

on
-----------------------------9374110204596
Content-Disposition: form-data; name="post"

Submit
-----------------------------9374110204596
Content-Disposition: form-data; name="fileupload"; filename=""
Content-Type: application/octet-stream


-----------------------------9374110204596
Content-Disposition: form-data; name="filecomment"


-----------------------------9374110204596
Content-Disposition: form-data; name="lastclick"

1264168985
-----------------------------9374110204596
Content-Disposition: form-data; name="creation_time"

1264168985
-----------------------------9374110204596
Content-Disposition: form-data; name="form_token"

9a2d31dd2f59921bbee88dc16996ec189fbd08f0
-----------------------------9374110204596--

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:31 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
X-Powered-By: PHP/5.2.4-2ubuntu5.6
Cache-Control: private, no-cache="set-cookie"
Expires: 0
Pragma: no-cache
Vary: Accept-Encoding
Content-Encoding: gzip
Keep-Alive: timeout=2, max=50
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: text/html; charset=UTF-8
----------------------------------------------------------
[http://www.indigorenderer.com/forum/styles/minimal/theme/stylesheet.css](http://www.indigorenderer.com/forum/styles/minimal/theme/stylesheet.css)

GET /forum/styles/minimal/theme/stylesheet.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Thu, 06 Aug 2009 02:59:01 GMT
If-None-Match: "1f8a-470704d37e740"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:32 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Thu, 06 Aug 2009 02:59:01 GMT
Etag: "1f8a-470704d37e740"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:32 GMT
Content-Encoding: gzip
Content-Length: 2129
Keep-Alive: timeout=2, max=49
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------
[http://www.indigorenderer.com/media/reset.css](http://www.indigorenderer.com/media/reset.css)

GET /media/reset.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Fri, 20 Nov 2009 04:00:22 GMT
If-None-Match: "288-478c583cd4180"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:42 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Fri, 20 Nov 2009 04:00:22 GMT
Etag: "288-478c583cd4180"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:42 GMT
Content-Encoding: gzip
Content-Length: 395
Keep-Alive: timeout=2, max=50
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------
[http://www.indigorenderer.com/media/text.css](http://www.indigorenderer.com/media/text.css)

GET /media/text.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Fri, 20 Nov 2009 04:57:34 GMT
If-None-Match: "4e4-478c6505d6b80"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:42 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Fri, 20 Nov 2009 04:57:34 GMT
Etag: "4e4-478c6505d6b80"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:42 GMT
Content-Encoding: gzip
Content-Length: 506
Keep-Alive: timeout=2, max=50
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------
[http://www.indigorenderer.com/media/960.css](http://www.indigorenderer.com/media/960.css)

GET /media/960.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Fri, 20 Nov 2009 04:00:22 GMT
If-None-Match: "14bd-478c583cd4180"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:43 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Fri, 20 Nov 2009 04:00:22 GMT
Etag: "14bd-478c583cd4180"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:43 GMT
Content-Encoding: gzip
Content-Length: 996
Keep-Alive: timeout=2, max=50
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------
[http://www.indigorenderer.com/media/indigo.css](http://www.indigorenderer.com/media/indigo.css)

GET /media/indigo.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Tue, 05 Jan 2010 02:41:29 GMT
If-None-Match: "428f-47c61c664a840"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:43 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Tue, 05 Jan 2010 02:41:29 GMT
Etag: "428f-47c61c664a840"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:43 GMT
Content-Encoding: gzip
Content-Length: 3818
Keep-Alive: timeout=2, max=50
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------
[http://www.indigorenderer.com/content/auth](http://www.indigorenderer.com/content/auth)

GET /content/auth HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558](http://www.indigorenderer.com/forum/posting.php?mode=edit&f=4&sid=a2c771359b30031722e24031f01c9e6f&t=8020&p=90558)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Fri, 22 Jan 2010 14:03:09 GMT

HTTP/1.x 404 Not Found
Date: Fri, 22 Jan 2010 14:03:43 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
X-Powered-By: PHP/5.2.4-2ubuntu5.6
Expires: Sun, 19 Nov 1978 05:00:00 GMT
Last-Modified: Fri, 22 Jan 2010 14:03:43 GMT
Cache-Control: store, no-cache, must-revalidate, post-check=0, pre-check=0
Set-Cookie: DRUPAL_UID=2626; expires=Sun, 14-Feb-2010 17:37:03 GMT; path=/; domain=.indigorenderer.com
Content-Encoding: gzip
Content-Length: 2390
Keep-Alive: timeout=2, max=49
Connection: Keep-Alive
Content-Type: text/html; charset=utf-8
----------------------------------------------------------
[http://www.google.com/jsapi](http://www.google.com/jsapi)

GET /jsapi HTTP/1.1
Host: [www.google.com]("http://www.google.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: */*
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/content/auth](http://www.indigorenderer.com/content/auth)
Cookie: PREF=ID=e80a0cb4532c4723:U=e9494be5cacb9adc:TM=1261779479:LM=1261854422:GM=1:S=AVeIxA2DtUht3Vli; NID=31=Qz85AtowBCtF5RREUCw5X-eK2bLwBSWoaPDlfUc3_GLTavFaOfsPKv8poVmTWIyOeYtoskB2RtoYPS5SpDCioQe0Zd8vrna81rDQ6ePWCAZlFlgu3t3W-4mTKe_bi9op; rememberme=true; SID=DQAAAJEAAAAaMoJ6WeP2s2IZ5x8lvVIm-R_NwEOxmQBd8LsUR7LFH5LHfvLFK-UdJkEeDIxM9IlPRHG43uQ_YLQXZXCG-Ku4jY1YXjNx_LY6CXIYynKwVoANQIDvSDlZsRjv1n71KrfPTZtmCwP4EYMxQYtS23tKGZRFKFr78NpKIGRr_CO9_4T2gydAskgSbeuicTiSRDZFJ-pzPpreZEjg1vSdH7L7; HSID=AJGJtarRmknQrPWQ9

HTTP/1.x 200 OK
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: Fri, 01 Jan 1990 00:00:00 GMT
Date: Fri, 22 Jan 2010 13:57:45 GMT
Content-Type: text/javascript; charset=utf-8
Content-Encoding: gzip
X-Content-Type-Options: nosniff
X-XSS-Protection: 0
X-Frame-Options: SAMEORIGIN
Content-Length: 5351
Server: GFE/2.0
----------------------------------------------------------
[http://www.indigorenderer.com/media/960.css](http://www.indigorenderer.com/media/960.css)

GET /media/960.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/content/auth](http://www.indigorenderer.com/content/auth)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Fri, 20 Nov 2009 04:00:22 GMT
If-None-Match: "14bd-478c583cd4180"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:44 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Fri, 20 Nov 2009 04:00:22 GMT
Etag: "14bd-478c583cd4180"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:44 GMT
Content-Encoding: gzip
Content-Length: 996
Keep-Alive: timeout=2, max=49
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------
[http://www.indigorenderer.com/media/text.css](http://www.indigorenderer.com/media/text.css)

GET /media/text.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/content/auth](http://www.indigorenderer.com/content/auth)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Fri, 20 Nov 2009 04:57:34 GMT
If-None-Match: "4e4-478c6505d6b80"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:44 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Fri, 20 Nov 2009 04:57:34 GMT
Etag: "4e4-478c6505d6b80"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:44 GMT
Content-Encoding: gzip
Content-Length: 506
Keep-Alive: timeout=2, max=48
Connection: Keep-Alive
Content-Type: text/css
----------------------------------------------------------
[http://www.indigorenderer.com/media/reset.css](http://www.indigorenderer.com/media/reset.css)

GET /media/reset.css HTTP/1.1
Host: [www.indigorenderer.com]("http://www.indigorenderer.com/")
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.indigorenderer.com/content/auth](http://www.indigorenderer.com/content/auth)
Cookie: phpbbcoo_u=3559; phpbbcoo_k=; phpbbcoo_sid=a2c771359b30031722e24031f01c9e6f; __utma=259830354.1597131344.1261785826.1264165021.1264162697.243; __utmz=259830354.1263918485.222.4.utmcsr=blendernation.com|utmccn=(referral)|utmcmd=referral|utmcct=/indigo-renderer-2-2-released/; DRUPAL_UID=2626; SESS11e8347481e3a9a8a535c78b4c29f0cd=d47d97ebf19a89692bbd2ac305d6fcfd; __utmb=259830354.24.10.1264162697; __utmc=259830354
If-Modified-Since: Fri, 20 Nov 2009 04:00:22 GMT
If-None-Match: "288-478c583cd4180"-gzip

HTTP/1.x 200 OK
Date: Fri, 22 Jan 2010 14:03:44 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Phusion_Passenger/2.2.2
Vary: Cookie,Accept-Encoding
Last-Modified: Fri, 20 Nov 2009 04:00:22 GMT
Etag: "288-478c583cd4180"-gzip
Accept-Ranges: bytes
Cache-Control: max-age=1814400
Expires: Fri, 12 Feb 2010 14:03:44 GMT
Content-Encoding: gzip
Content-Length: 395
Keep-Alive: timeout=2, max=49
Connection: Keep-Alive
Content-Type: text/css
```

---

### Post by dakiru on 2010-01-23
The game continues :popcorn:
What I else tried:

Debian Live 5.02 Gnome (Live session) - no problems with posting and previewing. Just works as it has to

Xubuntu 9.10 (Live session) - doesn't work, same as in Ubuntu. After trying the Firefox in Xubuntu, I installed Elinks and tried the same. I didn't reach the needed result, but at least some output:
```

Unable to retrieve http://here-is-web-adress/forum/posting.php?mod=edit_alphanumericblablabla
(MULTIPART FORM DATA)
Error reading from socket
```


One more thing is, that I tried the same with the Live session in Ubuntu (x86) on the second PC in the same network. And it didn't work the same.

Plus, I tried public proxy a it didn't help

So, it's not hardware, it's not x64 issue, it's not Firefox issue, it's not Gnome issue.

Would appreciate any tips :)

---

### Post by dakiru on 2010-01-23
Tried Fedora 12 - same problem, so it's not Ubuntu family issue.

What I can assume: network interface, drivers..

Guys, any idea what to try or where to look? My head is melting :-\"

P.S. Sorry for bumping the thread.

---

### Post by jacebenson on 2010-02-14
I think I may be having a similar situation.  I can log in to most of the sites but some pages just return the Unable to Connect screen (in both Chrome and Firefox).

I think you are on the right track with thinking drivers or network issues.

The network interface card make/model, networking equipment might be a good place to start.  As this is only happening on this pc though I do not think it is past your NIC.

I am using my onboard NIC on my custom built pc from a few years ago.  The information I found using Hardware info (see sysinfo, may need to be installed)

Hardware->Network;
Ethernet controller
*Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 91)
Subsystem: Giga-byte Technology Device e000

Hopefully someone can figure this out.
While doing some searches I found some other forum topics that may be related to this;
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1371519]("http://ubuntuforums.org/showthread.php?t=1371519") - Some replies, sounds like user can load the page but once he logs in it logs him off and he cannot stay logged in for any period of time.
[*][http://ubuntuforums.org/showthread.php?t=1366959]("http://ubuntuforums.org/showthread.php?t=1366959") - No replies.  Sounds like he can load the page but when the user attempts to log in he is unable to and the browsers return a Unable to Connect screen.
[/LIST]

---

