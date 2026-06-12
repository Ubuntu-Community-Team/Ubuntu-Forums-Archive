---
title: "error 17 and other problems (dual boot vista) HELP ME PLZ"
date: 2009-10-01
forum: General Help
---

### Post by error17 on 2009-10-01
OK so I had everything working fine then i found an xp cd in my house and i made a xp partition so i could install it...next day i turn on my laptop and i get grub error 17!!!!!
so i go looking arround the web and fing no help 
i got on to the ubuntu live cd and went to partition edditor and found that my vista partition had some problems so i wanted to see if i could fix them and ubuntu said it couldnt.
i got this message
GParted 0.3.8

Libparted 1.8.9

   **Delete Logical Partition (ntfs, 15.75 GiB) from /dev/sda**  00:00:00    ( SUCCESS )             calibrate /dev/sda5  00:00:00    ( SUCCESS )             [I]path: /dev/sda5
start: 4096
end: 33028095
size: 33024000 (15.75 GiB)[/I]          delete partition  00:00:00    ( SUCCESS )       
========================================

   **Check and repair filesystem (ntfs) on /dev/sda2**  00:00:06    ( ERROR )             calibrate /dev/sda2  00:00:00    ( SUCCESS )             [I]path: /dev/sda2
start: 33029640
end: 429948607
size: 396918968 (189.27 GiB)[/I]          check filesystem on /dev/sda2 for errors and (if possible) fix them  00:00:06    ( ERROR )             ***ntfsresize -P -i -f -v /dev/sda2***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 203222508032 bytes (203223 MB)
Current device size: 203222511616 bytes (203223 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 41783 (0xa337): extra cluster in $Bitmap
Cluster accounting failed at 62056 (0xf268 ): extra cluster in $Bitmap
Cluster accounting failed at 62057 (0xf269): extra cluster in $Bitmap
Cluster accounting failed at 62058 (0xf26a): extra cluster in $Bitmap
Cluster accounting failed at 62059 (0xf26b): extra cluster in $Bitmap
Cluster accounting failed at 62060 (0xf26c): extra cluster in $Bitmap
Cluster accounting failed at 62061 (0xf26d): extra cluster in $Bitmap
Cluster accounting failed at 62062 (0xf26e): extra cluster in $Bitmap
Cluster accounting failed at 62063 (0xf26f): extra cluster in $Bitmap
Cluster accounting failed at 62064 (0xf270): extra cluster in $Bitmap
Cluster accounting failed at 62065 (0xf271): extra cluster in $Bitmap
Cluster accounting failed at 62066 (0xf272): extra cluster in $Bitmap
Cluster accounting failed at 62067 (0xf273): extra cluster in $Bitmap
Cluster accounting failed at 62068 (0xf274): extra cluster in $Bitmap
Cluster accounting failed at 62069 (0xf275): extra cluster in $Bitmap
Cluster accounting failed at 62070 (0xf276): extra cluster in $Bitmap
Cluster accounting failed at 13143435 (0xc88d8b): extra cluster in $Bitmap
Cluster accounting failed at 13143436 (0xc88d8c): extra cluster in $Bitmap
Cluster accounting failed at 13143437 (0xc88d8d): extra cluster in $Bitmap
Cluster accounting failed at 13143438 (0xc88d8e): extra cluster in $Bitmap
Cluster accounting failed at 13143439 (0xc88d8f): extra cluster in $Bitmap
Cluster accounting failed at 13143440 (0xc88d90): extra cluster in $Bitmap
Cluster accounting failed at 13143441 (0xc88d91): extra cluster in $Bitmap
Cluster accounting failed at 13143442 (0xc88d92): extra cluster in $Bitmap
Cluster accounting failed at 13143443 (0xc88d93): extra cluster in $Bitmap
Cluster accounting failed at 13143444 (0xc88d94): extra cluster in $Bitmap
Cluster accounting failed at 13143445 (0xc88d95): extra cluster in $Bitmap
Cluster accounting failed at 13143446 (0xc88d96): extra cluster in $Bitmap
Cluster accounting failed at 13143447 (0xc88d97): extra cluster in $Bitmap
Cluster accounting failed at 13266249 (0xca6d49): extra cluster in $Bitmap
Cluster accounting failed at 13266250 (0xca6d4a): extra cluster in $Bitmap
Cluster accounting failed at 13266251 (0xca6d4b): extra cluster in $Bitmap
Cluster accounting failed at 13266252 (0xca6d4c): extra cluster in $Bitmap
Cluster accounting failed at 13266253 (0xca6d4d): extra cluster in $Bitmap
Cluster accounting failed at 13266254 (0xca6d4e): extra cluster in $Bitmap
Cluster accounting failed at 13266255 (0xca6d4f): extra cluster in $Bitmap
Cluster accounting failed at 13266256 (0xca6d50): extra cluster in $Bitmap
Cluster accounting failed at 13266257 (0xca6d51): extra cluster in $Bitmap
Cluster accounting failed at 13266258 (0xca6d52): extra cluster in $Bitmap
Cluster accounting failed at 13266259 (0xca6d53): extra cluster in $Bitmap
Cluster accounting failed at 13266260 (0xca6d54): extra cluster in $Bitmap
Cluster accounting failed at 13266261 (0xca6d55): extra cluster in $Bitmap
Cluster accounting failed at 13266262 (0xca6d56): extra cluster in $Bitmap
Cluster accounting failed at 13266263 (0xca6d57): extra cluster in $Bitmap
Cluster accounting failed at 13357293 (0xcbd0ed): extra cluster in $Bitmap
Cluster accounting failed at 13357294 (0xcbd0ee): extra cluster in $Bitmap
Cluster accounting failed at 13357295 (0xcbd0ef): extra cluster in $Bitmap
Cluster accounting failed at 13357296 (0xcbd0f0): extra cluster in $Bitmap
Cluster accounting failed at 13357297 (0xcbd0f1): extra cluster in $Bitmap
Cluster accounting failed at 13357298 (0xcbd0f2): extra cluster in $Bitmap
Cluster accounting failed at 13357299 (0xcbd0f3): extra cluster in $Bitmap
Cluster accounting failed at 13357300 (0xcbd0f4): extra cluster in $Bitmap
Cluster accounting failed at 13357301 (0xcbd0f5): extra cluster in $Bitmap
Cluster accounting failed at 13357302 (0xcbd0f6): extra cluster in $Bitmap
Cluster accounting failed at 13357303 (0xcbd0f7): extra cluster in $Bitmap
Cluster accounting failed at 13357304 (0xcbd0f8 ): extra cluster in $Bitmap
Cluster accounting failed at 13357305 (0xcbd0f9): extra cluster in $Bitmap
Cluster accounting failed at 13357306 (0xcbd0fa): extra cluster in $Bitmap
Cluster accounting failed at 13357307 (0xcbd0fb): extra cluster in $Bitmap
Cluster accounting failed at 38266800 (0x247e7b0): extra cluster in $Bitmap
Cluster accounting failed at 38266801 (0x247e7b1): extra cluster in $Bitmap
Cluster accounting failed at 38266802 (0x247e7b2): extra cluster in $Bitmap
Cluster accounting failed at 38266803 (0x247e7b3): extra cluster in $Bitmap
Cluster accounting failed at 38266804 (0x247e7b4): extra cluster in $Bitmap
Cluster accounting failed at 38266805 (0x247e7b5): extra cluster in $Bitmap
Cluster accounting failed at 38266806 (0x247e7b6): extra cluster in $Bitmap
Cluster accounting failed at 38266807 (0x247e7b7): extra cluster in $Bitmap
Cluster accounting failed at 38266808 (0x247e7b8 ): extra cluster in $Bitmap
Cluster accounting failed at 38266809 (0x247e7b9): extra cluster in $Bitmap
Cluster accounting failed at 38266810 (0x247e7ba): extra cluster in $Bitmap
Cluster accounting failed at 38266811 (0x247e7bb): extra cluster in $Bitmap
Cluster accounting failed at 38266812 (0x247e7bc): extra cluster in $Bitmap
Cluster accounting failed at 38266813 (0x247e7bd): extra cluster in $Bitmap
Cluster accounting failed at 38266814 (0x247e7be): extra cluster in $Bitmap
Cluster accounting failed at 38266815 (0x247e7bf): extra cluster in $Bitmap
Cluster accounting failed at 38285288 (0x2482fe8 ): extra cluster in $Bitmap
Cluster accounting failed at 38285289 (0x2482fe9): extra cluster in $Bitmap
Cluster accounting failed at 38285290 (0x2482fea): extra cluster in $Bitmap
Cluster accounting failed at 38285291 (0x2482feb): extra cluster in $Bitmap
Cluster accounting failed at 38285292 (0x2482fec): extra cluster in $Bitmap
Cluster accounting failed at 38285293 (0x2482fed): extra cluster in $Bitmap
Cluster accounting failed at 38285294 (0x2482fee): extra cluster in $Bitmap
Cluster accounting failed at 38285295 (0x2482fef): extra cluster in $Bitmap
Cluster accounting failed at 38285296 (0x2482ff0): extra cluster in $Bitmap
Cluster accounting failed at 38285297 (0x2482ff1): extra cluster in $Bitmap
Cluster accounting failed at 38285298 (0x2482ff2): extra cluster in $Bitmap
Cluster accounting failed at 38285299 (0x2482ff3): extra cluster in $Bitmap
Cluster accounting failed at 38285300 (0x2482ff4): extra cluster in $Bitmap
Cluster accounting failed at 38285301 (0x2482ff5): extra cluster in $Bitmap
Cluster accounting failed at 38285302 (0x2482ff6): extra cluster in $Bitmap
Cluster accounting failed at 38285303 (0x2482ff7): extra cluster in $Bitmap
Cluster accounting failed at 38527660 (0x24be2ac): extra cluster in $Bitmap
Cluster accounting failed at 38527661 (0x24be2ad): extra cluster in $Bitmap
Cluster accounting failed at 38527662 (0x24be2ae): extra cluster in $Bitmap
Cluster accounting failed at 38527663 (0x24be2af): extra cluster in $Bitmap
Cluster accounting failed at 38527664 (0x24be2b0): extra cluster in $Bitmap
Cluster accounting failed at 38527665 (0x24be2b1): extra cluster in $Bitmap
Cluster accounting failed at 38527666 (0x24be2b2): extra cluster in $Bitmap
Cluster accounting failed at 38527667 (0x24be2b3): extra cluster in $Bitmap
Cluster accounting failed at 38555732 (0x24c5054): extra cluster in $Bitmap
Cluster accounting failed at 38555733 (0x24c5055): extra cluster in $Bitmap
Cluster accounting failed at 38555734 (0x24c5056): extra cluster in $Bitmap
Cluster accounting failed at 38555735 (0x24c5057): extra cluster in $Bitmap
Cluster accounting failed at 38555736 (0x24c5058 -): extra cluster in $Bitmap 
Cluster accounting failed at 38555737 (0x24c5059): extra cluster in $Bitmap
Cluster accounting failed at 38555738 (0x24c505a): extra cluster in $Bitmap
Cluster accounting failed at 38555739 (0x24c505b): extra cluster in $Bitmap
Cluster accounting failed at 38555740 (0x24c505c): extra cluster in $Bitmap
Cluster accounting failed at 38555741 (0x24c505d): extra cluster in $Bitmap
Cluster accounting failed at 38555742 (0x24c505e): extra cluster in $Bitmap
Cluster accounting failed at 38555743 (0x24c505f): extra cluster in $Bitmap
Cluster accounting failed at 38555744 (0x24c5060): extra cluster in $Bitmap
Cluster accounting failed at 38555745 (0x24c5061): extra cluster in $Bitmap
Cluster accounting failed at 38555746 (0x24c5062): extra cluster in $Bitmap
Cluster accounting failed at 38555747 (0x24c5063): extra cluster in $Bitmap
Cluster accounting failed at 38556696 (0x24c5418 ): extra cluster in $Bitmap
Cluster accounting failed at 38556697 (0x24c5419): extra cluster in $Bitmap
Cluster accounting failed at 38556698 (0x24c541a): extra cluster in $Bitmap
Cluster accounting failed at 38556699 (0x24c541b): extra cluster in $Bitmap
Cluster accounting failed at 38556700 (0x24c541c): extra cluster in $Bitmap
Cluster accounting failed at 38556701 (0x24c541d): extra cluster in $Bitmap
Cluster accounting failed at 38556702 (0x24c541e): extra cluster in $Bitmap
Cluster accounting failed at 38556703 (0x24c541f): extra cluster in $Bitmap
Cluster accounting failed at 38556704 (0x24c5420): extra cluster in $Bitmap
Cluster accounting failed at 38556705 (0x24c5421): extra cluster in $Bitmap
Cluster accounting failed at 38556706 (0x24c5422): extra cluster in $Bitmap
Cluster accounting failed at 38556707 (0x24c5423): extra cluster in $Bitmap
Cluster accounting failed at 38556708 (0x24c5424): extra cluster in $Bitmap
Cluster accounting failed at 38556709 (0x24c5425): extra cluster in $Bitmap
Cluster accounting failed at 38556710 (0x24c5426): extra cluster in $Bitmap
Cluster accounting failed at 38556711 (0x24c5427): extra cluster in $Bitmap
Cluster accounting failed at 38556712 (0x24c5428 ): extra cluster in $Bitmap
Cluster accounting failed at 38556713 (0x24c5429): extra cluster in $Bitmap
Cluster accounting failed at 38556714 (0x24c542a): extra cluster in $Bitmap
Cluster accounting failed at 38556715 (0x24c542b): extra cluster in $Bitmap
Cluster accounting failed at 38556716 (0x24c542c): extra cluster in $Bitmap
Cluster accounting failed at 38556717 (0x24c542d): extra cluster in $Bitmap
Cluster accounting failed at 38556718 (0x24c542e): extra cluster in $Bitmap
Cluster accounting failed at 38556719 (0x24c542f): extra cluster in $Bitmap
Cluster accounting failed at 38556720 (0x24c5430): extra cluster in $Bitmap
Cluster accounting failed at 38556721 (0x24c5431): extra cluster in $Bitmap
Cluster accounting failed at 38556722 (0x24c5432): extra cluster in $Bitmap
Cluster accounting failed at 38556723 (0x24c5433): extra cluster in $Bitmap
Cluster accounting failed at 38556724 (0x24c5434): extra cluster in $Bitmap
Cluster accounting failed at 38556725 (0x24c5435): extra cluster in $Bitmap
Cluster accounting failed at 38556726 (0x24c5436): extra cluster in $Bitmap
Cluster accounting failed at 38556727 (0x24c5437): extra cluster in $Bitmap
Cluster accounting failed at 38558768 (0x24c5c30): extra cluster in $Bitmap
Cluster accounting failed at 38558769 (0x24c5c31): extra cluster in $Bitmap
Cluster accounting failed at 38558770 (0x24c5c32): extra cluster in $Bitmap
Cluster accounting failed at 38558771 (0x24c5c33): extra cluster in $Bitmap
Cluster accounting failed at 38558772 (0x24c5c34): extra cluster in $Bitmap
Cluster accounting failed at 38558773 (0x24c5c35): extra cluster in $Bitmap
Cluster accounting failed at 38558774 (0x24c5c36): extra cluster in $Bitmap
Cluster accounting failed at 38558775 (0x24c5c37): extra cluster in $Bitmap
Cluster accounting failed at 38558776 (0x24c5c3[/I]*8 )*[I]: extra cluster in $Bitmap
Cluster accounting failed at 38558777 (0x24c5c39): extra cluster in $Bitmap
Cluster accounting failed at 38558778 (0x24c5c3a): extra cluster in $Bitmap
Cluster accounting failed at 38558779 (0x24c5c3b): extra cluster in $Bitmap
Cluster accounting failed at 38558780 (0x24c5c3c): extra cluster in $Bitmap
Cluster accounting failed at 38558781 (0x24c5c3d): extra cluster in $Bitmap
Cluster accounting failed at 38558782 (0x24c5c3e): extra cluster in $Bitmap
Cluster accounting failed at 38558783 (0x24c5c3f): extra cluster in $Bitmap
Cluster accounting failed at 39261024 (0x2571360): extra cluster in $Bitmap
Cluster accounting failed at 39261025 (0x2571361): extra cluster in $Bitmap
Cluster accounting failed at 39261026 (0x2571362): extra cluster in $Bitmap
Cluster accounting failed at 39261027 (0x2571363): extra cluster in $Bitmap
Cluster accounting failed at 39261028 (0x2571364): extra cluster in $Bitmap
Cluster accounting failed at 39261029 (0x2571365): extra cluster in $Bitmap
Cluster accounting failed at 39261030 (0x2571366): extra cluster in $Bitmap
Cluster accounting failed at 39261031 (0x2571367): extra cluster in $Bitmap
Cluster accounting failed at 39261032 (0x257136[/I]*8 )*[I]: extra cluster in $Bitmap
Cluster accounting failed at 39261033 (0x2571369): extra cluster in $Bitmap
Cluster accounting failed at 39261034 (0x257136a): extra cluster in $Bitmap
Cluster accounting failed at 39261035 (0x257136b): extra cluster in $Bitmap
Cluster accounting failed at 39261036 (0x257136c): extra cluster in $Bitmap
Cluster accounting failed at 39261037 (0x257136d): extra cluster in $Bitmap
Cluster accounting failed at 39261038 (0x257136e): extra cluster in $Bitmap
Cluster accounting failed at 39261039 (0x257136f): extra cluster in $Bitmap
Cluster accounting failed at 39261040 (0x2571370): extra cluster in $Bitmap
Cluster accounting failed at 39261041 (0x2571371): extra cluster in $Bitmap
Cluster accounting failed at 39261042 (0x2571372): extra cluster in $Bitmap
Cluster accounting failed at 39261043 (0x2571373): extra cluster in $Bitmap
Cluster accounting failed at 39261044 (0x2571374): extra cluster in $Bitmap
Cluster accounting failed at 39261045 (0x2571375): extra cluster in $Bitmap
Cluster accounting failed at 39261046 (0x2571376): extra cluster in $Bitmap
Cluster accounting failed at 39261047 (0x2571377): extra cluster in $Bitmap
Cluster accounting failed at 39261048 (0x257137[/I]*8 )*[I]: extra cluster in $Bitmap
Cluster accounting failed at 39261049 (0x2571379): extra cluster in $Bitmap
Cluster accounting failed at 39261050 (0x257137a): extra cluster in $Bitmap
Cluster accounting failed at 39261051 (0x257137b): extra cluster in $Bitmap
Cluster accounting failed at 39261052 (0x257137c): extra cluster in $Bitmap
Cluster accounting failed at 39261053 (0x257137d): extra cluster in $Bitmap
Cluster accounting failed at 39261054 (0x257137e): extra cluster in $Bitmap
Cluster accounting failed at 39261055 (0x257137f): extra cluster in $Bitmap
Cluster accounting failed at 39261056 (0x2571380): extra cluster in $Bitmap
Cluster accounting failed at 39261057 (0x2571381): extra cluster in $Bitmap
Cluster accounting failed at 39261058 (0x2571382): extra cluster in $Bitmap
Cluster accounting failed at 39261059 (0x2571383): extra cluster in $Bitmap
Cluster accounting failed at 39261060 (0x2571384): extra cluster in $Bitmap
Cluster accounting failed at 39261061 (0x2571385): extra cluster in $Bitmap
Cluster accounting failed at 39261062 (0x2571386): extra cluster in $Bitmap
Cluster accounting failed at 39261063 (0x2571387): extra cluster in $Bitmap
Cluster accounting failed at 39261064 (0x257138[/I]*8 )*[I]: extra cluster in $Bitmap
Cluster accounting failed at 39261065 (0x2571389): extra cluster in $Bitmap
Cluster accounting failed at 39261066 (0x257138a): extra cluster in $Bitmap
Cluster accounting failed at 39261067 (0x257138b): extra cluster in $Bitmap
Cluster accounting failed at 39261068 (0x257138c): extra cluster in $Bitmap
Cluster accounting failed at 39261069 (0x257138d): extra cluster in $Bitmap
Cluster accounting failed at 39261070 (0x257138e): extra cluster in $Bitmap
Cluster accounting failed at 39261071 (0x257138f): extra cluster in $Bitmap
Cluster accounting failed at 39261072 (0x2571390): extra cluster in $Bitmap
Cluster accounting failed at 39261073 (0x2571391): extra cluster in $Bitmap
Cluster accounting failed at 39261074 (0x2571392): extra cluster in $Bitmap
Cluster accounting failed at 39261075 (0x2571393): extra cluster in $Bitmap
Cluster accounting failed at 39261076 (0x2571394): extra cluster in $Bitmap
Cluster accounting failed at 39261077 (0x2571395): extra cluster in $Bitmap
Cluster accounting failed at 39261078 (0x2571396): extra cluster in $Bitmap
Cluster accounting failed at 39261079 (0x2571397): extra cluster in $Bitmap
Cluster accounting failed at 39261080 (0x257139[/I]*8 )*[I]: extra cluster in $Bitmap
Cluster accounting failed at 39261081 (0x2571399): extra cluster in $Bitmap
Cluster accounting failed at 39261082 (0x257139a): extra cluster in $Bitmap
Cluster accounting failed at 39261083 (0x257139b): extra cluster in $Bitmap
Cluster accounting failed at 39261084 (0x257139c): extra cluster in $Bitmap
Cluster accounting failed at 39261085 (0x257139d): extra cluster in $Bitmap
Cluster accounting failed at 39261086 (0x257139e): extra cluster in $Bitmap
Cluster accounting failed at 39261087 (0x257139f): extra cluster in $Bitmap
Cluster accounting failed at 39468076 (0x25a3c2c): extra cluster in $Bitmap
Cluster accounting failed at 39468077 (0x25a3c2d): extra cluster in $Bitmap
Cluster accounting failed at 39468078 (0x25a3c2e): extra cluster in $Bitmap
Cluster accounting failed at 39468079 (0x25a3c2f): extra cluster in $Bitmap
Cluster accounting failed at 39468080 (0x25a3c30): extra cluster in $Bitmap
Cluster accounting failed at 39468081 (0x25a3c31): extra cluster in $Bitmap
Cluster accounting failed at 39468082 (0x25a3c32): extra cluster in $Bitmap
Cluster accounting failed at 39468083 (0x25a3c33): extra cluster in $Bitmap
Cluster accounting failed at 39468084 (0x25a3c34): extra cluster in $Bitmap
Cluster accounting failed at 39468085 (0x25a3c35): extra cluster in $Bitmap
Cluster accounting failed at 39468086 (0x25a3c36): extra cluster in $Bitmap
Cluster accounting failed at 39468087 (0x25a3c37): extra cluster in $Bitmap
Cluster accounting failed at 39468088 (0x25a3c3[/I]*8 )*[I]: extra cluster in $Bitmap
Cluster accounting failed at 39468089 (0x25a3c39): extra cluster in $Bitmap
Cluster accounting failed at 39468090 (0x25a3c3a): extra cluster in $Bitmap
Cluster accounting failed at 39468091 (0x25a3c3b): extra cluster in $Bitmap
Filesystem check failed! Totally 243 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.[/I]

HELP ME

---

### Post by oldfred on 2009-10-02
Using the partition editor you may have messed up the Vista partition. Info on the issue:
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

This forum has every other grub issue at error 17 (it seems).
info on this
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)
Herman says a file system check usual will solve it.
But if you edited partitions you may have renumbered them and then all you entries in menu.lst and fstab need to be updated.

From a liveCD run testdisk and see what it tells you about your partitions.

---

