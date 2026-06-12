---
title: "hyperlinks in other programs do not open in firefox!"
date: 2006-04-13
forum: General Help
---

### Post by sgleo87 on 2006-04-13
When I click on hyperlinks in emails in Thunderbird or in Xchat they do not open in firefox. I have tried different settings in preferred applications (firefox, firefox %s, firefox %u) but nothing has worked so far. Please help! :(

---

### Post by daedalusman on 2006-04-13
I just want to add that I have had this problem since I installed Ubuntu. I have no idea how to fix this either, I just copy link location and past into address bar but this is a bit annoy. Can someone shed some light on this issue, thanks.

---

### Post by dcstar on 2006-04-13
Check:

Applications-System Tools-Configuration Editor-Desktop-Gnome-url-handlers

and make sure the various **http** & **https** ones are set to the right place (and other ones as well).

---

### Post by heislord5 on 2006-04-13
Dcstar's instructions worked for me...same problem.

I went through everything in that folder.  Because I had upgraded my firefox version it may have still been trying to invoke the wrong thing.  So I changed everywhere under url-handlers everything that had:

mozilla-firefox %s
to
firefox %s

---

### Post by sgleo87 on 2006-04-14
Unfortunately that didn't work for me. All the keys were correct and had firefox %s (I did upgrade to 1.5 also).

---

### Post by dcstar on 2006-04-14
[QUOTE=sgleo87]Unfortunately that didn't work for me. All the keys were correct and had firefox %s (I did upgrade to 1.5 also).[/QUOTE]
Just plain "firefox" may still try to open the old version.

If you put in the whole path to the new version of Firefox it might work differently.

---

### Post by John Jason Jordan on 2006-04-14
I have a variation on this problem. I use Gnome, but I also have a lot of KDE apps installed, including Konqueror. However, I use Firefox exclusively for browsing. Yet, when I double-click on a link in an e-mail or elsewhere, up pops Konqueror.

I went into the Configuration Editor as recommended in this thread. All the settings were already set to Firefox. Nevertheless, I get Konqueror when I double-click on a link. 

Does anyone have any idea how to get Ubuntu to launch Firefox instead of Konqueror?

---

### Post by sgleo87 on 2006-04-14
[QUOTE=dcstar]Just plain "firefox" may still try to open the old version.

If you put in the whole path to the new version of Firefox it might work differently.[/QUOTE]


I put /opt/firefox/firefox %s and that didn't help either...unfortunately :(

---

### Post by dcstar on 2006-04-14
[QUOTE=John Jason Jordan]
.......
Does anyone have any idea how to get Ubuntu to launch Firefox instead of Konqueror?[/QUOTE]

The only thing I can suggest is you do a full search of your system for files containing the Konqueror string.

One you find the relevant file, you might be able to manually edit it.

---

### Post by aysiu on 2006-04-14
[This](http://www.ubuntuforums.org/showthread.php?t=60427) might help.

---

### Post by sgleo87 on 2006-04-14
[QUOTE=aysiu][This](http://www.ubuntuforums.org/showthread.php?t=60427) might help.[/QUOTE]

THANK YOU!!!! adding the code to the thunderbird prefd.js file solved it for me :D

---

### Post by daedalusman on 2006-04-16
Yeah that code did the job nicely for me as well, thanks.

---

