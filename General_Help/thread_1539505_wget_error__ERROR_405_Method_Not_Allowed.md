---
title: "wget error : ERROR 405: Method Not Allowed"
date: 2010-07-26
forum: General Help
---

### Post by techbrainless on 2010-07-26
Hi All,

I have executed the command 
```
sudo wget -r -Nc -mk http://code.google.com/codejam/
```(refering the site : [http://linuxpoison.blogspot.com/2010/06/download-entire-website-using-wget-for.html](http://linuxpoison.blogspot.com/2010/06/download-entire-website-using-wget-for.html)) for downloading entire website using wget for offline viewing on Linux,

at the middle of download i have shutdown my laptop (downloading was not over) , and when i started my laptop again , i have executed the same command to continue downloading but i have got the error :

```
test@test-laptop:/data/Applications/sites/googlejam$  sudo wget -r -Nc -mk http://code.google.com/codejam/
--2010-07-25 19:41:32--  http://code.google.com/codejam/
Resolving code.google.com... 209.85.227.100, 209.85.227.101, 209.85.227.102, ...
Connecting to code.google.com|209.85.227.100|:80... connected.
HTTP request sent, awaiting response... 405 Method Not Allowed
2010-07-25 19:41:33 ERROR 405: Method Not Allowed.

Converted 0 files in 0 seconds.
test@test-laptop:/data/Applications/sites/googlejam$ 



```

---

### Post by limestone on 2010-07-26
try without sudo.
wget -r -Nc -mk [http://code.google.com/codejam/](http://code.google.com/codejam/)

---

### Post by limestone on 2010-07-26
Also, this software download entire sites.
[http://www.httrack.com/](http://www.httrack.com/)
sudo apt-get install httrack

---

### Post by techbrainless on 2010-07-26
thanks pont.andersson for the reply.

[HTML]try without sudo.
wget -r -Nc -mk http://code.google.com/codejam/[/HTML]
try without sudo ???? 


[HTML]Also, this software download entire sites.
http://www.httrack.com/
sudo apt-get install httrack 	[/HTML]
1) I have already tested wget for some small sites and it worked fine , i was downloading the sites using wget all at once , but since the site [http://code.google.com/codejam]("http://code.google.com/codejam/") is too big , it took long time and i have prefered to rest my laptop by shutting down it and restarted it after sometime. 
2) i have already downloaded around 650 mb of the site [http://code.google.com/codejam/](http://code.google.com/codejam/) , so using httrack i might need to start downloading from the begining.

---

### Post by techbrainless on 2010-07-26
Any reply........

---

### Post by techbrainless on 2010-07-27
Any suggestions?

---

### Post by limestone on 2010-07-27
Oh, sorry... I misunderstood the problem.. 
Maybe the logfile or something messed it up? 
Type wget --help to checkout the options again..

---

### Post by techbrainless on 2010-07-27
thanks  pont.andersson for your reply ...

I have  added option to continue downloading (-c)
but am getting the same error....

---

### Post by limestone on 2010-07-27
Sorry can't help you solve it :/
Anyone else here that manages wget??

---

