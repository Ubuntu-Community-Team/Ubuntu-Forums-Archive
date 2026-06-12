---
title: "dual boot killed windows XP :-("
date: 2010-05-15
forum: General Help
---

### Post by netmonky on 2010-05-15
Hi Guys,

I am new to the ubuntu world and seem to have set up everything i want to -- thanks to the older posts i found on this site :-D. 

I wanted to complete a dual boot for winxp (already on PC) and ubuntu lucid. I get the options in grub menu to load windows but it just sits there with a flashing cursor :-( -- possible boot loader issue ??

Can anyone help me out?


Hardware = vm freedom netbook

---

### Post by kekc_leader on 2010-05-15
I usually have to switch back to IDE mode in BIOS before booting Windows XP, then I turn on ACPI again to boot Linux, so that the HD would be faster. May be, you changed the HD mode to ACPI and forgot about it?

---

### Post by netmonky on 2010-05-15
Nope - havent touched the Bios but thanks for your response.

---

### Post by netmonky on 2010-05-15
Can anyone please help ?

---

### Post by jackhe22 on 2010-05-15
I have a suggestion, but in the process it will stop you booting Ubuntu and you will have to re-install Grub, which I am sure someone will help you with.

You Will Need:
Windows XP Disc / Recovery CD / Rescue CD

As you did with Ubuntu, boot from your XP disc. When the Blue Screen appears, it should say Welcome To XP Setup and all of that garbage. Select The Key it says takes you to Recovery Mode.

This should take you to a Dos Looking Prompt. Type fixmbr and press enter. You might have to type fixmbr C: Once it has done this, type fixboot, again, it might be fixboot C: 

---
Once done, press Ctrl-Alt-Del (Control-Alt-Delete) to reboot. Quickly take the disc out, and watch it boot back into XP as normal. Now you just have to figure out how to get Grub Back.

---

### Post by john newbuntu on 2010-05-15
Follow talsemgeest's first post to restore Ubuntu grub bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Raygreen on 2010-05-16
I saw a suggestion that you can fix your boot up to Windows XP by putting your Windows XP disk in your CD drive, boot computer from there. Then Go to C:\ prompt and type fixmbr and then follow that by fixboot. Then reboot your computer normally. This worked for me the only difference is I am running Windows 7 and I had to use a different command of BootRec.exe fixmbr and then BootRec.exe fixboot. But I got back into my Windows, and I ended up deleting Ubuntu out of my Windows programs. It scared the crap out of me that I thought I lost all my Windows stuff. Ubuntu has let me down a number of times. Seems 2 other times I went to upgrade Ubuntu, and it trashed my system. This time I was lucky and everything seems intact on my Windows install.

---

### Post by oldfred on 2010-05-16
If you installed grub to the windows partition - PBR or partition boot sector:

Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

This is similiar to fixboot in the windows repair. If you run fixMBR it will only boot grub and you have to reinstall grub or grub2 to the MBR.

If that has not worked, post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by jackhe22 on 2010-05-16
> **Raygreen said:**
> I saw a suggestion that you can fix your boot up to Windows XP by putting your Windows XP disk in your CD drive, boot computer from there. Then Go to C:\ prompt and type fixmbr and then follow that by fixboot. Then reboot your computer normally. This worked for me the only difference is I am running Windows 7 and I had to use a different command of BootRec.exe fixmbr and then BootRec.exe fixboot. But I got back into my Windows, and I ended up deleting Ubuntu out of my Windows programs. It scared the crap out of me that I thought I lost all my Windows stuff. Ubuntu has let me down a number of times. Seems 2 other times I went to upgrade Ubuntu, and it trashed my system. This time I was lucky and everything seems intact on my Windows install.

I just said that.

---

### Post by tonver on 2010-05-16
> **netmonky said:**
> Hi Guys,

I am new to the ubuntu world and seem to have set up everything i want to -- thanks to the older posts i found on this site :-D. 

I wanted to complete a dual boot for winxp (already on PC) and ubuntu lucid. I get the options in grub menu to load windows but it just sits there with a flashing cursor :-( -- possible boot loader issue ??

Can anyone help me out?


Hardware = vm freedom netbook


I had a good working dual boot system with Ubuntu 9.10 and Windows XP, but after upgrading Ubuntu to version 10.04, Windows XP refuses to start, while it is still in the Grub-list. 
This problem is almost identical to the mentionned one.
What must I do to repair is (I have no W-XP CD!!)

---

### Post by Raygreen on 2010-05-17
Sorry, didn't realize your suggestion was right here in the same thread. Well it worked for me. Except I had to add the "BootRec.exe in front of those commands in Windows 7

---

