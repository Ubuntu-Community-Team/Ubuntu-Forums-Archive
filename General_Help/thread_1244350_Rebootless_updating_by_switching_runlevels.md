---
title: "Rebootless updating by switching runlevels?"
date: 2009-08-19
forum: General Help
---

### Post by dhughes on 2009-08-19
I thought I had this figured out but I guess not. 

 Let's say Update Manager has installed updates and I get *"In order to complete the update of your system it needs to be restarted."* which is fine but I want to restart without rebooting.

 I log out of GNOME and my account, at the GDM login screen I select on the keyboard keys ctrl+alt+F1 to go to a command prompt, log in as root (I previously set up a root password) and then check using the **runlevel** command, I think it was showing "N 3". 

 Then I type the command **init 1** and after a moment a menu with a list of options appears (fsck, repair etc.) one of which is to go to a command prompt (without networking), so I choose that.

 I check which processes are running using the **top** command, quite a few are there but from what I understand the are children of /sbin/init anyway so it's not unusual to see them. I exit top.

 Still at the command line I type **runlevel** again and see "1 S" and I assume at 'runlevel 1' it's as low as I can go before runlevel 0 which is a system **halt**.

 When I type **init 3** I see what appears like the boot up screen with processes starting, networking initializing etc. but when I get back to the GDM, log in and after a minute I get the 'Restart Required' again, am I missing a step?

---

### Post by mcduck on 2009-08-19
> **dhughes said:**
> I thought I had this figured out but I guess not. 

 Let's say Update Manager has installed updates and I get *"In order to complete the update of your system it needs to be restarted."* which is fine but I want to restart without rebooting.

 I log out of GNOME and my account, at the GDM login screen I select on the keyboard keys ctrl+alt+F1 to go to a command prompt, log in as root (I previously set up a root password) and then check using the **runlevel** command, I think it was showing "N 3". 

 Then I type the command **init 1** and after a moment a menu with a list of options appears (fsck, repair etc.) one of which is to go to a command prompt (without networking), so I choose that.

 I check which processes are running using the **top** command, quite a few are there but from what I understand the are children of /sbin/init anyway so it's not unusual to see them. I exit top.

 Still at the command line I type **runlevel** again and see "1 S" and I assume at 'runlevel 1' it's as low as I can go before runlevel 0 which is a system **halt**.

 When I type **init 3** I see what appears like the boot up screen with processes starting, networking initializing etc. but when I get back to the GDM, log in and after a minute I get the 'Restart Required' again, am I missing a step?
Yes, the step where you actually load the new kernel version (which is the most common reason why an update would require you to restart the system). :)

You reload pretty much everything else, but not the kernel itself.

---

### Post by Cheesemill on 2009-08-19
The only time you will get prompted for a restart is if you install a new kernel.
You can only switch to a different kernel by rebooting.

---

### Post by mcduck on 2009-08-19
It's not actually impossible to load new kernel without a reboot, although it tends to be at least a bit buggy and, in most cases, not really useful.

However if you are running a production server or some other large system that takes *long* time to boot Ksplice provides a tool handling kernel updates without rebooting:
[http://www.ksplice.com/]("http://www.ksplice.com/")
[http://www.ubuntugeek.com/install-ubuntu-kernel-updates-without-rebooting-using-ksplice-uptrack.html]("http://www.ubuntugeek.com/install-ubuntu-kernel-updates-without-rebooting-using-ksplice-uptrack.html")

---

### Post by dhughes on 2009-08-19
Ah I see, the kernel, thanks.

 Actually, I do have ksplice, I installed it pretty much the day it came out, but I never really used it yet, or figured out what has to be done to use it. I wasn't aware about its ability to "reboot" when the kernel is updated but I guess that's the point behind it seeing how awkward it is!

---

