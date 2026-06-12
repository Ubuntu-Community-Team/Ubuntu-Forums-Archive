---
title: "Backing up the system."
date: 2006-02-07
forum: General Help
---

### Post by lgmdaniel on 2006-02-07
Now I come from a UNIX back ground. Namely AIX, and we have a number of methods to back the system up.
Mksysb: Make System Backup. The makes a restorable backup of the OS volume group on either tape, disk, or DVD-R. That you can then boot from, and restore the system.
savevg: Save Volume Group. This enables you so save your application volume group data to a tape, disk, or DVD-R.
[SIZE="1"]
Note; if your not sure of the term then just treat a volume group as a partition in its own right that can span multipul disks.[/SIZE]

So I have 2 disks in my machine, 80 and 60 GB's, plus I also have CD writter and 2x20GB USB2 external ibm drives. Ubuntu's only using about 8GB at the moment.
I would like to be able to save my OS data to 'restore' my last saved config on one of these medias. But how and what would be best? Or is something like what I do in AIX not possible?

---

### Post by lgmdaniel on 2006-02-08
Any ideas anyone?

---

### Post by obibok on 2006-02-09
I'm sure what you're looking for is quite possible in Ubuntu. I can't really recommend any particular package but you can just search for them in your favourite package manager.

Here are a few:

[SIZE="1"]backuppc - high-performance, enterprise-grade system for backing up PCs
konserve - KDE kicker applet that performs periodic backups
afbackup - Client-Server Backup System (Server side)
backup-manager - command-line backup tool
backup2l - low-maintenance backup/restore tool for mountable media
backupninja - lightweight, extensible meta-backup system
bacula - Network backup, recovery and verification (Meta-package)
bkp - Backup utilities
cdbackup - CD-R(W) backup utility
cdrw-taper - taper replacement for amanda to support backups to CD-RW or DVD+RW
chiark-backup - backup system for small systems and networks
cpbk - a mirroring utility for backing up your files
dar - Disk ARchive: Backup directory tree and files
dirvish - Filesystem based backup system using rsync
dump - 4.4bsd dump and restore for ext2 filesystems
duplicity - encrypted bandwidth-efficient backup
dvbackup - backup tool using MiniDV camcorders
faubackup - Backup System using a Filesystem for Storage
filetraq - Small utility to keep track of changes in config files
flexbackup - Flexible backup tool for small to medium sized installations
floppybackup - Floppy backup using a diversity of floppy formats
hdup - Filesystem duplicator and backup
ibackup - Automated backups (even remote) of machine configurations
kdar - archive data to disc
mondo - powerful disaster recovery suite
multicd - Backup your data to CD-R/CD-RW
partimage - backup partitions into a compressed image file
pdumpfs - a daily backup system similar to Plan9's dumpfs
rdiff-backup - Backup program to use deltas for history
simplebackup - Simple backup tool
slbackup - Skolelinux Backup system
storebackup - fancy compressing managing checksumming hard-linking cp -rua
sbackup - Simple Backup Suite for desktop use
kdat - a KDE tape backup tool[/SIZE]

---

### Post by lgmdaniel on 2006-02-09
> partimage - backup partitions into a compressed image file

This just might be what I'm looking for.. ;)  ta...

---

