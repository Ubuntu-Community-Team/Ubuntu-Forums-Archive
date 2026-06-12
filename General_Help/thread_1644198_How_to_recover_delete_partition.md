---
title: "How to recover delete partition"
date: 2010-12-12
forum: General Help
---

### Post by mthalis on 2010-12-12
My computer have Ubuntu 10.10 and windows Xp. I try to format my windows partition in that case I deleted my Ubuntu swap area. After that without installing Xp I boot up my machine using Ubuntu 10.10 live CD and try to access my Ubuntu partition but now it was disappear so how can I recover my Ubuntu partition, now my complete hard disk show as unallocated disk. please help me to restore my partition.

Thank You.

---

### Post by karmila on 2010-12-12
I don't really have experience on this but I read somewhere if [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") has that ability.

---

### Post by mthalis on 2010-12-13
I run my machine using Live CD, so can I use that software in Live CD mode ?

---

### Post by oldfred on 2010-12-13
It is not installed on the liveCD but you can download it.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Rasa1111 on 2010-12-13
darn.

 Doesnt sound too promising. 

I don't know as much about all of this as a lot of people here~
So I could be very wrong...
But I cannot foresee you getting your partition back.
Hope im wrong.

---

### Post by mthalis on 2010-12-13
I have little problems,
1) If I delete my swap area. Can't I access my ext4 file system using Live CD. 
2) If I create new swap area can I boot my machine using that ext4 file system.

---

### Post by oldfred on 2010-12-13
I do not understand your concern about swap. It usually is a small partition that you use just when RAM is full.


You system should even boot without swap. If you have and  incorrect one set up it should still boot after several error messages.

So we can see what is where, from liveCD:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by mthalis on 2010-12-13
Below show my **sudo bash boot_info_script055.sh** output.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)



```


I installed testdisk using live CD mode, Seems to be it can recover my NTFS partitions but if I try to list file in Linux partition it gave this error **No file found, filesystem seems damaged.** Is their any way to recover that partition also.

Thank you.

---

### Post by oldfred on 2010-12-13
There are some paid programs but most are for NTFS partition. If you really want to recover valuable data, then you have to send the drive to service and that can be very expensive.

Testdisk also has photorec which recovers most files from any partition. It does not recover names and also recovers file segments. I had saved a text file many times and it recovered parts of it into many files. Never did find original but from all the parts got most of it back. You have to copy to another drive.
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
Photos and music have internal data that will let you rebuild a file name.
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by mthalis on 2010-12-17
I solved my problem using testdisk. :)

Thank You.

---

