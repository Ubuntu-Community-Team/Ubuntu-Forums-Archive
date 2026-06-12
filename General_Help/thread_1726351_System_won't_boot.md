---
title: "System won't boot"
date: 2011-04-11
forum: General Help
---

### Post by st4tique on 2011-04-11
I'm running Ubuntu 10.10. 
Last time the system was up and running I /might/ have been installing updates, but can't recall what exactly (I install them as they come, and sometimes don't even check what they are).

Came back after several hours to a black screen with a visible movable cursor on top.
Hard reboot landed me in a screen that says something like this:

[INDENT][I]mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have requested /sbin/init

No init found. Try passing init= bootarg

BusyBox v1.15.3 <... some other stuff I didn't write down ....> Built-in shell (ash)

<... something about entering help for available commands ...>

(initramfs)
[/I][/INDENT]The last line being a prompt awaiting commands.

At this point I started googling it but couldn't find my particular case, and didn't want to mess things up further. Most users with this issue say they installed Ubuntu inside Windows, and the rest say they don't have windows at all.

I do have dual boot with Windows, but I have them on separate partitions, and Windows is not aware of the Ubuntu partition and can't access it. I tried downloading a Windows tool to access the partition and take a look, but currently it's not working.

Any help will be much appreciated. Please use n00b level terminology =)

---

### Post by akakingess on 2011-04-11
Just as a quick try, have you tried typing "startx" without the quotes at the prompt awaiting commands?

---

### Post by st4tique on 2011-04-11
Nope, doesn't work. It's not one of the available commands. It prints out a list of commands I can use if I type in "help": I recognize few of them, and none look useful.

---

### Post by st4tique on 2011-04-11
Update:

I booted with a live CD (a usb stick, actually), opened a terminal, and here's how far I got:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2096768

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10121    81189965    7  HPFS/NTFS
/dev/sda3           10121       19458    74995713    5  Extended
/dev/sda5           10121       19072    71895040   83  Linux
/dev/sda6           19072       19458     3099648   82  Linux swap / Solaris

Disk /dev/sdb: 8000 MB, 8000110592 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         973     7811072    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(971, 254, 63) logical=(972, 143, 3)

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?


```I tried umounting it, says it's not mounted. Tried checking the partition with gparted - same error (resource busy).

Tried to mount it via the gui - got: "DBus error org.gtk.Private.RemoteVolumeMonitor.Failed"
Tried to mount it via terminal - just hung there. Closed terminal, now any attempts to mount it from gui result in: "A job is pending on /dev/sda5".

Got no idea how to remove this pending job, so will try to restart and follow more random instructions from random threads around the internet.


***


Edit:

Every time I touch the linux partition in some way, it either errors or hangs. If it hangs, I don't even get proper errors from anything anymore, since it says a job is pending for /dev/sda5 and it doesn't even bother trying whatever it is I wanted.

I ran disk utility from the live cd, and apparently my HD has 23 bad sectors (I guessed it's not in the best condition, but I don't know if this means it's completely fried or still functional, and since my Windows is still running on the same HD...)

I'm currently running self-tests on the HD (not sure what they are, but looked like a good option), but it's taking forever.

Will appreciate any help at all. A fresh install is an option, but I'd love to get a chance to backup my data before that...

---

### Post by st4tique on 2011-04-12
PARTIAL FIX:

I got some serious progress so far, so I'm posting this for anyone who might have the same problem.

After failing to fsck the linux partition with ubuntu live cd, I downloaded slax and booted from it.
It allowed me to fsck the partition to a certain point, and then abruptly exited with signal 6 (if I'm not mistaken).
The partition was still inaccessible from slax.
I booted from ubuntu live cd again, and voila - partition accessible, data backed up and saved. 
Had some issues with copying some of the files, but they were solved with: "chmod 777 <filename>" and I could copy all I needed to my windows partition.
Next I tried to fsck the partition again, still being in ubuntu live cd. No "resource busy" this time, and unlike slax it managed to go all the way.

I tried to boot from the ubuntu installation on my hard drive, with some success:

I'm reaching ubuntu, it's there alright. I can log in and issue commands.

HOWEVER:

- GUI is gone. All I see is a shell. I managed to log in alright, and things look fine, but I want my gui. So I tried to run startx as suggested above (don't know what it does, but sounded appropriate), only to discover:

- I'm not a sudoer anymore! So basically I can't do anything properly to restore my system, for lack of privileges. Lovely.

Well, at least I have my data and something new to google. 
As always, any help will be much appreciated.
I'm also considering marking this as solved and opening a new thread, since this appears like a whole new problem.

***

Edit:

I decided that the recovery of my data is good enough and proceeded with a fresh install. 
All appears to be working currently.

---

### Post by akakingess on 2011-04-12
Glad to see that you at least recovered your data, as that is usually 99% of the concern in these situations, thanks for marking it solved for people that may have a similar problem in the future and you were right to open a new thread since this is technically speaking a new problem, however, in the new thread you may want to include a link to this thread so that viewers have the option to get the background information that got you to this point.  Good Luck!!

---

