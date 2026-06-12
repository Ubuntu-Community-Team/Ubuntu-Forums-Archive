---
title: "Trouble with opening certain websites under ubuntu"
date: 2011-08-16
forum: General Help
---

### Post by micdhack on 2011-08-16
I have a weird problem with opening certain websites under ubuntu. I tried at windows and i have no problem. The DNS in windows is my modem 192.168.1.1 but under linux for some strange reason this won't fly.

For example youtube.com won't open on firefox, but ping and traceroute works just fine.

Any ideas how to troubleshoot the problem?

UPDATE: ping and traceroute doesnt work for [www.youtube.com](www.youtube.com) but only for youtube.com
After using lynx this is what i got back
> micdhack@micdhack-laptop:~$ lynx youtube.com
Looking up  'youtube.com' first

Looking up youtube.com first
Looking up youtube.com
Making HTTP connection to youtube.com
Sending HTTP request.
HTTP request sent; waiting for response.
HTTP/1.0 301 Moved Permanently
Data transfer complete
HTTP/1.0 301 Moved Permanently
Using [http://www.youtube.com/](http://www.youtube.com/)
Looking up [www.youtube.com](www.youtube.com)
Unable to locate remote host [www.youtube.com](www.youtube.com).
Alert!: Unable to connect to remote host.

lynx: Can't access startfile [http://youtube.com/](http://youtube.com/)


Is there a way to use another dns than the one that i get from my internet provider?

---

### Post by lmarmisa on 2011-08-16
> **micdhack said:**
> I have a weird problem with opening certain websites under ubuntu. I tried at windows and i have no problem. The DNS in windows is my modem 192.168.1.1 but under linux for some strange reason this won't fly.

For example youtube.com won't open on firefox, but ping and traceroute works just fine.

Any ideas how to troubleshoot the problem?

UPDATE: ping and traceroute doesnt work for [www.youtube.com]("http://www.youtube.com") but only for youtube.com
After using lynx this is what i got back


Is there a way to use another dns than the one that i get from my internet provider?

Try to use the Google public DNS addresses 8.8.8.8 and 8.8.4.4 

[http://code.google.com/intl/en/speed/public-dns/docs/using.html](http://code.google.com/intl/en/speed/public-dns/docs/using.html)

---

### Post by micdhack on 2011-08-16
Imarmisa i tried it and it works great! 1000x thanks :-)

---

### Post by lmarmisa on 2011-08-16
Great!!!!. :D

Please, mark the thread as SOLVED (look at Thread Tools).

---

