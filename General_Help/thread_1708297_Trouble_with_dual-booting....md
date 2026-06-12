---
title: "Trouble with dual-booting..."
date: 2011-03-16
forum: General Help
---

### Post by akakingess on 2011-03-16
Okay, first of all I am fairly literate when it comes to computers and Linux and Windows in particular, however, when I took my Ubuntu laptop (10.10 desktop version) and decided to use the extra HD space to put on Windows for my wife's benefit and so that I could do some Flash development, the trouble began. Yes, I have read the Grub 2 documentation and followed to the letter, so when I installed Windows 7 on sda1, I lost Grub and hence the ability to access my Ubuntu. Sounds like a simple fix, boot off of a liveCD, reinstall Grub onto sda5 (my 10.10 /boot partition) and then boot off of a Windows 7 CD and using the CLI restore the MBR. Well, none of that has resulted in the desired outcome. I can still access one at a time by doing the respective steps (i.e. booting off of a Ubuntu LiveCD and installing grub will give me grub but with only the Linux versions from which to choose. Vice-versa, if I boot off of the Windows CD and repair the MBR I can boot directly into Windows 7, but at no time do I have a choice during boot to choose which one I want to go into. Any and all suggestions are welcome and appreciated, I will be available via IM'ing which all of my contact info is available within my profile here on the forums. Thanks in advance for any and all suggestions as I am just frustrated at this point.

Earl

---

### Post by Vi3tHoneyX on 2011-03-16
Maybe [this will help?]("http://www.supergrubdisk.org/")

I've heard good things about it but I've never personally had to use it...yet

---

### Post by wilee-nilee on 2011-03-16
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us the correct tools to start with, your description of the fix is convoluted.:) Also tell us the computer manufacturer.

---

### Post by akakingess on 2011-03-16
Thanks to the both of ya for the quick responses, I am going to try the 'Rescatux' LiveCD first and see if that does the trick, if not, I will boot into Ubuntu and run the bootscript provided by wilee-nilee, and we'll see where we stand at that point. I am really hoping that the rescatux works, cuz this reconfiguring every time that I need to switch OSs is getting quite annoying. That's the main reason I am waiting to do the bootscript as i am currently in Windows right now. I will keep ya'll informed of what is going on and thanks again for the prompt assistance.

---

