---
title: "Novice Mountaineer"
date: 2006-05-29
forum: General Help
---

### Post by tamal_patra on 2006-05-29
](*,) [INDENT][CENTER][FONT="Comic Sans MS"]I have Windows XP preloaded. So I want to mount the NTFS partitions of my HDD into Ubuntu for both [SIZE="4"][COLOR="SlateGray"]Read & Write[/COLOR][/SIZE]. Also, "[SIZE="3"][COLOR="Teal"]mounting[/COLOR][/SIZE]" is a very new term for me. How can I reach to the peak??[/FONT][/CENTER][/INDENT]

---

### Post by Hanj on 2006-05-29
Unfortunately, write support to ntfs is experimental (because MS won't release the specs for the file system), so it's really recommended that you *don't* enable writing to ntfs partitions. It might screw your entire partition up.

---

### Post by psychicdragon on 2006-05-29
I believe the linux NTFS driver only supports read operations at the moment. You can have you NTFS partition mounted as read-only on boot-up fairly easily.

Run these commands in the terminal (The terminal is located in the Applications menu, under Accessories):
```
sudo mkdir /media/windows
sudo gedit /etc/fstab
```

*** Note: This next part presumes that WIndows XP is the first partition on the primary drive. If it's not just post a reply.

Add this line to the end of file that opens (leave a blank line at the end too):
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```
Save the file. Then, finally, run this command:
```
sudo mount -a
```

The disk should show up in the file manager now, and on your desktop if you have that turned on.

---

### Post by sugonaut on 2006-05-29
If you _need_ to share files between Windows and Linux, you'll need to set up a FAT32 partition.  Both can read and write to this filesystem.

Creating this partition is possible using either Windows or Linux.  If you're not familiar with partitioning, use a slick GUI tool.  GParted looks like a good one although I've never used it.  For Windows there's Partition Magic (~50 USD) at the local computer magastore.

Be very cautious creating partitions.  You can really hose things up in a hurry.  Before doing anything, make sure your data is backed up.

I've got a nice setup right now, but I planned ahead.  Here are the details...

I recently bought a new laptop; the HD is 80 GB.  At first all 80 were dedicated to XP.  I have a copy of Partition Magic.  I installed that.  I fired it up and created my 1st new partition, specifying a linux filesystem at ~40 GB.  I then created a 2nd partition, specifying FAT32 at ~20GB.  For this 2nd FAT32 partition, I specified to take space away from my existing NTFS filesystem.  So afterwards I had 3 physical partitions; 50% for Ubuntu, 25% for WinXP, and 25% for FAT32 sharedrive.

After I created my partitions, I quickly jammed my Ubuntu CD into the tray and rebooted.  When I was prompted to make some decisions about where Ubuntu was to be installed, I specified that 40 GB Linux filesystem.  Done.

The term "mount" basically means "to make a device available".  Everything in Linux is a device more or less.  Most distros automagically mount stuff for us - the common things like CD drives, DVD drives, etc.  The reason why we sometimes have to mount devices has to do with the history of Linux.  It was primarily developed to be a network/server OS and has grown into a desktop OS.  This is the opposite of Windows which started out as a desktop OS and grew into a...oh wait..well, I think some folks use it as a server.

To mount a new FAT32 partition in Ubuntu, just go to System -> Administration -> Disks.  Click on the partition with the FAT32 filesystem and click Enable.

Good luck.  And look forward to the day when we won't need those Windows partitions.

---

