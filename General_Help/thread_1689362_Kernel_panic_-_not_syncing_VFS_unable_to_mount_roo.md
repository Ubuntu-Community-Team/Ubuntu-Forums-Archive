---
title: "Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)"
date: 2011-02-16
forum: General Help
---

### Post by Erdr1ck on 2011-02-16
Serious problem trying to boot into my Ubuntu partition this morning - when I select either Ubuntu or recovery mode from GRUB, I get the above error message.  I've been using my current dual-boot Windows XP/Ubuntu 10.10 set-up stably for ~2 months now with zero problems, up until today.  

Yesterday I installed the most recent security updates, and logged off as normal with no trouble to use some Windows proprietary software.  Windows partition worked, and still works fine, but whenever I attempt to boot into Ubuntu now the machine hangs on this 'kernel panic'.

The error message seems almost identical to that posted here:
[https://lists.ubuntu.com/archives/kernel-bugs/2010-September/143887.html](https://lists.ubuntu.com/archives/kernel-bugs/2010-September/143887.html)

Any advice would be greatly appreciate - I'm running the only Linux here in a business setting, so I don't have any Linux trained tech-support to draw upon.

Brett Bowman
Senior Research Associate
Cibus US LLC

---

### Post by drs305 on 2011-02-16
Please go to the following site, download the boot info script and run it according to the instructions. Post the contents of the RESULTS.txt, which will give us a good picture of your system's boot setup and allow us to provide suggestions based on what we find.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Erdr1ck on 2011-02-16
Done - the RESULTS.txt file from the boot info script is attached.

---

### Post by drs305 on 2011-02-16
Boot the LiveCD, open a terminal, and verify your Ubuntu partition is "sdb". You can use "sudo fdisk -l" (lowercase L) to check. Then run these commands and reboot.

The commands assume Ubuntu is still reported on sdb1:

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Don't include the partition number in the second command.

Reboot and make sure the sdb drive is the first to be chosen by BIOS.  If you don't see Windows in the menu, run the following once you get Ubuntu booting normally:
```
sudo update-grub
```

---

### Post by Erdr1ck on 2011-02-17
Thank you for the step-by-step,

The system correctly identifies "sdb" as my Ubuntu partition, and the mount command works with no issues.  However, when I attempt to run the grub-install command, I get the following error message:

> 
/usr/sbin/grub-setup: warn: Sector 32 is already in use by Flexnet; avoiding it.
 

Then, when I attempt to boot into my Ubuntu partion as normal, I still get the same kernel panic message.

---

### Post by drs305 on 2011-02-17
Were you trying to install on sdb and not sda? sda may have the 'FlexNet' problem but I'm a bit surprised the sdb drive does, since you only have Ubuntu on it.

You are being 'victimized' by Adobe's FlexNet software. It writes to a part of the disk normally reserved for other information, such as boot instructions. This information includes registration data and may cause problems with Adobe software and some others if it is removed. 

Originally Grub2 wasn't able to handle this situation and the FlexNet software had to be removed. 

Later Grub2 versions were supposed to deal with this situation and just avoid the offending section while still being able to install. If you aren't using the latest release of Grub 2 (1.98), try to upgrade to it. If you are using it, you can follow the advice on the following page. 

Definitely make a backup of the MBR following the post's instructions. You might want to try to zero out only sector 32 first (after making a backup) to see if it works. If you have problems with Window apps registrations you could restore the sector or entire MBR with any backup you made.
[_http://ubuntuforums.org/showthread.php?t=1661254_]("http://ubuntuforums.org/showthread.php?t=1661254")
Since you are working with sdb, which currently has no Windows partitions on it, the above solution should not jeopardize any software registrations on sda (Windows) and I would give it a try.

Another option would be to try to write to the sda mbr *while still mounting your sdb1 Ubuntu partition*:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**
```
I'd try the other method first.

---

### Post by Erdr1ck on 2011-02-17
I was able to successfully mount the "sdb"/Ubuntu partition once I followed the instructions that you linked to for zeroing Sector 32.  I believe that the FlexNet installation was left over from the Linux hard-drive's previous existence as a spare disk in a Windows RAID array.  Though how it survived formatting to Ext4 is curious...

Unfortunately, remounting that partition did not solve my initial error - I still get the same kernel panic message when I try to boot into it.  

I have yet to try over-writing the MBR of the "sda"/Windows partition, because I have at least two expensive licenses installed on that system that I would like to avoid messing with if possible, though I don't know if they are written to the MBR or not.

If you have any other suggestions for possible causes of, or solutions to my kernal panic issue, I would be grateful to hear of them.  Otherwise, I will back up my "sda" MBR and try to install grub there as per your previous post.

---

### Post by drs305 on 2011-02-17
The mention of the RAID setup leads to another possibility. There are cases where Grub2 fails on drives which formerly contained a RAID setup.

Here is a thread that briefly discusses the issue.
[http://ubuntuforums.org/showthread.php?t=1325650]("http://ubuntuforums.org/showthread.php?t=1325650")

*presence1960* provided the following command:
```
	sudo dmraid -E -r /dev/sdb
```

Posting a new RESULTS.txt might indicate if anything is changed.

---

### Post by Erdr1ck on 2011-02-17
I looked at my partitions both with Gparted and with blkid, as discussed in that thread and see no signs of that the previous RAID configuration is affecting any of my drives.  The only partitions I see are the ones that I expect - sda1 (Windows XP), sdb1 (Ubuntu 10.10), and sdb5 (Swap).

The dmraid command gives the following output:
> 
ubuntu@ubuntu:~/Downloads$ sudo dmraid -E -r /dev/sda1
no raid disks and with names: "/dev/sda1"
ubuntu@ubuntu:~/Downloads$ sudo dmraid -E -r /dev/sdb1
no raid disks and with names: "/dev/sdb1"
ubuntu@ubuntu:~/Downloads$ sudo dmraid -E -r /dev/sdb5
no raid disks and with names: "/dev/sdb5"

ubuntu@ubuntu:~/Downloads$ sudo dmraid -E -r /dev/sda
no raid disks and with names: "/dev/sda"
ubuntu@ubuntu:~/Downloads$ sudo dmraid -E -r /dev/sdb
no raid disks and with names: "/dev/sdb"


I have attached my new boot_info_script results as per your request, though I can see no significant changes.

---

### Post by Erdr1ck on 2011-02-20
Any other suggestions?  I may have to wipe and reinstall, unless I can find a solution to this problem.

-Brett

---

