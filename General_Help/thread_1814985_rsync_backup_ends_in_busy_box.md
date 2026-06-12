---
title: "rsync backup ends in busy box"
date: 2011-07-30
forum: General Help
---

### Post by Ordes on 2011-07-30
i am trying to keep a backup of my root on a second partition using rsync.

sda1 system
sda2 system-BAK
sdb1 /home

in my rsync i exclude following folders / files ( taken from here >> [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR))

/etc/fstab
/home/*
/proc/*
/lost+found/*
/sys/*
/mnt/*
/media/cdrom/*
/media/floppy/*
/media/floppy0/*
/media/hdd3/*
/media/hdd4/*
/media/system-BAK
/dev/*

for the fstab, i have edited the fstab on BAK in order to fit for sda2.

for the rsync command i use: 

sudo rsync --delete -azvv --exclude-from '~/.../exclude.txt' / /media/system-BAK

---
Problem: When i load up the backup, the ubuntu screen comes up, but than before it goes to the GUI, it goes to the busy box. I tried the "exit" command; but didnt work. and so far i have no clue nor idea what the busy box is all about or why it comes up, or where the problems of the sync is...

txs for suggestions

---

### Post by dim_hyder on 2011-07-30
What about the HDD MBR etc?

It looks like the backup HDD already has some non-related boot sector and grub install.

I'm investigating - will post will more info.

---

### Post by dim_hyder on 2011-07-30
Clone the disk first with Clonezilla or another tool and the run the regular rsync.

The backup disk should then be bootable.

It's probably best however to test it's still bootable after doing system updates.

---

### Post by Ordes on 2011-07-31
i actually dont think it is connected with grub or boot...

as they both show up in grub, (sda1 & sda2), and r both bootable.

just on sda2 during the booting ( the ubu logo with the little dots), instead of going to the login in GUI, it drops to the busy box.

it must have something to do with the root device sda2. when trying to run in recovery mode its dropping into shell after not finding the UUID of sda2. but when i look at sda2 in gaprted than it is the right UUID.

also, i get the message, >> missing modules /proc/modules; ls/dev

---

