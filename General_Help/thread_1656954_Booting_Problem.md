---
title: "Booting Problem"
date: 2010-12-31
forum: General Help
---

### Post by Mega99 on 2010-12-31
Hey guys, I have a problem.
I have Ubuntu Netbook Edition installed on my Hp Mini using Wubi (Windows 7 and Ubunutu are on the same partition). Last week I was playing with the boot-up configuration in Windows, and I set the default booting OS to Ubuntu and the timeout to 0. Now I can't boot into Windows at all.

When it boots Ubuntu, grub pops-up, and if I choose to load Windows, it sends me back to the timeout 0 page, and directly send me to grub once again. Because of this infinite loop, I cannot load Windows at all.

I found how to fix the timeout,but to do that, I have to run a Windows program (bdcedit.exe) through command prompt.

Could anyone please help me out? I need to use a Windows program for homework, and school starts in a few days.

Thanks,
Mega99

---

### Post by bcbc on 2010-12-31
That was a mistake. Windows boots straight to the windows boot manager. You set it to go straight to Ubuntu. The best you could try is maybe hit F8 repeatedly (or hold F8 ) on boot and see if it gives you the option to override. Then change the timeout to > 0. If you want to avoid one of those menus you need to change the grub one. [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)


I'm not sure how to edit the timeout for the boot menu in win 7. Search around on support.microsoft.com. There should be away to either do it from linux or boot to a windows repair prompt from a Windows repair USB/CD and do it from there.

---

### Post by Habeouscorpus on 2010-12-31
If you really get into a jam, you could try an open-source alternative or installing it with Wine. ([http://www.winehq.org/](http://www.winehq.org/)) But before you try, search for it here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

May I ask what program it is?

---

### Post by Mega99 on 2011-01-03
Thanks for all the help,  and sorry for the lateness of this reply (I though i had enabled instant email notification, which i hadn't).

Unfortunatly, you seem to have misunderstood my problem. bcdedit.exe is located in System32 folder. Its a system application, and all the third party applications that can also edit the boot configuration data (BCD) are for Windows, which I can't boot to.

I have searched the web for any kidn of software for ubuntu that will edit the windows bootloader, and I have found none.

Just like you mentioned, I have tried running this program with Wine, with no suceess.
I still see no solutions, but will try a recovery disk via a bootable USB drive.

---

