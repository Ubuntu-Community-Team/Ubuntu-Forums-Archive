---
title: "problem related to USB and Gparted, unable to find mount point"
date: 2010-05-29
forum: General Help
---

### Post by hihihi100 on 2010-05-29
Hi there:

3 weeks ago I upgraded to 10.04 lucid, and since then, every time I mount an external hard drive I can access it (I mean it mounts automatically, copy and paste archives, and so on), but, if I go to Gparted, the screen will always show what you can see on the uploaded screenshot.

Now, why does that happen?

Unable to find mount point

Before you post any solutions, please keep in mind that, just yesterday, I executed 

```
sudo rm -r /media/usb* 

```Because before executing that command, I was able to used Gparted without problems, but lucid wouldnt recognize the label of the external drive...

Now the system mounts the external hard drive automatically, but Gparted shows what you can see on the screenshot

tips please

thx

The whole thread regarding the clommand can be seen here: [http://ubuntuforums.org/showthread.php?t=1495854](http://ubuntuforums.org/showthread.php?t=1495854)

---

### Post by pastalavista on 2010-05-29
I've heard this problem before with 10.04 even though I haven't experienced it. I believe the solution is in the BIOS. According to [this article]("http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html") you should disable the floppy drive in BIOS to fix it.

---

### Post by hihihi100 on 2010-05-29
floppy drive as in floppy disk? 2mb floppy disk?

I use a laptop that has USB and a CD reader, no more

---

### Post by dino99 on 2010-05-29
remove/purge then reinstall pmount & usbmount

---

