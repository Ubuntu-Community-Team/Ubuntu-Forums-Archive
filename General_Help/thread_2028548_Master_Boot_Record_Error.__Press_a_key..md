---
title: "Master Boot Record Error.  Press a key."
date: 2012-07-18
forum: General Help
---

### Post by george.henne on 2012-07-18
Recently, I've been getting an error message when booting.  It would say....

[INDENT]Master Boot Record Error.

Press a key.[/INDENT]

So, I would press a key and.... the computer boots.  No further problems.  Until the next reboot when it would do it again. :(

I've done some searching on fixing master boot records and they all center around one that is totally trashed and needs to be redone from scratched.  I am hesitant to do this for fear that I'll make things worse before they get better.

I'm wondering what information, while I have access to the system, I should collect before trashing my existing MBR for a clean one.  I've had to restore MBRs before, but I'm hazy on the details.  I'm thinking I'll need to reinstall grub2 and I think that it should recognise my various boot partitions (dual booting Windows because I like Star Craft & Diablo on occasion).

I've collected partition info from sfdisk (7 partitions), just in case.  I've also made an untimly backup of the faulty 512 byte MBR because, if nothing else, the current is better than nothing.

Anyway, does anyone have any advice before I boot into a live CD and try to lay down a new MBR? :D

---

### Post by oldfred on 2012-07-18
Is this a BIOS error?

A few BIOS (mostly Intel) require a boot flag on a primary partition. Windows requires a boot flag on a primary partition to boot or make repairs to boot, but grub does not use a boot flag even to dual boot Windows. 

You can post the link to the BootInfo, if you want to see if there is some issue. Will also repair many grub2 issues.
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Manual ways from liveCD.
that we can see.How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
(was this thread) [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by george.henne on 2012-07-19
It appears to be a BIOS error.  It displays just after the regular BIOS messages, in the same generic BIOS font, before grub takes over the screen.  I installed boot-repair and performed the 'recommended repair' function of boot-repair.  Unfortunatly, it didn't fix the issue.

I did a BootInfo summary both before and after the repair, so at least I have a lot of information, so if I do try to just recreate the MBR I can get another BootInfo summary and try to restore what is lost. :)

Before: ....://paste.ubuntu.com/....
(edited out the links)
After: ....://paste.ubuntu.com/....

It made some unfortunate changes.  It removed the mount points for the windows partition (not that I used them), and it added a 10 second time out to grub (easy to fix).  I have to go over the diff of the two to see what else changed.  Unfortunatly, the one thing that didn't change is the error on boot. :(

---

### Post by oldfred on 2012-07-19
Unless it is something with sdb, your sda looks ok. The issue with BIOS has been primarily with Intel motherboards that want a boot flag on a primary partition which you have on sda1, so that is not an issue.

You may want to houseclean out some old kernels.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

Check current kernel I also keep one older just in case:
uname -a
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI (or CLI)
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by YannBuntu on 2012-07-20
Hello

If you disconnect your 120GB disk, then reboot several times, does the "Master Boot Record Error" error still appear or not ?

**If the error does not appear any more,** that means that your BIOS tries to boot on this disk (when connected), but fails because there is no GRUB in its MBR. In this case, i would install GRUB in its MBR (eg via the "Place GRUB into: sdb" option of Boot-Repair). I'm not sure it will work, so backup all the data on this disk to another disk first.

---

### Post by plucky on 2012-07-20
Just a thought,

Have you tried removing from the boot list any other device other than the Hard Drive.

Is is looking at a non-existent drive to boot from?

Do you have a floppy or CD in any of those drives?

Good Luck

---

### Post by george.henne on 2012-07-20
It was trying to boot from sdb.

I'm not sure how it got changed, but for some reason, the drive identifided as sdb was the first boot choice in the BIOS.  I've now switched the boot order for the drives to get the proper drive first.  That fixed it. :D

I had forgotten that drive was in there.  It was the main drive of the computer that this machine replaced.

So, thank you to everyone.  I'm pretty sure that I would have been pulling my hair out after redoing the MBR of sda only to find that the computer was still having issues.

Anyway, now I just have to undo some of the damage that boot-repair did.  Luckily, it is minor and well documented damage.  I'm still grateful for the software because it generated the data that got me the help I needed, so thanks to the people behind boot-repair too.

Thank you! :D

---

### Post by YannBuntu on 2012-07-21
Happy it works :)

- "it removed the mount points for the windows partition": please fill a bug report [here]("https://bugs.launchpad.net/boot-repair/+filebug"). In this report, indicate the before&after URLs (you have deleted them in your previous post). If you forgot them, please indicate the exact content of your /etc/fstab file.
- "it added a 10 second time out to grub": this is the default setting of Boot-Repair, it can be changed via the Advanced options.

---

