---
title: "Demo and Full Installation Problem!!!"
date: 2009-09-13
forum: General Help
---

### Post by Svedka on 2009-09-13
Hi, I'm a rookie when it comes to Ubuntu. I downloaded 9.04 this past week and have to say I really like it.
Basically I ran the ***Demo and Full Installation*** option straight from the ISO (I'm using magicdisc). Since it wouldn't reboot I chose the ***Help me boot from CD*** option. It proceeded to install a temporary file and then I was able to run Ubuntu.

My current OS is Windows XP Pro (which I need to run my audio and video applications). After that trial run I opted to run Ubuntu from Virtualbox instead of making a partition on my hard drive for it.

I unmounted the ISO, uninstalled wubi from C:\ubuntu, yet everytime I restart my computer I get the option to boot either from XP or Ubuntu.
Whenever I choose to run Ubuntu it never loads up and gets stuck here:

[B]Loading Please wait...

Busybox v1.10.2 (Ubuntu 1:1.10.2-2Ubuntu7) built-in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)[/B]   

My initial reaction was to run the LiveCD again and follow the same steps I took the first time. ***Help me boot from CD*** and let it do it's magic. To my demise it always gets stuck in the same place and Ubuntu never loads.

All I'm trying to do is completely delete the option to boot from Ubuntu, since like I said, I will now be running it on Virtualbox.

Any help would be greatly appreciated. Thanks!


p.s. Yesterday I posted a similar thread on Installation and upgrades that didn't get much attention. After seeing that this part of the forum gets more views and replies I decided to try my luck here. Hope I don't piss off anyone :)

---

### Post by Ms_Angel_D on 2009-09-13
You need to fix your Master Boot Record or MBR for windows

Have a Look Here
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by Svedka on 2009-09-13
Already tried that but it doesn't make a difference.

---

### Post by Ms_Angel_D on 2009-09-13
Well the only other idea I personally have would be to re-install windows. If you used the wubi(demo) option, then repairing your MBR would be the only way I know to remove it. Because the only thing wubi does is add this option to your MBR so that you can boot to the virtual drive it creates.

---

### Post by Svedka on 2009-09-13
yeah, i've been trying so many methods to no avail. i already backed up my files thinking worst comes to worst i'll just reinstall XP. i think i might have to.

thanks a lot for your help tho!

---

### Post by synapsys on 2009-09-13
When you install a fresh copy of your mbr (fixboot, fixmbr) you should only see windows. I have never heard of this not working. 

If for whatever reason this doesn't work, you will have to manually edit a file called 'boot.ini' If you delete the entry for ubuntu in boot.ini you will not see it at boot time.

Here's a link:
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by Svedka on 2009-09-13
Fixed it by deleting the Ubuntu/Wubi line in boot.ini!!! :D

---

### Post by synapsys on 2009-09-13
Out of sight, out of mind :)

---

