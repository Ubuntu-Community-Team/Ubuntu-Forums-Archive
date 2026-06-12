---
title: "Wubi Google Talk plugin doesn't work"
date: 2012-08-31
forum: General Help
---

### Post by ppdjoy on 2012-08-31
Hi

I recently installed Wubi (Ubuntu) on my Windows 7 machine. I installed most of the commonly used softwares that I need, i.e. Skype, Chrome, jDownloader etc. But when I tried to install [Google Talk/Voice plugin]("https://www.google.com/chat/video/download.html"), I was unsuccessful. Everytime I try to install, the Ubuntu Software Center opens up to install. But after I click "Install", it just does the 100% process only to return to previous uninstalled view.

The following shows what happens:

[IMG]http://i.imgur.com/X2I9F.png[/IMG]

[IMG]http://i.imgur.com/L54Ex.png[/IMG]

[IMG]http://i.imgur.com/NULS4.png[/IMG]

[IMG]http://i.imgur.com/X2I9F.png[/IMG]


Thanks in advance.........

---

### Post by gandaran on 2012-08-31
did you choose/download the right architecture file for your system?
also I recommend using gdebi to install packages instead of software center, works better!
```
sudo apt-get install gdebi
```
then right click the file to choose install with gdebi

---

### Post by ppdjoy on 2012-10-15
Thanks. Gdebi solved the problem.

---

