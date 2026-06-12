---
title: "Boot menu with Ubuntu 10.10, Windows 7 and Windows XP Pro"
date: 2011-01-06
forum: General Help
---

### Post by acompay on 2011-01-06
[COLOR=black][FONT=Verdana]I have Windows XP Pro running in a hard drive, and I installed Windows 7 in a second hard drive thinking in having at the end a dual boot menu. Nevertheless, only Windows 7 appears in the boot menu and I can't have access to my Windows XP Pro installation. Now, I start installing Ubuntu 10.10 thinking that it will recognize these two operating systems. But Ubuntu 10.10 recognizes only Windows XP which is installed in a second hard drive. So the situation is that I want to keep Windows XP Pro in a hard drive and Windows 7 and Ubuntu 10.10 in a second hard drive that has already Windows 7 in one partition and there is another partition with enough space for Ubuntu 10.10. If I install Ubuntu and I get at the end a dual boot menu with Ubuntu and Windows XP Pro can I edit the GRUB2 to add Windows 7? Your help will be very much appreciated![/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Regards,[/FONT][/COLOR]

---

### Post by wilee-nilee on 2011-01-06
I think it will be helpful for us to see what is where so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

You might try sudo update-grub first though in Ubuntu and see if that load W7 into the menu.

---

### Post by acompay on 2011-01-06
> **wilee-nilee said:**
> I think it will be helpful for us to see what is where so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.
 
You might try sudo update-grub first though in Ubuntu and see if that load W7 into the menu.
 
Hello,
Thank you for your reply. I started following your advice.
Regards,

---

### Post by perspectoff on 2011-01-06
See subsequent posts for flames, but I still use Grub Legacy in a boot partition to chainload every other OS' peculiar bootloader (whether that of WinXP, WinVista, Win7, or Grub2 of Ubuntu). 

Some of my computers now have 15 OS on them, and never a conflict. It takes some effort the first time, but not much after that, and OS updates are painless and foolproof, no matter how many OS you have.

Check out my suggestions:

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

Kubuntuguide.org
[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

---

