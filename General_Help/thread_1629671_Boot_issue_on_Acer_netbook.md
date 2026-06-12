---
title: "Boot issue on Acer netbook"
date: 2010-11-24
forum: General Help
---

### Post by adnafunnyfarm on 2010-11-24
I'm having nearly the *exact* issue described [here]("http://ubuntuforums.org/archive/index.php/t-1244466.html"). I've changed the boot order on the netbook so that USB FDD is first in line. I then mounted the live CD ISO to a USB flash drive... no dice.

After the *mount: mounting /dev on /root/dev failed: No such file or directory* message, it indicates that it has scanned the USB drive but I still get no boot.

---

### Post by wilee-nilee on 2010-11-24
How did you load the usb drive? Is it a regular thumb drive?

---

### Post by sikander3786 on 2010-11-24
USB FDD is not the USB Drive. Go to the Hard disk boot menu under Bios and see if your USB drive is listed there. If it is, bring to the top of that list.

---

### Post by adnafunnyfarm on 2010-11-24
Yeah, just a regular old thumb drive. I'll double check the boot order in the BIOS.

---

### Post by wilee-nilee on 2010-11-24
> **adnafunnyfarm said:**
> Yeah, just a regular old thumb drive. I'll double check the boot order in the BIOS.

Please read posts carefully I asked this question. Personally we are helping you so make sure you  make it as easy as possible.;)
"How did you load the usb drive?"

This is a post and run situation good luck.

---

### Post by sikander3786 on 2010-11-25
And if someone else jumps in the thread like me did in this thread, it doesn't mean that the information/questions asked by the previous poster/posters were irrelevant. It only means that they missed something and you need to answer all of those queries ;-)

Hope you got it :P

---

### Post by madjr on 2010-11-25
> **adnafunnyfarm said:**
> I'm having nearly the *exact* issue described [here]("http://ubuntuforums.org/archive/index.php/t-1244466.html"). I've changed the boot order on the netbook so that USB FDD is first in line. I then mounted the live CD ISO to a USB flash drive... no dice.

After the *mount: mounting /dev on /root/dev failed: No such file or directory* message, it indicates that it has scanned the USB drive but I still get no boot.

how did you mount the live-cd into the usb?

did you use the unetbootin program? if not than go ahead and try it with that

---

### Post by adnafunnyfarm on 2010-11-27
I apologize for the confusion, Wilee-Nilee. In my use of the linear rather than threaded view I hadn't considered how using a single "quick reply" to address posts by different users would cause confusion.

Sikander, you are correct. I've now got the install screen up.

Related follow-up question: If I install Ubuntu Netbook outright (by which I mean no dual-boot) will I lose access to the files/documents from the previous install?

---

### Post by sikander3786 on 2010-11-27
> If I install Ubuntu Netbook outright (by which I mean no dual-boot) will I lose access to the files/documents from the previous install?

Where are those files/documents? I mean on which partition? And which version of Ubuntu is installed?

---

### Post by adnafunnyfarm on 2010-11-27
The hard drive was not previously partitioned, just running Ubuntu 10.04 because I was happy to say goodbye to XP.

In any case, I've spoken too soon. I was able to boot the "live" CD from the flash drive only once.

It will now not boot, simply gives me this message:

> BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by adnafunnyfarm on 2010-11-29
No ideas?

---

### Post by sikander3786 on 2010-11-30
> **adnafunnyfarm said:**
> No ideas?
I would recommend to try some other USB drive (if available) and use unetbootin this time.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

And prior to that, make sure your downloaded image is not corrupt.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

