---
title: "Apache 2 Post Method not allowed"
date: 2009-10-01
forum: General Help
---

### Post by jawad.ssuet on 2009-10-01
Hello,

I am trying to PUT one file through OpenXcap but it seems Apache 2.2.12 is not allowed PUT method. Following is the error. Can someone have some solution are there any special settings for appache.conf and httpd.conf.

xcapclient -i pres-rules Put

Complete Message
--------------------------------

405 Method not Allowed
content-type: text/html ; charset=iso-8859-1
content-length: 356
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<h1> Method Not Allowed </h1>
<p> The requested method PUT is not allowed for the URL /xcap-root/pres-rules/users/sip:alice@open-ims.test/index.</p>

<address> Apache 2.2.12 (Ubuntu) Server at open-ims.test Port 80 </address>
 </body></html>

---

### Post by Lekensteyn on 2009-10-01
Search for <Limit>-directives.

---

