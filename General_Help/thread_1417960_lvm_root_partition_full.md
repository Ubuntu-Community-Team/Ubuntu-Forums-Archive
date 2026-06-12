---
title: "lvm root partition full"
date: 2010-02-28
forum: General Help
---

### Post by incubus0h on 2010-02-28
Hi guys:

I have multiple LVM partitions on my 9.10 desktop. The  /boot partition is outside the
LVM. 

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
[B]/dev/mapper/server-root
                       4805760   4559672      1968 100% /[/B]
udev                   1030104       360   1029744   1% /dev
none                   1030104       232   1029872   1% /dev/shm
none                   1030104       288   1029816   1% /var/run
none                   1030104         0   1030104   0% /var/lock
none                   1030104         0   1030104   0% /lib/init/rw
/dev/sda1               186663     50825    126201  29% /boot
[COLOR=MediumTurquoise]/dev/mapper/server-usr
                      10324408   2904420   6895704  30% /usr[/COLOR]
/dev/mapper/server-var
                       4805760    420440   4141200  10% /var
/dev/mapper/server-tmp
                       4805760    141332   4420308   4% /tmp
[COLOR=MediumTurquoise]/dev/mapper/server-home
                      20642428    408008  19185844   3% /home[/COLOR]
/dev/mapper/server-vbox_win_xp_base
                      20642428     44980  20597448   1% /vbox_win_xp_base
[COLOR=DarkOrange]/dev/mapper/server-smb1
                      58245340    184136  58061204   1% /smb1
/dev/mapper/server-smb2
                      13707612    165056  13542556   2% /smb2
/dev/mapper/server-smb3
                      13707612    165056  13542556   2% /smb3[/COLOR]

All seemed to be going well until I did some LVM partition-related operations
(reduced /dev/mapper/server-home to 20G; increased /dev/mapper/server-usr to 10G;
created 3 new partitions - smb1, smb2 and smb3 for samba share). 

Once I got my samba cofiguration working, I did 'upload' from my backup WinXP 
machine to my samba share /smb1, which is a write-able folder. But I forgot to check 
if all the mount points are mounted or not. Sometime during the upload process, the
samba client (WinXP machine) complained about not enough disk space. When I looked 
at the mount listings ($ mount) I found many of the mount points, including smb1, smb2 
and smb3 are not mounted. So it looks like the uploaded files are stored in the /smb1
directory which is a simple directory, not the mounted LVM partition. 

Since then the (/) which is /dev/mapper/server-root is showing me 100%. After 
resolving the mount related issues (reboot and ran e2fsck under rescue mode on
/home, /usr, /smb1, /smb2, /smb3), I still get 100% full error when I reboot the
machine. 

$ sudo lvs
  LV               VG     Attr   LSize  Origin Snap%  Move Log Copy%  Convert
  smb3             server -wi-ao 13.28G                                      
  home             server -wi-ao 20.00G                                      
  smb2            server -wi-ao 13.28G                                      
  smb1           server -wi-ao 56.43G                                      
  root             server -wi-ao  4.66G                                      
  swap             server -wi-ao  1.86G                                      
  tmp              server -wi-ao  4.66G                                      
  usr              server -wi-ao 10.00G                                      
  var              server -wi-ao  4.66G                                      
  vbox_win_xp_base server -wi-ao 20.00G


Questions:
1. Is there any simple way to fix this problem ?
2. Is there any way to do e2fsck on the LVM root partition (/) , under rescue mode ?

Many thanks,
Incubus0h

---

### Post by incubus0h on 2010-02-28
Found the 'solution'. I am posting it here in case someone is interested:

In my case, the smb1 lvm partition was not mounted, but I still 'uploaded' a lot of
big-size files. After I realised my mistake, I managed all the mount points including the
smb1 partition. But that hid the old uploaded files 'underneath'. So my (/) partition was 
showing that it was 99% full. 

Fix: I un-mounted the smb1 lvm partition. And then I saw all these old uploaded files
under /smb1 directory. Once I removed them, the (/) partition size went back to normal.
I again mounted the smb1 partition and everything is ok!

---

