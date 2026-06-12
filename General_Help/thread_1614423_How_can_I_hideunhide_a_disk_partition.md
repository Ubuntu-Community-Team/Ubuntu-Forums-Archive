---
title: "How can I hide/unhide a disk partition?"
date: 2010-11-05
forum: General Help
---

### Post by oldefoxx on 2010-11-05
According to what I have read to date, Linux should let me hide or unhide a partition by just using gparted or parted, or reverting to fdisk.  Well, all three say you can do it, but none of them does.  According to several sources, there is software available under DOS or Windows for the purpose, but I want to do it as a separate boot method or under Ubuntu when I boot up Live.

Any ideas?

---

### Post by oldefoxx on 2010-11-05
Well, I found part of the answer on my own.  Using the fdisk command under Ubuntu's Terminal mode, I found that these are the disk types that are deemed valid at present:

Command (m for help): l

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       bf  Solaris        
 1  FAT12           24  NEC DOS         81  Minix / old Lin c1  DRDOS/sec (FAT-
 2  XENIX root      39  Plan 9          82  Linux swap / So c4  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c6  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c7  Syrinx         
 5  Extended        41  PPC PReP Boot   85  Linux extended  da  Non-FS data    
 6  FAT16           42  SFS             86  NTFS volume set db  CP/M / CTOS / .
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set de  Dell Utility   
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext df  BootIt         
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       e1  DOS access     
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e3  DOS R/O        
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e4  SpeedStor      
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          eb  BeOS fs        
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi ee  GPT            
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ef  EFI (FAT-12/16/
10  OPUS            55  EZ-Drive        a6  OpenBSD         f0  Linux/PA-RISC b
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f1  SpeedStor      
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f4  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f2  DOS secondary  
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     fb  VMware VMFS    
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fc  VMware VMKCORE 
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fd  Linux raid auto
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid fe  LANstep        
1c  Hidden W95 FAT3 75  PC/IX           be  Solaris boot    ff  BBT            

Command (m for help): 

The Linux types pretty much start at hex 80, and no provision was made for a hidden Linux type.  What I see instead are:

80  Old Minix              
81  Minix / old Lin 
82  Linux swap / So 
83  Linux          
84  OS/2 hidden C:        
85  Linux extended
86  NTFS volume set
87  NTFS volume set
88  Linux plaintext         
8e  Linux LVM

These, along with others for different flavors of DOS and what nots,
including ones associated with specific products or brand names.

I don't know if the list is complete or not, but there are curious gaps
in the numbering sequence, and soem of the other types are really rather
outdated now.  You could manually attempt to change the fs type as a flag to indicate that it is not to be taken as a final, because what you intend later is put the flag back as it was.  That would be possible with
fdisk, but if you tried it with parted or gparted, you would be asking for trouble, because this means choosing another fs that it recognizes, and it would immediately attempt to reformat the partition to match the type you designated, or would fail to correctly see it as a type and not let you make the change to start with.

Hey. if others can arbitrarily define types, like Dell, Novell, BSD, VMWare, Solaris, IBM with OS/2 did, then why can't Ubuntu do the same?
I might suggest grabbing 89 to 8d which seem open at the moment.  Now
apparently some of the fs types available to Linux now aren't known to the version of fdisk that comes with Ubuntu, or maybe they just use a secondary fs flag somewhere within the general Linux fs structure.  I don;t even pretend to know.  But just grabbing a couple of the available hex codes could add a massive weight to what signals can be passed with respect to the fs table.  For instance, 89 could mean Linux (hidden), 8a could mean Ubuntu (special), and 8b could mean Ubuntu (special & hidden).

Get the picture?  Other Distros would have to play a bit of catch up after Ubuntu begins to really make its mark, and Ubuntu could show itself a leader in a whole new area associated with data access and retention.

---

### Post by srs5694 on 2010-11-06
It's unclear what your intent is, but I suspect you're barking up the wrong tree. Linux ignores partition table type codes for most purposes, so changing them will have no effect in Linux. If you want to "hide" a partition *in Linux,* the solution lies in your /etc/fstab configuration, not in the partition table. Specifically, you can create an /etc/fstab entry for a partition but include the "noauto" option, which keeps it from mounting automatically.

---

### Post by oldefoxx on 2010-11-08
Doesn't seem appropriate to go with your noauto approach, unless it can also be made to limit the installer.  It says that undesignated drives and partitions will be ignored during the install,  but I have already found that to be false, at least where the /home folder is concerned.  I was thinking that if I could simply hide the partitions that had a /home on them, that would get me around the awkwardness of dealing with more than one install of Linux using a /home folder for user accounts.  Of course on the other hand, I suppose I could use a different user name with each install, but I prefer tg just deal with a common name and password for each install.

Well, that spoils another prospect for keeping each install free and clear of the others.  I rather liked it, since using parted or gparted would be more visible and understandable than a series of bash commands that appear to be required otherwise.

---

### Post by srs5694 on 2010-11-08
The installer is one of the few Linux tools that *does* pay attention to partition type codes.

You can give users on different installations different home directories while keeping their usernames the same. You need to either specify a particular home directory at account creation time (using -d or --home to useradd, for instance) or change it after the fact with usermod's -d or --home option. (You can also edit /etc/passwd directly, if you prefer.) I don't recall offhand if Ubuntu's installer gives this sort of option at install time, but most installers are pretty limited in this respect. You could install one OS, change its user's home directory (renaming it in the process), and then install another OS using the same username.

---

### Post by dino99 on 2010-11-08
[http://www.ubuntu-unleashed.com/2007/12/howto-hide-partition-volumes-in.html](http://www.ubuntu-unleashed.com/2007/12/howto-hide-partition-volumes-in.html)

---

### Post by oldefoxx on 2010-11-12
The matter of hiding and unhiding a partition from a running instance of Linux was not altogether that important to me. What I want is a way to constrain the actions of the installer as it installs more than one instance of a Linux distro.  If I don't designate a partition for a specific purpose, then hands off.

---

### Post by SeijiSensei on 2010-11-12
That's pretty much the standard behavior of the Ubuntu installer.  I have a drive with Windows, a couple of different Linux distros, and separate partitions for /home and /usr/local.  The partitions I leave unsassigned in the installer remain untouched.  Is there something deeper in your question that I'm missing here?

---

### Post by samMD on 2011-05-21
Im trying to do this to install sc2..as per this guys instructions on youtube...

[http://www.youtube.com/watch?v=n1mblDTZnJE](http://www.youtube.com/watch?v=n1mblDTZnJE)

Is it ok to do this? More Importantly how do I safely do this as in detailed instructions for a noob xD

---

### Post by samMD on 2011-05-22
bump

---

### Post by linuxinstalledfromhdd on 2011-05-22
what exactly is the result or purpose you are looking for?  maybe it can try to find a work-around.

---

