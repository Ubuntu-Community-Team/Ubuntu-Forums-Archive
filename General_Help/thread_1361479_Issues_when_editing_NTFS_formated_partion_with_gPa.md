---
title: "Issues when editing NTFS formated partion with gParted!!!"
date: 2009-12-22
forum: General Help
---

### Post by Luftdruck on 2009-12-22
Hallo und guten Morgen!!
 I have an issue with my Laptop (lenovo) on which i have installed both Windows Vista and Ubuntu. I use the grubloader and gparted to handle both partitions. The other day I concluded that 40gb (ntfs) and 100gb (fat32) was an inconvenient distribution of drive space so I decided to resize both partitions......;D  
 Using the gparted live cd I was able to downsize the fat32 partition but later had problems modifying the ntfs partition. These are the details that gparted can share with us here:
---------------------------------------------------------------------------------------------------------------------------------

 GParted 0.3.5
Libparted 1.7.1
                                      [SIZE=2]**Dateisystem (ntfs) auf /dev/sda2 Überprüfen und reparieren             **00:12 
[/SIZE]
[SIZE=2]( ERROR )[/SIZE]              
                                                                                                                                                       [SIZE=1]/dev/sda2 kalibrieren 00:00( SUCCES )                      [/SIZE]
                                                                                                                                                                                                                                                              [SIZE=2][I]Pfad: /dev/sda2
Anfang: 168908800
Ende:                                     299804671
GrÃ¶Ã&#376;e: 130895872 (62.42 GB)[/I][/SIZE]                                      
                                                                                                                                                                                                                                                                                                      [SIZE=1]Dateisystem auf /dev/sda2 auf Fehler Ã¼berprÃ¼fen und                         (falls mÃ¶glich) diese beheben 00:12  ( ERROR )                          [/SIZE]
                                                                                                                                                                                                                                                                                           [SIZE=1]***ntfsresize -P -i -f -v /dev/sda2***[/SIZE]                                      
                                                                                                                                                                 [SIZE=1]
[/SIZE]                                     
                                                                                                                                                                                                                     [SIZE=1][I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name :                                                 /dev/sda2
NTFS volume version: 3.1
Cluster size :                                                 4096 bytes
Current volume size: 67018682880 bytes                                                 (67019 MB)
Current device size: 67018686464 bytes                                                 (67019 MB)
Checking for bad sectors ...
Checking                                                 filesystem consistency ...
Cluster 18284 is referenced                                                 multiple times!
Cluster 20481 is referenced multiple                                                 times!
Cluster 20482 is referenced multiple                                                 times!
Cluster 20483 is referenced multiple                                                 times!
Cluster 20249 is referenced multiple                                                 times!
Cluster 20111 is referenced multiple                                                 times!
ERROR: Filesystem check failed!
ERROR: 6                                                 clusters are referenced multiply times.
NTFS is                                                 inconsistent. Run chkdsk /f on Windows then reboot it                                                 TWICE!
The usage of the /f parameter is very                                                 IMPORTANT! No modification was
and will be made to                                                 NTFS by this software until it gets repaired.[/I][/SIZE]
                                                                                                                                                                [SIZE=1]---------------------------------------------------------------------------------------------------------------------------------------------------------------------
[/SIZE]                                     
                                     [SIZE=1]As it happens the chkdsk command doesnt work at all                                     (chkdsk/f, /r and /x). When im logged on and give the                                     command in the console I get a reply saying that the                                     selected partition cannot be locked and thus the system                                     needs to be restarted to be able to perform the command                                     prior to the next windows startup.                                      [/SIZE]
                                     [SIZE=1]
[/SIZE]                                     
                                     [SIZE=1]The key problem though is that when chdsk initiates prior                                     to startup it crashes immediatly. Default windows startup                                     and login then follow.[/SIZE]
                                     [SIZE=1]
[/SIZE]                                     
                                     [SIZE=1]The only (6) relevant protocoles I can find in Vistas                                     Event Manager  mention corrupted sectors.[/SIZE]
                                     [SIZE=1]
[/SIZE]                                     
                                     [SIZE=1]In Ubuntu I gathered this info as I thought it might help                                     you helping me                                      [/SIZE]
                                     [SIZE=1]&#8222;*hendryk@Tagwerk:~$ sudo fdisk -l &#8220; *[/SIZE]                                     
                                     -----------------------------------------------------------------------------------------------------

                                      
[SIZE=1]Drive/dev/sda: 160.0 GByte, 160041885696 Byte [/SIZE]
                                     [SIZE=1]255 Köpfe, 63 Sectors, 19457 Cylinders [/SIZE]
                                     [SIZE=1]Unit = Cylinder of 16065 × 512 = 8225280 Bytes [/SIZE]
                                     [SIZE=1]Disk identifier: 0x77777777 [/SIZE]
                                      
                                     [SIZE=1]   Device boot.         Begin               End           Block                     Id                                      System [/SIZE]
                                     [SIZE=1]/dev/sda1               1                 6519         52363836     83                                      Linux [/SIZE]
                                     [SIZE=1]/dev/sda2   *                 10515          18662         65447936    7                                            HPFS/NTFS [/SIZE]
                                     [SIZE=1]/dev/sda3              18663           19457           6385837+   5                                           Erweiterte [/SIZE]
                                     [SIZE=1]/dev/sda5                      18663           19457           6385806   82                                            Linux Swap / Solaris [/SIZE]
[SIZE=1]--------------------------------------------------------------------------------------------------------------------------------------------------------------------------[/SIZE]
                                                  [SIZE=1]
What  can I do to identify and attempt to solve the                         problem??[/SIZE]
                         [SIZE=1]
[/SIZE]                         
                         [SIZE=1]Thank yo[/SIZE][SIZE=1]u, Hendryk[/SIZE]
                         [SIZE=1]
[/SIZE]

---

### Post by byStanderone on 2009-12-22
hi...got no ntfs partition on my box right now, but am wondering if you were able to mount the ntfs partition while in ubuntu, that is before this current problem happened? cause i think ntfs can't be access while in ubuntu without added configuration to the default ubuntu setup.

---

### Post by Mark Phelps on 2009-12-22
There have been numerous posts on this forum about problems resulting from using GParted to mess with Vista partitions.  If your Vista OS is still bootable, suggest using the Vista Disk Management utility instead.  It's not great, but at least it doesn't corrupt the partition.

You might have to boot into Vista command line and run chkdsk a few times to clean up the filesystem first.

---

### Post by audiomick on 2009-12-22
+1 Mark

Übrigens, im Englischen werden Namen aufgetrennt. "grub loader", nicht "grubloader". Die Deutsche Schriebweise is verwirrend für uns Englischsprachigen...:)

---

