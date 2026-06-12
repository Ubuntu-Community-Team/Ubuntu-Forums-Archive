---
title: "grub2 - the never ending story"
date: 2010-05-02
forum: General Help
---

### Post by rnerwein on 2010-05-02
hi
i installed lucid lynx beta 2 dit an upgrate/update to the offical version an every thing seems fine.
my configuration is:
/dev/sda1               1        1828    14680064   27  Unbekannt ( system recovery i think )
/dev/sda2   *        1828       46484   358701056    7  HPFS/NTFS __________ ( vista C:  )
/dev/sda3           46484       58566    97046524    7  HPFS/NTFS __________ ( vista D:  )
/dev/sda4           58567       91201   262140607    f  W95 Erw. (LBA)
/dev/sda5           58567       58828     2104483+  82  Linux Swap / Solaris
/dev/sda6           58829       61439    20972826   83  Linux _______________( suse 11 /root  - grub )
/dev/sda7           61440       70425    72180013+  83  Linux _______________( suse 11 /home)
/dev/sda8           70426       82663    98301703+  83  Linux _______________( Karmic Koala /root grub2 )
/dev/sda9           82664       91201    68581453+  83  Linux _______________( Karmic Koala /home )
===============================
/dev/sdb1  *  _______ ( solaris 10 grub )
===============================

/dev/sdc1   *           1        5229    42001911   83  Linux __________________( lucid lynx /root grub2 )
/dev/sdc2            5230       44552   315861967    5  Erweiterte
/dev/sdc5            5230        5785     4466038+  82  Linux Swap / Solaris
/dev/sdc6            5786       18659   103410373+  83  Linux _______________( lucid lynx /home )
/dev/sdc7           18660       31470   102904326   83  Linux _______________( backup stuff )
/dev/sdc8           31471       44552   105081133+   7  HPFS/NTFS _________( backup stuff )
================================
and here my problem:
/dev/sdc where the last install occured with lucid lynx i an USB disk and during the installation i wasn't
ask where to place the  the original boot or wich grub should be used. this means when i unplug
the USB disk the system is going to the ">grub rescue" nice joke  ( it's a removable disk and there is nothing to rescue ).
 i tried to change the BIOS settings - no change.
and when i try to boot into vista --> have a look at my grub.cfg entry:
menuentry "Windows Vista (loader) (on /dev/sda1)" {
        insmod ntfs
       [COLOR=Red] set root='(hd0,1)'[/COLOR]
        search --no-floppy --fs-uuid --set 2820378c2037604c
        chainloader +1
}
[COLOR=Blue]this try ends in the nirvana.[/COLOR] ( remember the output of fdisk -l )
but i am a lucky boy - i can use the vista recovery mode this entry is correct:
[COLOR=Green]set root='(hd0,2)'[/COLOR]
i ain't remember when i used windows the last time, but i want to check out the grub2 functionality.

until the installing lucid lynx i used the menu.lst of suse and this works  charmed  !!!!!
and here is another funny ( or not ) stuff wich a never seen before ( output of "mount" )
/dev/sr2 on /media/FRITZ!WLAN USB Stick selfinstall type iso9660 \
(ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400, \
dmode=0500)

FRITZ!WLAN is my Wifi adapter :confused::P
what happen is - the wlan is first connected then about 30 seconds it is disconnected and about 
two minutes later it is coming back and then it will stay ( uff ).

my problem is that the system is going to boot on a removealble disk.
my question is: can i manage it to set grub2 back to use the grub2 of Karmic_Koala, or better the
good old menu.lst which i can use with "vi".
have a nice day.

---

