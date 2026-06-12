---
title: "Changing Apache settings"
date: 2011-11-12
forum: General Help
---

### Post by horseatingweeds on 2011-11-12
I installed Apache2 using tasksel. Now I'm not sure how to make setting changes. I assumed that the (blank) httpd.conf file was for this. So I added the following directives:

ServerAdmin horseatingweed-at-gmail.com
ServerName stupidServer

-restart-

But when I examine the output of phpinfo() (a php function that ouputs server configuration) nothing indicates a change. SERVER_NAME is still localhost and SERVER_ADMIN is still webmaster@localhost

So then I tried editing the apache2.conf file. I put "ServerName stupidServer" in the very top, restarted, and phpinfo() was still the same. Then I put it in the bottom of apache2.conf, restarted, still no change. 

I understand the Apache setup on Ubuntu isn't the regular straight-forward way of doing it. So what am I missing? How is Apache on Ubuntu supposed to have settings adjusted?

Thanks.

---

