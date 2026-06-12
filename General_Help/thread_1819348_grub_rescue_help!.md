---
title: "grub rescue help!"
date: 2011-08-06
forum: General Help
---

### Post by ffmurray on 2011-08-06
So it seems I deleted grub, and the partition it was on.
Acer aspire 5250-P5WE6
I installed Ubuntu 11.04 alongside windows 7.  In windows I was trying to resize the partitions again to minimize the size of windows.  I deleted my Linux partition instead (I learned my lesson of computers and beer)
When I boot from BIOS to the harddrive I get

Error: no such partition
Grub rescue>

I tried booting from both USB and CD, from two seperate downloads of 11.04, and neither will load.  USB gets as far as displaying the desktop background and the mouse cursor, but it will not move.  CD will only get to the Ubuntu loading screen right before that.
I've tried looking up grub2 commands but whatever I have tried to enter so far comes back with command 'x' not found.
I have no idea what to do next.

Any help or even pointing me in the right direction would be greatly appreciated.

---

### Post by wildmanne39 on 2011-08-06
Hi, with the livecd try nomodeset here is a link for it.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you deleted your ubuntu partition in my opinion it will be easier to reinstall ubuntu.

---

### Post by ffmurray on 2011-08-06
I would love to reinstall Ubuntu but I can't figure out how because nothing I've tried will load, and every grub rescue> command I've tried so far doesn't work.

Im not sure nomodset covers what I need, because it boots to real screens not just a blank screen or colorsplash, it just gets stuck.  But I really don't know what I'm talking about

Is rosewell in the 575 now?  Its all good keeping it in the ex-505

---

### Post by wildmanne39 on 2011-08-06
Hi, I am not sure either but you should try nomodeset options from the livecd.

Yes I am in the 575 area code.

---

### Post by Bucky Ball on 2011-08-06
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

That might help and you can install and run it during a LiveCD desktop sessions to reinstall grub to the MBR also.

---

### Post by ffmurray on 2011-08-06
I guess right now my main problem is that I cannot get the GUI to fully load from either live USB or CD.  I just ran from the live CD while the USB was plugged in, but booting from the CD.  I got farther into loading for the installation than I did with either one independently.  I was able to reach the first install screen where you can pick the language for install but it froze up when I clicked forward.

Would an earlier version of Ubuntu help? Or maybe xubuntu?  Or is there a way to install via command line from a live USB or CD so I can see if its just the GUI?

Or is there a way to bypass grub and boot directly to my windows 7 partition?

---

### Post by ramon.rha on 2011-08-06
Is your computer's HARD DRIVE open or something like that?
 

 A couple of days ago I was installing an OS on a hp dv4 and I was having problems because of sensor that are inside of the HHDD cover, so it could not open any kind of live cd or pendrive, the only think it did was turn on the leds of the compute and no more. so once the HHDD cover closed, I could use the HHDD and finaly a could install all I wanted.
 

 Sorry my bad english :P

---

### Post by ffmurray on 2011-08-06
My hard drive is not open, it's a brand new computer haha.
When I boot without live cd and get grub rescue and ls I get:

grub rescue> ls
(hd0), (hd0msdos1), (hd0msdos2), (hd0msdos3)

So my hard drive is there, and if I boot from live something or other I can only get as far as selecting the language before a freeze.
When I escape from the default boot menu to command line boot: I can tab for commands and go through the help menu but when I enter any command execpt live or live-install, such as expert or click to try and install through a differnt route it just comes back error kernal process not found.
How to I get to a command line interface for the install?

EDIT> i burned a rescatux 0.29 live cd and tried to use its wizart to reinstall grub.  i could not get it to install, but i did get the MBR fixed so that windows at least tries to load, but "a recent software or hardware change" has prevented it from booting.  I called ACER and they are sending me a win7 recovery disk in 8-10 business days, but i could really use my computer before then.

rescatux 0.29 grub install record [http://paste.debian.net/125328/](http://paste.debian.net/125328/)

the

---

### Post by Bucky Ball on 2011-08-07
Try the alternate install instead of the desktop. Alternate text based but that is the only difference. That way if the graphics of the desktop install gui are causing probs you should be able to bypass.

Give it a go, 10.04 LTS might be best. Longer support anyhow. You can always install a different release once you are up and running.

---

### Post by ffmurray on 2011-08-07
After using rescatux 0.29 for fixing the MBR I was able to install 10.04 lts with xfce and with it grub2.  After that it was a simple matter to get win7 running again and get my computer back.
Thanks for the help.

---

