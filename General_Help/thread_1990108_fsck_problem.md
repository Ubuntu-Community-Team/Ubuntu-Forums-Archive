---
title: "fsck problem"
date: 2012-05-29
forum: General Help
---

### Post by HRH_H_Crab on 2012-05-29
O.K. first a bit of information.
I have a drive layout that Ubuntu seems to really struggle with.
I have one ide drive with /boot, swap and /.

When the system has booted this is enumerated as sda1, sda2 and sda3 (so sda3 is on root).

I have 4 sata drives which together make up a software raid device (/dev/md1).

Those drives are enumerated as sdb1, sdc1, sdd1, sde1 when the system is booted.

When I boot my system I am getting nagged by ubuntu that it wants to fsck sde3 on the next reboot (which never happens as it doesn't exist).

I had noted that there was some nonsense in /etc/fstab which had / as sde3 so I corrected that to sda3 but this hasnt fixed this issue.

On a side note, something connected with this screws up every single upgrade as the system insists on installing grub to one of the drives in my raid array. Thankfully this has never resulted in lost data but always prevents my system from booting.

Can anyone advise?!

I'm suspecting udev is involved somewhere.

Pastebin with blkid / fdisk / fstab: [http://pastebin.com/QU37r72Q](http://pastebin.com/QU37r72Q)

---

### Post by oldfred on 2012-05-29
I do not know RAID, but grub stores the location to reinstall to on updates.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by HRH_H_Crab on 2012-05-29
Thanks that is good to know and I will look into it.
I've been trying to get some help on irc in #freenode.
Ive now replaced all my /dev/<blah> stuff in fstab with uuids.

Yet I'm still getting nagged to check sde3 (which doesnt exist) each time I log in.

I suspect that that message is actually erroneous in that its noted sde3 somewhere but that device name is now stale.

Do you know how that notification works, and whether I can reset it?

Note I no longer have any reference to sde3 in fstab.

Oldfred: you rock. I never knew about grub-pc. I just reconfigured it and I could instantly see why I've been getting nightmares on each system upgrade. Ive set the correct drive and hopefully thanks to your help those will be a thing of the past. Now I just need to get rid of this pesky reference to sde3 on login!

---

### Post by oldfred on 2012-05-29
I am not seeing the sde3 in fstab or grub anywhere. Is there some script you start with it?

Do log files show anything? System tools, log file viewer. I might look as  dmesg or syslog, but it could be in some other startup log file.

Log files are in:
/var/log

---

