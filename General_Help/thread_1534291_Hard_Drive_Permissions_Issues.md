---
title: "Hard Drive Permissions Issues"
date: 2010-07-19
forum: General Help
---

### Post by oracle002 on 2010-07-19
I have multiple external hard drives connected to my computer vis USB.  Most of the drives are partitioned.  It is a mixed array of FAT, NTFS, and EXT4 drives/partitions.  Recently, the drives have developed an issue with permissions that I can not fathom.
 

 About two weeks ago, Transmission began giving me permissions error messages on files I had successfully completed downloading and was in the middle of downloading.  I had never had this issue before and to my knowledge, had not knowingly changed any settings.  (The only thing that might have been the start of the issue was my computer crashed during some video encoding while running Windows 7.  While the Transmission files were not on the drives where the encoding was occurring, the drive was connected to the machine when the crash occurred.)  In right clicking on the drive's icon on the desktop, the properties box stated that permissions could not be determined.  I checked the other drives.  Some could be determined, others could not be.
 

 Thus began an odyssey to solve the problem, but it is getting worse.  I can not tell you all the steps I've taken because I've lost track.
 

 Here are some of the things I have tried:
 

 Renaming drives/Resetting permissions via Disk Utility and GParted
 Reformatting drives (via Disk Utility and Windows 7)
 Resetting mount points (got the "permissions denied" message, had to be logged in as "root")
 Editing FSTAB
 Editing config-ntfs
 Launching Nautilus through Terminal and reset permissions (although that didn't seem to affect the drives when I right clicked on their icons on the desktop)
 

 The one thing I have not tried was mounting the drives via command line because I am unsure of the syntax to use.
 

 Coming back to the Transmission situation, I bought a new hard drive last week.  I formatted it to EXT4, having read that it was easier to set and reset permissions on a linux-formatted drive.  I set Transmission up to download specifically to a folder on that drive.
 

 Yesterday, I had video encoding to do, which meant working booting to the Windows 7 partition of my computer.  This morning, upon launching Ubuntu and Transmission, I am getting the permissions error message.  Considering Windows couldn't have mounted an EXT4 drive in the first place, I can't see how this would have had any effect.
 

 The end result is that my permissions are seriously pooched at this point.  I'm at the point where the permissions of none of my external drives can be determined or reset (including the EXT4 drive and its partitions) and I have absolutely no idea how to fix the problem.  Any help would be greatly appreciated.
 

 Thank you!

---

### Post by jpl888 on 2010-07-19
Whoa too much information.

Perhaps you could stick to just what the problem is and then give more info when asked. I think the length of your post may be putting people off.

---

### Post by stobbsm on 2010-07-19
go to the directory on the command line, and run:
```
ls -la
```

This will give us an idea of the permission that are sent.
Also, run:
```
dmesg
```
and we'll make sure everything is getting detected properly.

Also, what kind of drives? Hardware involved? Do you receive any error messages besides permissions problems?

---

### Post by oracle002 on 2010-07-19
> **jpl888 said:**
> Whoa too much information.

Perhaps you could stick to just what the problem is and then give more info when asked. I think the length of your post may be putting people off.

Thank you for the reply.  I'll try to keep this brief.

For reasons unclear, permissions to write to my external hard drives can not be determined or reset.  This is a new problem that developed two weeks ago.  I need to figure out how to reset the permissions so I can write to my external hard drives.

---

### Post by jpl888 on 2010-07-19
You are going to have to take a trip down "dreaded command line" lane as the previous poster suggested.

Could you get to a command line type

```
sudo -s
```

then cd into the mount point where the drive is mounted e.g.

```
cd /media/somemountpoint
```

You can find out where it is mounted by typing

```
mount
```

Then type and post the output of 

```
ls -lh
```

and we'll see if we can dig deeper.

---

### Post by oracle002 on 2010-07-19
> **stobbsm said:**
> go to the directory on the command line, and run:
```
ls -la
```This will give us an idea of the permission that are sent.
Also, run:
```
dmesg
```and we'll make sure everything is getting detected properly.

Also, what kind of drives? Hardware involved? Do you receive any error messages besides permissions problems?

Thanks for your response.

The drives:
Western Digital 1TB drive formatted with three EXT4 partitions
Western Digital 500GB drive ntfs
Buffalo 1TB drive, 1 ntfs partition, one FAT partition
Maxtor 100GB ntfs
Western Digital 250GB, four FAT partitions

The error messages are stem from not having permissions to access the drives:  i.e. you must have root access to change permssions, can't create folder without permission, etc.

I am not a linux expert by any means, so I very rarely run things from the command line as I don't always understand the syntax or the response I get.

I ran ls -la as per your suggestion.  This is what came back:

[INDENT]total 472
drwxr-xr-x 41 joe  joe    4096 2010-07-19 09:35 .
drwxr-xr-x  3 root root   4096 2010-06-03 00:06 ..
drwx------  3 joe  joe    4096 2010-06-07 08:17 .adobe
drwxr-xr-x  4 joe  joe    4096 2010-06-16 00:09 .audacity-data
drwxr-xr-x  3 joe  joe    4096 2010-07-08 12:41 .avidemux
-rw-------  1 joe  joe     826 2010-07-19 11:03 .bash_history
-rw-r--r--  1 joe  joe     220 2010-06-03 00:06 .bash_logout
-rw-r--r--  1 joe  joe    3103 2010-06-03 00:06 .bashrc
drwx------  9 joe  joe    4096 2010-07-01 11:35 .cache
drwx------  3 joe  joe    4096 2010-06-03 00:23 .compiz
drwxr-xr-x 15 joe  joe    4096 2010-07-01 11:35 .config
drwx------  3 joe  joe    4096 2010-06-03 00:17 .dbus
drwxr-xr-x  2 joe  joe    4096 2010-07-10 21:12 Desktop
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 Documents
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 Downloads
drwxr-xr-x 19 joe  joe    4096 2010-07-08 00:18 .dvdcss
-rw-------  1 joe  joe      16 2010-06-03 00:17 .esd_auth
-rw-r--r--  1 joe  joe     179 2010-06-03 00:06 examples.desktop
drwxr-xr-x  2 joe  joe    4096 2010-06-08 12:25 .fontconfig
drwxr-xr-x  4 joe  joe    4096 2010-07-19 09:02 .gconf
drwx------  2 joe  joe    4096 2010-07-19 11:05 .gconfd
-rw-r-----  1 joe  joe       0 2010-07-19 10:39 .gksu.lock
drwx------ 11 joe  joe    4096 2010-07-19 09:01 .gnome2
drwx------  2 joe  joe    4096 2010-06-03 00:18 .gnome2_private
drwx------  4 joe  joe    4096 2010-06-07 11:26 .gnucash
drwxr-xr-x  2 joe  joe    4096 2010-07-08 08:07 .gstreamer-0.10
-rw-r--r--  1 joe  joe     127 2010-07-19 09:02 .gtk-bookmarks
dr-x------  3 joe  joe       0 2010-07-19 09:02 .gvfs
-rw-------  1 joe  joe   15886 2010-07-19 09:02 .ICEauthority
drwxr-xr-x  2 joe  joe    4096 2010-07-07 08:31 .icedteaplugin
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:22 .icons
drwx------  3 joe  joe    4096 2010-06-04 23:12 .kde
drwx------  3 joe  joe    4096 2010-06-03 09:18 .local
drwx------  3 joe  joe    4096 2010-06-07 08:17 .macromedia
drwxr-xr-x  4 joe  joe    4096 2010-06-03 00:18 .mozilla
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 Music
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 .nautilus
drwxr-xr-x  3 joe  joe    4096 2010-07-07 08:31 .netx
drwxr-xr-x  3 joe  joe    4096 2010-06-03 15:34 .openoffice.org
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 Pictures
-rw-r--r--  1 joe  joe     675 2010-06-03 00:06 .profile
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 Public
drwx------  2 joe  joe    4096 2010-07-19 09:02 .pulse
-rw-------  1 joe  joe     256 2010-06-03 00:17 .pulse-cookie
-rw-------  1 joe  joe  238591 2010-07-19 08:41 .recently-used.xbel
-rw-r--r--  1 joe  joe       0 2010-06-03 18:06 .sudo_as_admin_successful
drwxr-xr-x  4 joe  joe    4096 2010-06-21 06:02 .sudoku
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 Templates
-rw-r--r--  1 joe  joe    8553 2010-07-10 00:12 testdisk.log
-rw-r--r--  1 joe  joe    2970 2010-07-01 11:43 test.xptv
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:22 .themes
drwx------  4 joe  joe    4096 2010-06-03 00:22 .thumbnails
drwx------  2 joe  joe    4096 2010-06-30 09:41 .update-notifier
drwxr-xr-x  2 joe  joe    4096 2010-06-03 00:17 Videos
drwxr-xr-x  2 joe  joe    4096 2010-07-13 08:33 .xine
-rw-------  1 joe  joe    5253 2010-07-19 11:14 .xsession-errors
-rw-------  1 joe  joe    3895 2010-07-19 09:01 .xsession-errors.old
[/INDENT]Unfortunately, this doesn't mean anything to me, so I can't troubleshoot it.

I then ran dmsg:

[INDENT][ 8021.789559] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8021.789574] end_request: I/O error, dev sr0, sector 256
[ 8021.792250] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8021.792256] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8021.792263] Info fld=0x40, ILI
[ 8021.792266] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8021.792274] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8021.792289] end_request: I/O error, dev sr0, sector 256
[ 8021.922698] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8021.922706] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8021.922714] Info fld=0x22, ILI
[ 8021.922717] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8021.922726] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 22 00 00 02 00
[ 8021.922741] end_request: I/O error, dev sr0, sector 136
[ 8021.926966] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8021.926972] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8021.926979] Info fld=0x22, ILI
[ 8021.926982] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8021.926990] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 22 00 00 02 00
[ 8021.927005] end_request: I/O error, dev sr0, sector 136
[ 8021.931333] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8021.931339] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8021.931346] Info fld=0x24, ILI
[ 8021.931349] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8021.931357] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 24 00 00 02 00
[ 8021.931372] end_request: I/O error, dev sr0, sector 144
[ 8021.935717] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8021.935723] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8021.935730] Info fld=0x24, ILI
[ 8021.935733] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8021.935740] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 24 00 00 02 00
[ 8021.935755] end_request: I/O error, dev sr0, sector 144
[ 8022.042387] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.042393] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.042400] Info fld=0x28, ILI
[ 8022.042403] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.042411] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 28 00 00 02 00
[ 8022.042426] end_request: I/O error, dev sr0, sector 160
[ 8022.045128] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.045134] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.045141] Info fld=0x28, ILI
[ 8022.045143] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.045151] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 28 00 00 02 00
[ 8022.045166] end_request: I/O error, dev sr0, sector 160
[ 8022.142657] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.142663] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.142670] Info fld=0x30, ILI
[ 8022.142673] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.142681] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.142696] end_request: I/O error, dev sr0, sector 192
[ 8022.145396] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.145402] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.145409] Info fld=0x30, ILI
[ 8022.145412] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.145420] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.145435] end_request: I/O error, dev sr0, sector 192
[ 8022.241481] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.241487] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.241495] Info fld=0x40, ILI
[ 8022.241497] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.241505] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8022.241520] end_request: I/O error, dev sr0, sector 256
[ 8022.244204] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.244211] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.244218] Info fld=0x40, ILI
[ 8022.244221] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.244229] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8022.244244] end_request: I/O error, dev sr0, sector 256
[ 8022.348897] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.348904] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.348911] Info fld=0x20, ILI
[ 8022.348915] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.348923] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8022.348938] end_request: I/O error, dev sr0, sector 128
[ 8022.351607] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.351612] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.351619] Info fld=0x20, ILI
[ 8022.351622] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.351630] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8022.351645] end_request: I/O error, dev sr0, sector 128
[ 8022.354573] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.354579] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.354586] Info fld=0x20, ILI
[ 8022.354589] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.354597] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8022.354612] end_request: I/O error, dev sr0, sector 128
[ 8022.357286] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.357292] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.357300] Info fld=0x20, ILI
[ 8022.357303] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.357311] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8022.357326] end_request: I/O error, dev sr0, sector 128
[ 8022.359988] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.359994] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.360016] Info fld=0x20, ILI
[ 8022.360019] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.360027] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8022.360042] end_request: I/O error, dev sr0, sector 128
[ 8022.362703] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.362710] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.362717] Info fld=0x20, ILI
[ 8022.362720] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.362728] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8022.362742] end_request: I/O error, dev sr0, sector 128
[ 8022.366875] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.366881] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.366888] Info fld=0x24, ILI
[ 8022.366891] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.366899] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 24 00 00 02 00
[ 8022.366914] end_request: I/O error, dev sr0, sector 144
[ 8022.521173] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.521180] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.521188] Info fld=0x40, ILI
[ 8022.521191] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.521200] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8022.521216] end_request: I/O error, dev sr0, sector 256
[ 8022.523912] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.523919] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.523926] Info fld=0x40, ILI
[ 8022.523929] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.523938] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8022.523953] end_request: I/O error, dev sr0, sector 256
[ 8022.526858] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.526865] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.526872] Info fld=0x40, ILI
[ 8022.526875] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.526883] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8022.526898] end_request: I/O error, dev sr0, sector 256
[ 8022.640530] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.640538] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.640547] Info fld=0x24, ILI
[ 8022.640550] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.640559] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 24 00 00 02 00
[ 8022.640575] end_request: I/O error, dev sr0, sector 144
[ 8022.724510] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.724518] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.724526] Info fld=0x40, ILI
[ 8022.724529] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.724538] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8022.724553] end_request: I/O error, dev sr0, sector 256
[ 8022.829019] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.829027] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.829035] Info fld=0x30, ILI
[ 8022.829038] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.829047] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.829062] end_request: I/O error, dev sr0, sector 192
[ 8022.831732] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.831738] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.831745] Info fld=0x30, ILI
[ 8022.831748] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.831756] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.831770] end_request: I/O error, dev sr0, sector 192
[ 8022.834696] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.834702] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.834709] Info fld=0x30, ILI
[ 8022.834712] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.834720] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.834735] end_request: I/O error, dev sr0, sector 192
[ 8022.837411] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.837417] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.837424] Info fld=0x30, ILI
[ 8022.837427] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.837435] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.837450] end_request: I/O error, dev sr0, sector 192
[ 8022.840116] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.840123] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.840129] Info fld=0x30, ILI
[ 8022.840132] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.840140] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.840155] end_request: I/O error, dev sr0, sector 192
[ 8022.842815] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.842821] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.842828] Info fld=0x30, ILI
[ 8022.842831] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.842839] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.842854] end_request: I/O error, dev sr0, sector 192
[ 8022.845407] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.845414] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.845421] Info fld=0x30, ILI
[ 8022.845424] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.845432] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.845447] end_request: I/O error, dev sr0, sector 192
[ 8022.848096] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.848102] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.848109] Info fld=0x30, ILI
[ 8022.848112] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.848121] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.848136] end_request: I/O error, dev sr0, sector 192
[ 8022.850623] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.850629] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.850636] Info fld=0x30, ILI
[ 8022.850639] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.850647] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.850661] end_request: I/O error, dev sr0, sector 192
[ 8022.853328] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.853334] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.853340] Info fld=0x30, ILI
[ 8022.853343] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.853351] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 30 00 00 02 00
[ 8022.853367] end_request: I/O error, dev sr0, sector 192
[ 8022.972931] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.972939] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.972947] Info fld=0x60, ILI
[ 8022.972950] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.972959] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 60 00 00 02 00
[ 8022.972976] end_request: I/O error, dev sr0, sector 384
[ 8022.975667] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.975673] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.975680] Info fld=0x60, ILI
[ 8022.975683] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.975691] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 60 00 00 02 00
[ 8022.975706] end_request: I/O error, dev sr0, sector 384
[ 8022.978910] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.978916] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.978922] Info fld=0x62, ILI
[ 8022.978925] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.978934] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 62 00 00 02 00
[ 8022.978948] end_request: I/O error, dev sr0, sector 392
[ 8022.981615] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.981621] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.981628] Info fld=0x62, ILI
[ 8022.981631] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.981639] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 62 00 00 02 00
[ 8022.981654] end_request: I/O error, dev sr0, sector 392
[ 8022.990901] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.990907] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.990914] Info fld=0x64, ILI
[ 8022.990917] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.990925] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 64 00 00 02 00
[ 8022.990940] end_request: I/O error, dev sr0, sector 400
[ 8022.993619] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8022.993625] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8022.993631] Info fld=0x64, ILI
[ 8022.993634] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8022.993642] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 64 00 00 02 00
[ 8022.993657] end_request: I/O error, dev sr0, sector 400
[ 8023.153070] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.153078] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.153086] Info fld=0xe0, ILI
[ 8023.153089] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.153098] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 e0 00 00 02 00
[ 8023.153114] end_request: I/O error, dev sr0, sector 896
[ 8023.155801] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.155807] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.155814] Info fld=0xe0, ILI
[ 8023.155816] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.155824] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 e0 00 00 02 00
[ 8023.155839] end_request: I/O error, dev sr0, sector 896
[ 8023.159042] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.159048] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.159055] Info fld=0xe2, ILI
[ 8023.159058] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.159066] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 e2 00 00 02 00
[ 8023.159081] end_request: I/O error, dev sr0, sector 904
[ 8023.161753] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.161759] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.161766] Info fld=0xe2, ILI
[ 8023.161769] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.161777] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 e2 00 00 02 00
[ 8023.161791] end_request: I/O error, dev sr0, sector 904
[ 8023.171019] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.171025] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.171032] Info fld=0xe4, ILI
[ 8023.171035] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.171043] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 e4 00 00 02 00
[ 8023.171058] end_request: I/O error, dev sr0, sector 912
[ 8023.173736] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.173742] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.173749] Info fld=0xe4, ILI
[ 8023.173752] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.173760] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 e4 00 00 02 00
[ 8023.173775] end_request: I/O error, dev sr0, sector 912
[ 8023.340249] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.340255] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.340262] Info fld=0x20, ILI
[ 8023.340265] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.340274] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.340288] end_request: I/O error, dev sr0, sector 128
[ 8023.342963] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.342968] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.342975] Info fld=0x20, ILI
[ 8023.342978] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.342986] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.343001] end_request: I/O error, dev sr0, sector 128
[ 8023.345928] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.345934] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.345941] Info fld=0x20, ILI
[ 8023.345944] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.345951] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.345966] end_request: I/O error, dev sr0, sector 128
[ 8023.348642] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.348648] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.348655] Info fld=0x20, ILI
[ 8023.348658] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.348666] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.348680] end_request: I/O error, dev sr0, sector 128
[ 8023.351352] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.351358] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.351365] Info fld=0x20, ILI
[ 8023.351368] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.351375] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.351390] end_request: I/O error, dev sr0, sector 128
[ 8023.358234] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.358240] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.358246] Info fld=0x24, ILI
[ 8023.358249] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.358257] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 24 00 00 02 00
[ 8023.358272] end_request: I/O error, dev sr0, sector 144
[ 8023.360953] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.360959] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.360965] Info fld=0x20, ILI
[ 8023.360968] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.360976] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.360991] end_request: I/O error, dev sr0, sector 128
[ 8023.363656] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.363662] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.363669] Info fld=0x22, ILI
[ 8023.363672] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.363680] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 22 00 00 02 00
[ 8023.363694] end_request: I/O error, dev sr0, sector 136
[ 8023.366377] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.366383] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.366390] Info fld=0x22, ILI
[ 8023.366393] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.366401] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 22 00 00 02 00
[ 8023.366416] end_request: I/O error, dev sr0, sector 136
[ 8023.369083] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.369089] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.369096] Info fld=0x20, ILI
[ 8023.369099] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.369107] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.369121] end_request: I/O error, dev sr0, sector 128
[ 8023.371787] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.371793] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.371800] Info fld=0x20, ILI
[ 8023.371803] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.371811] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.371825] end_request: I/O error, dev sr0, sector 128
[ 8023.374345] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.374351] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.374358] Info fld=0x20, ILI
[ 8023.374361] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.374369] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.374383] end_request: I/O error, dev sr0, sector 128
[ 8023.376902] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.376908] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.376915] Info fld=0x20, ILI
[ 8023.376918] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.376926] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.376940] end_request: I/O error, dev sr0, sector 128
[ 8023.379599] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.379604] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.379611] Info fld=0x20, ILI
[ 8023.379614] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.379622] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.379636] end_request: I/O error, dev sr0, sector 128
[ 8023.382303] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.382309] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.382316] Info fld=0x20, ILI
[ 8023.382319] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.382327] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.382341] end_request: I/O error, dev sr0, sector 128
[ 8023.385028] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.385034] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.385041] Info fld=0x20, ILI
[ 8023.385044] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.385052] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.385066] end_request: I/O error, dev sr0, sector 128
[ 8023.387733] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.387739] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.387745] Info fld=0x20, ILI
[ 8023.387748] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.387756] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.387771] end_request: I/O error, dev sr0, sector 128
[ 8023.390438] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.390444] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.390451] Info fld=0x20, ILI
[ 8023.390454] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.390462] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.390477] end_request: I/O error, dev sr0, sector 128
[ 8023.512471] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.512478] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.512485] Info fld=0x40, ILI
[ 8023.512488] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.512496] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8023.512511] end_request: I/O error, dev sr0, sector 256
[ 8023.512515] __ratelimit: 446 callbacks suppressed
[ 8023.512520] Buffer I/O error on device sr0, logical block 64
[ 8023.512524] Buffer I/O error on device sr0, logical block 65
[ 8023.515229] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.515235] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.515242] Info fld=0x40, ILI
[ 8023.515245] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.515253] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8023.515267] end_request: I/O error, dev sr0, sector 256
[ 8023.515271] Buffer I/O error on device sr0, logical block 64
[ 8023.515276] Buffer I/O error on device sr0, logical block 65
[ 8023.631867] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.631873] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.631880] Info fld=0x24, ILI
[ 8023.631883] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.631891] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 24 00 00 02 00
[ 8023.631906] end_request: I/O error, dev sr0, sector 144
[ 8023.631911] Buffer I/O error on device sr0, logical block 36
[ 8023.631916] Buffer I/O error on device sr0, logical block 37
[ 8023.746973] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.746980] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.746988] Info fld=0x20, ILI
[ 8023.746991] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.746999] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.747014] end_request: I/O error, dev sr0, sector 128
[ 8023.747020] Buffer I/O error on device sr0, logical block 32
[ 8023.747024] Buffer I/O error on device sr0, logical block 33
[ 8023.752961] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.752967] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.752974] Info fld=0x22, ILI
[ 8023.752977] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.752985] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 22 00 00 02 00
[ 8023.753000] end_request: I/O error, dev sr0, sector 136
[ 8023.753004] Buffer I/O error on device sr0, logical block 34
[ 8023.753009] Buffer I/O error on device sr0, logical block 35
[ 8023.755699] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.755704] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.755711] Info fld=0x22, ILI
[ 8023.755714] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.755722] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 22 00 00 02 00
[ 8023.755737] end_request: I/O error, dev sr0, sector 136
[ 8023.764977] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.764983] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.764990] Info fld=0x24, ILI
[ 8023.764993] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.765000] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 24 00 00 02 00
[ 8023.765015] end_request: I/O error, dev sr0, sector 144
[ 8023.767690] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.767696] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.767702] Info fld=0x20, ILI
[ 8023.767705] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.767714] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.767728] end_request: I/O error, dev sr0, sector 128
[ 8023.770401] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.770407] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.770414] Info fld=0x20, ILI
[ 8023.770417] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.770425] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.770440] end_request: I/O error, dev sr0, sector 128
[ 8023.773111] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.773118] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.773124] Info fld=0x20, ILI
[ 8023.773127] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.773135] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.773150] end_request: I/O error, dev sr0, sector 128
[ 8023.775842] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.775848] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.775854] Info fld=0x20, ILI
[ 8023.775857] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.775865] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.775880] end_request: I/O error, dev sr0, sector 128
[ 8023.778546] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.778552] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.778559] Info fld=0x20, ILI
[ 8023.778562] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.778569] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.778584] end_request: I/O error, dev sr0, sector 128
[ 8023.781105] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.781111] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.781118] Info fld=0x20, ILI
[ 8023.781121] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.781129] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8023.781144] end_request: I/O error, dev sr0, sector 128
[ 8023.783661] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.783667] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.783674] Info fld=0x22, ILI
[ 8023.783677] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.783685] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 22 00 00 02 00
[ 8023.783699] end_request: I/O error, dev sr0, sector 136
[ 8023.919185] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8023.919193] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8023.919200] Info fld=0x40, ILI
[ 8023.919203] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8023.919212] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[ 8023.919228] end_request: I/O error, dev sr0, sector 256
[ 8024.026582] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8024.026588] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8024.026595] Info fld=0x20, ILI
[ 8024.026599] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8024.026607] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8024.026621] end_request: I/O error, dev sr0, sector 128
[ 8024.030850] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8024.030856] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8024.030862] Info fld=0x20, ILI
[ 8024.030865] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8024.030873] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[ 8024.030888] end_request: I/O error, dev sr0, sector 128
[ 8024.137156] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8024.137162] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8024.137169] Info fld=0x420, ILI
[ 8024.137172] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8024.137180] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 20 00 00 02 00
[ 8024.137195] end_request: I/O error, dev sr0, sector 4224
[ 8024.337289] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8024.337297] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8024.337305] Info fld=0x0, ILI
[ 8024.337308] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8024.337317] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 8024.337333] end_request: I/O error, dev sr0, sector 0
[ 8024.340026] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8024.340032] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8024.340039] Info fld=0x0, ILI
[ 8024.340042] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8024.340050] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 8024.340065] end_request: I/O error, dev sr0, sector 0
[/INDENT]That means even less to me, but to my eye, it looked incomplete int he terminal window as if the top of the entry was cut off for space in the window.

---

### Post by jpl888 on 2010-07-19
The ls -la you've posted is of your home directory which won't help us much, it needs to be of the mount point where the drive is mounted as per my previous post.

Don't worry too much about the sense errors in your dmesg they are only from your CDROM/DVD drive.

---

### Post by oracle002 on 2010-07-19
> **jpl888 said:**
> The ls -la you've posted is of your home directory which won't help us much, it needs to be of the mount point where the drive is mounted as per my previous post.

Don't worry too much about the sense errors in your dmesg they are only from your CDROM/DVD drive.

Forgive my previous misunderstanding.  Here is what comes up when I use the command at my media prompt:

[INDENT]joe@joe-desktop:/media$ la -ls
total 342
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-09 23:31 **[COLOR=SeaGreen]Audio[/COLOR]**
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-17 21:29 **[COLOR=SeaGreen]buffalo\040ntfs[/COLOR]**
  4 drwxr-xr-x  2 root root   4096 2010-07-09 23:31 buffalo ntfs
  4 -rw-r--r--  1 root root    134 2010-07-17 21:13 .created_by_python-fstab
  4 drwxr-xr-x  2 root root   4096 2010-07-09 23:30 Gateway
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-16 09:18 **[COLOR=SeaGreen]My[/COLOR]**
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-17 21:29 **[COLOR=SeaGreen]My\040Book_[/COLOR]**
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-08 18:19 **[COLOR=SeaGreen]My Book[/COLOR]**
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-09 23:31 **[COLOR=SeaGreen]My Book_[/COLOR]**
  4 drwxrwxrwx  1 root root   4096 2010-07-09 21:18 ntfs
  4 drwxr-xr-x  2 root root   4096 2010-07-09 23:30 PQSERVICE
 32 drwxr-xr-x  8 root root  32768 1969-12-31 19:00 sdh1
  4 drwxrwxrwx  1 root root   4096 2010-07-18 10:28 **[COLOR=SeaGreen]sdi1[/COLOR]**
 20 drwxrwxrwx 57 joe  joe   20480 2010-07-17 00:30 **[COLOR=SeaGreen]sdj1[/COLOR]**
  4 drwxrwxrwx  6 joe  joe    4096 2010-07-15 03:28 **[COLOR=SeaGreen]sdj2[/COLOR]**
  4 drwxrwxrwx  4 joe  joe    4096 2010-07-16 17:25 **[COLOR=SeaGreen]sdj3[/COLOR]**
 32 drwxr-xr-x 25 root root  32768 1969-12-31 19:00 sdk1
 32 drwxr-xr-x 18 root root  32768 1969-12-31 19:00 sdk5
 32 drwxr-xr-x 10 root root  32768 1969-12-31 19:00 sdk6
128 drwxr-xr-x 12 root root 131072 1969-12-31 19:00 sdk7
  4 drwxr-xr-x  2 root root   4096 2010-07-09 23:30 SYSTEM_RESERVED
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-09 23:31 **[COLOR=SeaGreen]Video[/COLOR]**
  2 drwx------  5 joe  joe     472 2010-01-28 15:02 WD SmartWare
joe@joe-desktop:/media$ 
[/INDENT]Some of the directories are highlighted.  I've tried to reproduce that here by changing the color of the text.

I ran la -ls for all the various drives listed above and was able to access them, receiving long lists of files and/or folders where appropriate.  I did not think you'd need that all cut and paste here, although I do have it if it will help.

---

### Post by jpl888 on 2010-07-19
Good we are getting somewhere now.

Some of those are owned by root and some of the permissions will only give read only access.

Perhaps a blanket ```
chown -R joe:joe *
```

while within that media directory would be the best idea, it certainly won't make things any worse unless you do it in the wrong location by accident, so be careful.

---

### Post by oracle002 on 2010-07-19
> **jpl888 said:**
> Good we are getting somewhere now.

Some of those are owned by root and some of the permissions will only give read only access.

Perhaps a blanket ```
chown -R joe:joe *
```while within that media directory would be the best idea, it certainly won't make things any worse unless you do it in the wrong location by accident, so be careful.

Thank you.  I will definitely try that.

Since my last post, I tried another trick.  Every time I have manually edited my FSTAB file through sudo gedit fstab, I have saved a back up.  I went to my oldest back up and reactivated it, then rebooted.  Ubuntu did not find some of the renamed drives, but I did get access to the drive where transmission's files are kept.  This leads me to believe the root of the problem is the FSTAB file, or at least some of the troubles can be traced back to that.

---

### Post by oracle002 on 2010-07-19
Tried the chown command in the media directory and got multiple "operation not permitted" error messages.  Following chown, ran la -ls.  This is what I got:

[INDENT]joe@joe-desktop:/media$ la -ls
total 382
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-09 23:31 Audio
  4 drwxrwxrwx  6 joe  joe    4096 2010-07-15 03:28 AudioExt4
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-17 21:29 buffalo\040ntfs
 32 drwx------  8 joe  joe   32768 1969-12-31 19:00 BUFFALO FAT
  4 drwxrwxrwx  1 root root   4096 2010-07-09 18:13 buffalo ntfs
  4 -rw-r--r--  1 root root    134 2010-07-17 21:13 .created_by_python-fstab
 32 drwx------ 25 joe  joe   32768 1969-12-31 19:00 DOC_FILES
  4 drwxrwxrwx  6 joe  joe    4096 2010-07-19 12:32 DownloadsExt4
  8 drwxrwxrwx  1 root root   8192 2010-07-09 21:18 Gateway
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-16 09:18 My
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-17 21:29 My\040Book_
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-08 18:19 My Book
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-09 23:31 My Book_
  4 drwx------  1 joe  joe    4096 2010-07-18 10:28 My Book__
  4 drwxrwxrwx  1 root root   4096 2010-07-09 21:18 ntfs
  4 drwxrwxrwx  1 root root   4096 2009-12-29 02:04 PQSERVICE
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdh1
  4 drwxr-xr-x  2 root root   4096 2010-07-19 10:48 sdi1
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdj1
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdj2
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdj3
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdk1
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdk5
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdk6
  4 drwxr-xr-x  2 root root   4096 2010-07-17 21:29 sdk7
 32 drwx------ 18 joe  joe   32768 1969-12-31 19:00 STORAGE_1
 32 drwx------ 10 joe  joe   32768 1969-12-31 19:00 STORAGE_2
128 drwx------ 12 joe  joe  131072 1969-12-31 19:00 STORAGE_3
  4 drwxrwxrwx  1 root root   4096 2010-03-29 17:21 SYSTEM_RESERVED
  4 drwxrwxrwx  2 joe  joe    4096 2010-07-09 23:31 Video
 20 drwxrwxrwx 57 joe  joe   20480 2010-07-17 00:30 VideoExt4
  2 drwx------  5 joe  joe     472 2010-01-28 15:02 WD SmartWare
[/INDENT]I doesn't look like it accomplished anything.

---

