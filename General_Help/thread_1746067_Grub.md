---
title: "Grub"
date: 2011-05-01
forum: General Help
---

### Post by slinzex on 2011-05-01
Hi, 

Since a lot of time I have problems with grub and splash screen on my linux. 
**Problem: **
launch sequence: 
1-DELL initial screen "press F2 for BIOS..."
2-GRUB (menu with options for OS to select)
3-Black screen with : "Starting ... "
4-In few seconds I see my desktop. No login no splash screen.

**Questions:**
1-How to make spash screen in the 3rd step? Ubuntu LOADING or something
Maybe I have bad options on my menu.lst? 
2-How to set background image for grub in step 2 ?
3-What is and where to read about options : ro quiet splash single , from menu.lst? 
4-What is best, grub 0.97 or grub 2 ? Easier?


**Details:**
Dell Vostro 1720
Ubuntu 10.10 
Windows 7
grub 0.97

---------- sudo fdisk -l  -------------------------
                                                                                                                                                         
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3702    29632512    7  HPFS/NTFS
/dev/sda3            3703       33421   238713477    7  HPFS/NTFS
/dev/sda4           33421       38914    44119041    5  Extended
/dev/sda5           33421       38671    42167296   83  Linux
/dev/sda6           38671       38914     1950720   82  Linux swap / Solaris

-------------------------
[menu.lst]("http://pastie.org/private/oyazmmacqaizcvflohgjg")
---------------------------------------
ls /boot/                                                                                                                                                                &#9472;&#9496;
abi-2.6.31-14-generic     
config-2.6.32-31-generic      
initrd.img-2.6.32-31-generic  
System.map-2.6.31-14-generic  
vmcoreinfo-2.6.32-31-generic  
vmlinuz-2.6.35-28-generic
abi-2.6.32-31-generic    
config-2.6.35-28-generic      
initrd.img-2.6.35-28-generic  
System.map-2.6.32-31-generic  
vmcoreinfo-2.6.35-28-generic
abi-2.6.35-28-generic     
grub                          
memtest86+.bin                
System.map-2.6.35-28-generic  
vmlinuz-2.6.31-14-generic
config-2.6.31-14-generic  
initrd.img-2.6.31-14-generic 
memtest86+_multiboot.bin     
vmcoreinfo-2.6.31-14-generic  
vmlinuz-2.6.32-31-generic
---------------------------------------




Thanks a lot!

---

### Post by zvacet on 2011-05-01
If I understand you correctly you can boot in Ubuntu but you don´t see login screen.That can be becsuse you put it to autologin.Check under system>admin>login window and if it select to autologin change that and on boot you will see login screen.

---

### Post by slinzex on 2011-05-01
> **zvacet said:**
> If I understand you correctly you can boot in Ubuntu but you don´t see login screen.That can be becsuse you put it to autologin.Check under system>admin>login window and if it select to autologin change that and on boot you will see login screen.

That's basic. I knew it. Not the my problem

---

