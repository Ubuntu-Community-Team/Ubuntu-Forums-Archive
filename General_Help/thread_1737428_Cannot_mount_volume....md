---
title: "Cannot mount volume..."
date: 2011-04-23
forum: General Help
---

### Post by meanmrmustard on 2011-04-23
I believe I've included all the relevant info here.

Suddenly this morning I find I am unable to access partitions in 2 of the 5 Sata disks in this machine. One of the five is dying and not mountable, and one is new and not yet partitioned. I will try to save that data to the new one once this problem is resolved.

 I can boot the system with no problem (/dev/sdf) but when I tried opening other 2disks and their partitions under 'removable media' I get "mount: /dev/sd(x)already mounted or media/disk busy" on 4 of the partitions.
On 3 others the message is "DBus error org.gtk.PrivateVolumeMonitor.Failed: An operation is already pending"


My searching has found that /dev/mapper was the problem for one who had the "already mounted" message: 

[http://www.linuxquestions.org/questions/red-hat-31/dev-sda1-already-mounted-or-mnt-busy-sata-sil-3112-a-494987/](http://www.linuxquestions.org/questions/red-hat-31/dev-sda1-already-mounted-or-mnt-busy-sata-sil-3112-a-494987/)

and was solved by commenting out "all lines with dm-mod/dm-mirror" in /lib/modules/`uname -r`/modules.dep. 

On my system however, all lines in that file with dm-* are dm-raid, dm-messages, and dm-mem
eg. kernel/ubuntu/dm-raid4-5/dm-messages.ko or /kernel/ubuntu/dm-mem-cache.ko
the command 'grep -h 'dm-mod" or "dm-mirror" return nothing while grep -h dm-m shows the above.

 The mount command shows only /dev/sdf1, 4 and 5 as mounted.
 /etc/fstab shows only /dev/sdc0 and scd1 listed along with /dev/sda1, 4, 5 and 3 showing as "/ was on /dev/sda1 during installation" and "/data was on ...." with /home and /swap the same, but are all commented out.

mtab show only /dev/sdf1, 4 and 5 for it's listings.

The command fdisk -l shows all of sda, sdb, sdc, sdd and sdf
 I do not use raid on this system (Jaunty Jackalope).

added:
I just tried accessing all seven partitions again and all messages are the same... the DBus error message. I no longer get the "already mounted" message.


I'm completely stumped. Anyone have a clue what's happened?
I think the only difference between today and yesterday is that yesterday I installed gddrescue in hopes of saving data from the dying /dev/sdc, though it hasn't been run yet.

---

### Post by blueridgedog on 2011-04-24
I would try booting on LiveCD, then issuing a swapoff command, to dismount the automounted swap partition, then test mounting you various partitions one at at time.

---

