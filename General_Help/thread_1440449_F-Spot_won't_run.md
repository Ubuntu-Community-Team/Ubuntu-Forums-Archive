---
title: "F-Spot won't run"
date: 2010-03-27
forum: General Help
---

### Post by Chuck_N on 2010-03-27
using 9.10 Karmic Koala
I have a folder of JPGs. Rightclick on one, choose Open With F=Spot. A small window opens. Then a larger one, identifying the F-Spot program. Then everything goes away.  Or I go to 
 Applications/Graphics/F-SpotPhotoManager the same thing happens: 
     small window, big window, gone.

Any ideas on how to get it to run?

---

### Post by HC48 on 2010-05-10
Hello,
I have a similar problem since I installed Lucid, ie. F-spot won't open in the graphics menu. It opens if I type "sudo f-spot" in the terminal. I have tried delete/install using the graphic interface and synaptic packages to no avail...
I have read the other thread too:
([http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot](http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot))
Luckily I have GIMP :)
Hope someone can help.
H :)

---

### Post by michy99 on 2010-05-10
Try this:```
rm -R ~/.config/f-spot
rm -R ~/gconf/apps/f-spot
```Then try to run it again.

---

### Post by Chuck_N on 2010-05-10
[COLOR=Red]> **HC48 said:**
> Hello,
I have a similar problem since I installed Lucid, ie. F-spot won't open in the graphics menu. It opens if I type "sudo f-spot" in the terminal. I have tried delete/install using the graphic interface and synaptic packages to no avail...
I have read the other thread too:
([http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot](http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot))
Luckily I have GIMP :)
Hope someone can help.
H :)[/COLOR]

Interesting.  I just updated 9.10 and installed Lucid; in total a long and scary process. But it seems to work right.  AND I now have F-Spot working.

---

### Post by Wtwine on 2010-05-20
The solution suggested by mich99 worked for me - thanks!  F-spot works now.  Why did I have to do this I on my fresh installation of Lucid netbook remix on my new netbook?  I'm still learning Linux so I don't quite understand what the issue was.

---

### Post by domen62 on 2010-06-05
I had the same problem with 10.04 Lucid Lynx. mich99 solution worked fine for me. Thanks

---

### Post by HC48 on 2012-06-24
later... a lot later... I have discovered gThumb which is great and even recognises my Kodak Easyshare C703 with which I was having touble getting to download photos from the internal memory when my memory card died!
Hope this helps others.

---

