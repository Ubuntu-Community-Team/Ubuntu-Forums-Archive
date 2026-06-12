---
title: "Web interface for vsftp"
date: 2011-07-06
forum: General Help
---

### Post by Jonny87 on 2011-07-06
I'm not sure where to put this so Moderators feel free to move accordingly.

I'm currently running vsftp on my system serving files to selected family and friends, it is all set how I want it and users can access it fine from a web browser. However I want a nice web interface to make it slightly more user friendly and allow uploading. The building of the web pages I can do, what I'm not sure about though is the integrating of the web page to the vsftp.

I'm guessing that I'll need to setup and install something like Apache though I've never configured webserver from scratch before. Or does anyone have any other suggestions on how to accomplish this?

---

### Post by An Sanct on 2011-07-06
There is a GUI tool for KDE [kvsftpdmanager]("http://linux.softpedia.com/progDownload/KVsftpdManager-Download-14207.html").

---

### Post by aeiah on 2011-07-06
if you're expecting them to upload large files, it really would be best just to get them to install filezilla or something so any timeouts or disconnections can resume nicely

---

### Post by Jonny87 on 2011-07-06
> **aeiah said:**
> if you're expecting them to upload large files, it really would be best just to get them to install filezilla or something so any timeouts or disconnections can resume nicely

I don't think they'll upload anything much bigger than a photo. I will get some of them to use filezilla but for that will just confuse them even more so. For them I want to try and keep it simple and in a familia environment such as their web browser.

@ An Sanct;
I'm going to check out that kvsftpmanager thanks.

---

### Post by An Sanct on 2011-07-06
To get your settings via GUI, use kvsftpdmanager

and 

To get upload simple and easy (also multi-file) use [uploadify]("http://www.uploadify.com/documentation/")

---

