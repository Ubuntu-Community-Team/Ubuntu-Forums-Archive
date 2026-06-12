---
title: "I broke grub?"
date: 2011-04-04
forum: General Help
---

### Post by Bluestars on 2011-04-04
Hi, 
 I was originally dual booting between win 7 and 10.04.   I didnt have a blank dvd so i tried to upgrade within ubuntu.   It didnt work so on windows i formated that linux partiton to fat32,  and then used the windows installer to install it from within in windows. 

Now when i boot up it says error:unrecognized file system grub rescue.  

How i fix?   Thanks.

---

### Post by oldfred on 2011-04-04
Did you do a full install or a wubi install?

You need a liveCD, liveUSB or a working Ubuntu to run this, otherwise we are just guessing:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Kirboosy on 2011-04-04
When you wacked Ubuntu off and changed the partition you didn't notify GRUB of the changes. Grub is still looking for the old setup (which doesn't exist)

You need to remove GRUB, this can be done by repairing your Windows 7 MBR. Here is a [guide]("http://www.ehow.com/how_4836283_repair-mbr-windows.html") to repairing your Windows 7. :)

Anymore questions feel free to ask..

~Caboose

---

### Post by Bluestars on 2011-04-04
I did a wubi install.  

[Caboose885]("http://ubuntuforums.org/member.php?u=900617") I ran bootsect /nt60 SYS and it said it updated for C  but when I reboot I get the same grub rescue error.

---

### Post by Bluestars on 2011-04-04
Also I tried this guide [http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)  but when I go into Live and try to run "sudo grub"  it says "grub:command not found"

---

### Post by coffeecat on 2011-04-04
@Bluestars, did you read this?

> **oldfred said:**
> You need a liveCD, liveUSB or a working Ubuntu to run this, **otherwise we are just guessing:**

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

"Otherwise we are just guessing." I agree with oldfred. You need to run the boot info script.

---

### Post by bcbc on 2011-04-04
> **Bluestars said:**
> I did a wubi install.  

[Caboose885]("http://ubuntuforums.org/member.php?u=900617") I ran bootsect /nt60 SYS and it said it updated for C  but when I reboot I get the same grub rescue error.
The command to repair the MBR is: bootsect /fixmbr

---

### Post by Bluestars on 2011-04-04
I tried bootsect /fixmbr but it didnt recognize the command.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 125. But according to the info from fdisk, 
                       sda5 starts at sector 1065511251.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/home.disk 
                       /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9434cb15

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,065,511,124 1,065,511,062   7 HPFS/NTFS
/dev/sda2       1,065,511,126 1,953,520,064   888,008,939   f W95 Ext d (LBA)
/dev/sda5       1,065,511,251 1,871,427,914   805,916,664   b W95 FAT32
/dev/sda6       1,871,427,978 1,905,501,779    34,073,802  82 Linux swap / Solaris
/dev/sda7       1,905,501,843 1,953,520,064    48,018,222  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        05BEB22D0F7B5B73                       ntfs                                     
/dev/sda5        0DE9-2959                              vfat                                     
/dev/sda6        dfceb513-b5b8-4eea-8a36-9c603e4b5f3e   swap                                     
/dev/sda7        419607ce-a945-4eb8-95da-9aab812f13d4   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


```

---

### Post by bcbc on 2011-04-04
> **Bluestars said:**
> I tried bootsect /fixmbr but it didnt recognize the command.



sorry my bad, it's "bootrec.exe /fixmbr"

PS you're installing wubi on a fat32 partition which has a limit of 4GB max/file (which is why you have a separate root.disk and home.disk). It doesn't look like an issue because you're not trying to install at the max size, but if you did want to increase the space there is that limit.

You could use ntfs instead.

---

### Post by Bluestars on 2011-04-04
> **bcbc said:**
> sorry my bad, it's "bootrec.exe /fixmbr"

PS you're installing wubi on a fat32 partition which has a limit of 4GB max/file (which is why you have a separate root.disk and home.disk). It doesn't look like an issue because you're not trying to install at the max size, but if you did want to increase the space there is that limit.

You could use ntfs instead.

Sweet!  bootrec.exe /fixmbr worked.  I'm gonna need to increase the size of that partition though.  What would be the easiest way to do that?  I don't want to run into the same problem again.

Thanks!

---

### Post by bcbc on 2011-04-04
> **Bluestars said:**
> Sweet!  bootrec.exe /fixmbr worked.  I'm gonna need to increase the size of that partition though.  What would be the easiest way to do that?  I don't want to run into the same problem again.

Thanks!
I don't think you have a problem with the partition size - it's 400GB or so (or am I reading that wrong, because it looks like you also have 2 swap partitions totalling 40GB).

But I'm not certain that Wubi is the right choice for you. It doesn't install Ubuntu directly to a partition but instead installs to virtual disk(s) which are just files stored on the host partition. It is limited to 30GB (on ntfs) and about 12GB on Fat32. 

If you want a full install of Maverick on /dev/sda5 you'd do best to do a regular install. At that time you can rejig the partitions and get rid of all that swap.

---

### Post by oldfred on 2011-04-04
Some info if you want a full install:

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Note that the instructions on the install and not clear on the use entire disk and use entire partition which both erase drive. Best to use manual install.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

