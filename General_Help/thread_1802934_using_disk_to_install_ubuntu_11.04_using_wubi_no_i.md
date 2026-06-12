---
title: "using disk to install ubuntu 11.04 using wubi no indication of instllling"
date: 2011-07-12
forum: General Help
---

### Post by Quakemeister on 2011-07-12
Good day all.  Got the Ubuntu 11.04 disk.  Installed it about an hour ago using wubi.  There is no indication of anything installing anywhere.  What gives?  Keep in mind that I know next to nothing about the workings of a computer.  Thank you...Don

---

### Post by vikash_chandola on 2011-07-12
> **Quakemeister said:**
> Good day all.  Got the Ubuntu 11.04 disk.  Installed it about an hour ago using wubi.  There is no indication of anything installing anywhere.  What gives?  Keep in mind that I know next to nothing about the workings of a computer.  Thank you...Don
open control psnel -> add remove program there will option of ubuntu if yes then you have installed no then you have ot installed wubi. you need to reboot/restart your computer to completely install it. In start up screen(when your pc start) choose ubuntu option and just see the whole 20 minute boring installation drama. if you want to see installation files then see C:\ or the directory you choose to install.
that's all.
if you found any error then post that here.

---

### Post by Quakemeister on 2011-07-12
Thank you.  I clicked on view Ubuntu before installing then rebooted.  All that happened was it took me right back to windows.  No where can I find anything that will allow me to try Ubuntu before installing it.  Thank you...Don

---

### Post by Quakemeister on 2011-07-13
Good day.  I'm still unable to install Ubuntu 11.04.  I think the problem may be with “wubi”.  I will get the microsoft install message and when I click on it I can see just for a second the next part that will let me click on what I want to do.  It is really just a flash and then it goes the part that asks if I want to try before installing, or install.  If I tell it to try before installing it will tell me okay then to reboot.  When I do the computer will restart, but it restart into windows.  If I tell it to install I will get an error message telling me “no translation file found for domain”.  The disk I'm using came from the UK made by the developers of Ubuntu 11.04.  Can't go any further.  Don

---

### Post by 3rdalbum on 2011-07-13
"Try Ubuntu" is where you boot your computer from the Ubuntu CD. The computer runs entirely off the CD in this mode so you can try Ubuntu without having to dedicate disk space, etc.

It does take a little more than simply rebooting with the CD in. You have to tell the computer that you want to boot off this CD. You do this through the BIOS setup. When you start your computer you'll see a little message like "Press F12 for boot order" or "Press Esc for SETUP". Press the key that it tells you to and you'll enter the BIOS setup, where you can change the boot order and have your computer start up from the CD.

Each computer has a different BIOS so unfortunately I can't tell you what key to press, or exactly what to expect from your BIOS's setup screen. Don't fiddle with anything there that you don't understand; just use the boot order. When you've made your changes, save and reboot. The computer will boot from CD and you can try Ubuntu. When you're done, just reboot without the CD in the drive and you'll go back to Windows.

You can also install Ubuntu while running it from CD, but you must back up all your Windows data first, and carefully read the instructions placed in front of you.

Unfortunately I can't advise you about your Wubi problem; I'm a permanent Ubuntu user so I use the regular Ubuntu installer, not the Wubi (Windows-based) one.

---

### Post by Rubi1200 on 2011-07-13
As far as installing Ubuntu with Wubi is concerned, the Wubi Guide is the best place to start:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

