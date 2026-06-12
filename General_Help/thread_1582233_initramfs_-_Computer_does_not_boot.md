---
title: "initramfs - Computer does not boot"
date: 2010-09-26
forum: General Help
---

### Post by Drigeolf on 2010-09-26
I am aware that there is a similar thread, but it was about Wubi, not fully installed Ubuntu.
 
I am using Lynx (10.04) on a single partitioned hard drive. I installed it this June and used it whithout any problems.
 
Today I simply checked my e-mail (using Chrome), I haven't downloaded anything, visited a weird website...etc. When I tried to open the chat package(the one that comes with installation, sorry I forgot its name) a blank window opened with the same size of the program, without anything else. I tried to open System Monitor, same thing happened. Tried to restart, but when I choose restart from the menu there was also a blank window. Then I tried to open a terminal, to manually restart, but again, a blank window.
 
I pressed ctrl+alt+delete, do not know why, but it worked and I finally choose the restart option there.
 
When it restarted I was looking at:
 
(initramfs) _ 
 
Before that, there is an error message, which says:
 
```
  
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init = boorarg
 
BusyBox v1.13.3 ...etc

```
 
At the very top of the page there is the line:
 
BUG: unable to handle kernel paging request at 013bf000
followed by some illegible stuff, some hex...etc.
 
Tried the exit command, but it didn't work.
 
I am using Ubuntu for years now and just recently completely switched to it. My problem is since I took backups of my system before the switch(June) I didn't bother doing it ever since. There are some very important files there without any backup, so please help me.
 
Also, I am computer literate, but I do not have a Ph.D. in computer science, so please keep it relatively simple.
 
p.s. Sorry for the English, I am not a native speaker.

---

### Post by Drigeolf on 2010-09-26
By the way, my computer is ASUS F3JC Laptop with Intel Core2 Duo Processors.

---

### Post by 0N3 on 2010-09-26
If the files are very important use another live cd to boot up the machine and retrieve the files Knoppix is quite good but any distro will do the same and maybe try a fresh install sorry its a little over my head

---

### Post by Drigeolf on 2010-09-26
Thanks for the reply, but I prefer to solve this without a reinstall.
 
I tried to force mount the hdd using:
 
```
mount -t ext3 /dev/sda1 /root -o force
```
 
It returned:
 
```
 
mount: mounting /dev/sda1 on /root failed: Device or resource busy

```

---

### Post by 0N3 on 2010-09-26
you should partition you HDD one partition /(root) for all your program ect and a home partition /home all your personal files that way you will never lose anything you don't have to format the home partition after a fresh install all your files, music, pictures, program settings, themes, bookmarks ect.... are never lost.

---

### Post by Drigeolf on 2010-09-26
bump

---

### Post by Drigeolf on 2010-09-26
Suggestions, anyone?

---

### Post by drs305 on 2010-09-26
Do you see the Grub menu during boot? Do you have other kernel or recovery mode options on the menu?

If you don't see the Grub2 menu, hold down the SHIFT key during boot.

If you don't have a recovery mode option, you can highlight your normal entry (the one that doesn't work), press "e" to edit and change the end of the *linux* line from "quiet splash" (if there) to "single". Then press CTRL-x to attempt to boot to the recovery mode.

---

### Post by Drigeolf on 2010-09-26
Thanks a lot for the reply.I do not normally have GRUB at boot but I tried holding down shift. It says:
 
GRUB loading.
 
Then nothing happens and I return back to the initramfs screen.
 
 
EDIT: No, apparently I should hold down the shift key until GRUB is loaded. I tried the recovery thing, didn't work, now I am going to try the other suggestion. Thanks again.

---

### Post by Drigeolf on 2010-09-26
Problem solved! I simply choose one of the other kernel options from the list, It automatically done a hdd test and repaired the problem.
 
Thank you all for your support.

---

### Post by subjucha on 2010-10-01
I had same problem and this helped me too!
Thank you a lot!

---

### Post by subjucha on 2010-10-07
Knows anybody where it can be submitted this problem in the ubuntu community? I think it would be useful if developers will create any kind of help in this situation.

---

### Post by drs305 on 2010-10-07
> **subjucha said:**
> Knows anybody where it can be submitted this problem in the ubuntu community? I think it would be useful if developers will create any kind of help in this situation.

Here is community documentation on one way to report bugs in the packages used in Ubuntu:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by ebramwells on 2010-10-20
I have this problem but the above solution didn’t work! I tried the various options under GRUB (the older kernels as well as their recovery modes), but this didn’t do anything.

---

### Post by drs305 on 2010-10-20
> **ebramwells said:**
> I have this problem but the above solution didn&#8217;t work! I tried the various options under GRUB (the older kernels as well as their recovery modes), but this didn&#8217;t do anything.

ebramwells,

Welcome to the Ubuntu forums. If you are stuck at the "grub>" or "grub rescue>" prompt, take a look at this thread for ways to boot into your system. 
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")


What is happening is most likely that Grub is passing control over to the kernel but at some point the system can't find the necessary files to continue the boot and gives up. The instructions in the thread help steer the boot process in the right direction.

If you still can't boot, run the boot info script as outlined in that thread and post the results there.

---

### Post by ebramwells on 2010-10-20
Thanks a lot, that fixed it!

---

