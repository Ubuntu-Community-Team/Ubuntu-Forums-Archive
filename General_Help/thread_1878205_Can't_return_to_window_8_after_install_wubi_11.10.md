---
title: "Can't return to window 8 after install wubi 11.10"
date: 2011-11-09
forum: General Help
---

### Post by tranhaithang on 2011-11-09
Hi everybody,
Recently, I have installed wubi ubuntu 11.10 on window 8 developer. In order to increase the speed Ubuntu boots, I have change my default startup OS into Ubuntu with [COLOR=Red]0 second delay[/COLOR] ( I do that in window by following this thread [http://windows.microsoft.com/en-US/windows-vista/Change-the-default-operating-system-for-startup-multiboot](http://windows.microsoft.com/en-US/windows-vista/Change-the-default-operating-system-for-startup-multiboot))
Now I have to turn back to window :-( but I can't, since it jump right to the ubuntu OS.
I have tried ***the start up manager,*** or ***using command*** sudo gedit /etc/default/grub > GRUB_DEFAULT=4
But they didn't work. The start up manager doesn't list my window 8 operating; and the command line does nothing.
Can I ask ubuntu expert please
Thank you in advances

---

### Post by Mark Phelps on 2011-11-09
OK ... so you installed Ubuntu inside an Windows ALPHA version (as in Pre-Beta, as in BUGGY) and you expected it to work?

Startup-manager doesn't work well with recent Ubuntu versions.

Instead, you should try installing Grub Customizer.  The link is below:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

But, this might not work with a Wubi installation -- at which point your best bet would be to erase the drive and reinstall Win8 DP from scratch.

---

### Post by bcbc on 2011-11-09
> **tranhaithang said:**
> Hi everybody,
Recently, I have installed wubi ubuntu 11.10 on window 8 developer. In order to increase the speed Ubuntu boots, I have change my default startup OS into Ubuntu with [COLOR=Red]0 second delay[/COLOR] ( I do that in window by following this thread [http://windows.microsoft.com/en-US/windows-vista/Change-the-default-operating-system-for-startup-multiboot](http://windows.microsoft.com/en-US/windows-vista/Change-the-default-operating-system-for-startup-multiboot))
Now I have to turn back to window :-( but I can't, since it jump right to the ubuntu OS.
I have tried ***the start up manager,*** or ***using command*** sudo gedit /etc/default/grub > GRUB_DEFAULT=4
But they didn't work. The start up manager doesn't list my window 8 operating; and the command line does nothing.
Can I ask ubuntu expert please
Thank you in advances

Try:
1. hitting F8 key at startup - see if windows boot manager pops
2. hitting up arrow key at startup - see if windows boot manager pops
3. boot a windows repair cd and run:
bcdedit /timeout 10

---

