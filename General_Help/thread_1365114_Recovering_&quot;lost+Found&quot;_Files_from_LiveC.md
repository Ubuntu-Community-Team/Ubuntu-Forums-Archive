---
title: "Recovering &quot;lost+Found&quot; Files from LiveCD"
date: 2009-12-26
forum: General Help
---

### Post by Milkman08 on 2009-12-26
Hi All :)
I did a huge mistake in [this]("https://help.ubuntu.com/community/LiveCD/Persistence") process...

After I formatted my USB Stick with GPartEd to Ext3 format, I jumped to creating Casper-RW part and Unmounted my Usb Stick :redface:*

and yeah, after running the next command in terminal My fist boot partition became formated and the only thing remained from my WinXP is a folder named "Lost+Found" which it doesn't seem to be opened...

How can I recover my old OS from it using a live ubuntu 9.04?

[SIZE="1"]*(I got too exited after I read the 1st line of instructions "unmount ... " that I said ooh ooh I know! and I manually unmounted my usb stick, pretty n00bish huh? after all I didn't know I should have unmounted my HDD)[/SIZE]

---

### Post by Milkman08 on 2009-12-27
There's no solution? Come on guy's, I've waited for 10 hours and I got no replies ...

---

### Post by Milkman08 on 2009-12-27
Come on, at least give me a No guys but SAy anything :(

---

### Post by louieb on 2009-12-27
Its a pain to use a Ubuntu live CD. Best to use a CD made for recovery such as [SystemRescueCd]("http://www.sysresccd.org/Main_Page") In particular you want to try two programs - testdisk and photorec. [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by Milkman08 on 2009-12-27
Ok, but how should I recover files from "lost+found" folder? Can you explain that?

---

### Post by louieb on 2009-12-27
lost+found is used by fsck (windows program chkdsk is similar) If you formatted your XP install partition there will not be anything in lost+found to recover. 

The testdisk wiki is your bet source of instructions on how to use the program. At this point there is not much chance of fixing the XP install. About all you can do is try to copy off any documents, photos ...

---

### Post by Milkman08 on 2009-12-27
I ran this command in Terminal exactly
```
sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda1
```
I don't know what it does (formats, ...etc) but instead of formating my USB, it formated my first boot partition.
> At this point there is not much chance of fixing the XP install. About all you can do is try to copy off any documents, photos ...
if you mean I can't recover my old OS at all, then forget it, I'm gonna intall it all over again, but if my doucument ARE recovarable, can anyone exactly tell me how?
I search the web for "lost+found" recover but none of solutions worked.

---

