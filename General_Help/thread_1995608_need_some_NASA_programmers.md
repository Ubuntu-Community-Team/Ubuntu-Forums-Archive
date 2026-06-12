---
title: "need some NASA programmers"
date: 2012-06-03
forum: General Help
---

### Post by ddimit on 2012-06-03
hello i have tried to install ubuntu alongside windows 7
i have not succeed 
2 genius friends came to my home to install it, still fail
im sure some tough problem exist which only NASA programmers can solve it(i guess)
last 2 weeks weeks even thje  boot of ubuntu cannot succeed (reading from cd then the screen gets black nothing more)
so if you believe you shoud belong to NASA please help me
  
some clues
my mother board p67a-gd55
my graphic card nvidia gtx 550 ti
my partitions table
[IMG]http://i47.tinypic.com/dnzzaa.png[/IMG]
razer mamba mouse
razer blackwidow ultimate keyboard

---

### Post by Cheesemill on 2012-06-03
We need more information if you want us to help.

What have you downloaded to try and install Ubuntu?
How did you try and install it?
What error messages did you get?

Usually installing Ubuntu is as easy as booting from the CD and following the instructions.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by matt_symes on 2012-06-03
Hi

I don't know your graphics card but have you tried to disable kernel mode setting for the graphic card when booting the CD ?

That's the first thing i would try.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Your looking the ```
nomodeset
``` option.

If that does not work then remove quiet and splash from the command line and post back what is displayed on the screen.

Kind regards

---

### Post by wilee-nilee on 2012-06-03
Posting the windows disk manager is of no use, it does not show all the partitions at times.

Boot the ubuntu cd and take a screenshot of gparted in ubuntu, and post that.

---

### Post by ddimit on 2012-06-03
downloaded ubuntu 12.4 x64 iso burned to cd verified cd no problem
restarted and booted from cd at the very first beginning it keeps reading from cd but nothing more,then after some minutes i can hear a sound of ubuntu but all are black then nothing 
no error message nothing at all
before one month i can boot on ubuntu but i had a different problem which it did not recognize my partitions with any way
i tried to boot from cd the gparted live cd but the same problems it cannot boot it but i do not remember the error message

---

### Post by wilee-nilee on 2012-06-03
> **ddimit said:**
> downloaded ubuntu 12.4 x64 iso burned to cd verified cd no problem
restarted and booted from cd at the very first beginning it keeps reading from cd but nothing more,then after some minutes i can hear a sound of ubuntu but all are black then nothing 
no error message nothing at all
before one month i can boot on ubuntu but i had a different problem which it did not recognize my partitions with any way
i tried to boot from cd the gparted live cd but the same problems it cannot boot it but i do not remember the error message

Check the live cd boot nomodeset option.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You are going to want to know in the future your hardware set up especially the graphics card. ;)

---

### Post by ddimit on 2012-06-03
omg you are genius (at least more than my friends :p)
you solved almost 50% of my problem  about installing ubuntu
now it boots with the nomodeset option
my last problem is that ubuntu does not recognize my partitions
also gparted live cd does not recognize my partitions
im unable to make ubuntu find them
please do not tell me the typical ways for how to solve that problem as i have read a lot of articles but i couldn't make it recognize them
so please tell me some clever ways making it find them and installing it alongside windows 7
the last time i tried i had destroyed all of my data
so please help me with that and i will pray for your goodness  
thanks

---

### Post by Cheesemill on 2012-06-03
When you have booted from a Live CD open a terminal and type:
```
sudo fdisk -l
```
and post the results back here.

---

### Post by wilee-nilee on 2012-06-03
> **ddimit said:**
> omg you are genius (at least more than my friends :p)
you solved almost 50% of my problem  about installing ubuntu
now it boots with the nomodeset option
my last problem is that ubuntu does not recognize my partitions
also gparted live cd does not recognize my partitions
im unable to make ubuntu find them
please do not tell me the typical ways for how to solve that problem as i have read a lot of articles but i couldn't make it recognize them
so please tell me some clever ways making it find them and installing it alongside windows 7
the last time i tried i had destroyed all of my data
so please help me with that and i will pray for your goodness  
thanks

Hard to say could be a broken partition table, we might run the bootscript, to see if it sees the set up.

Download this link on the live cd, and extract it to the desktop and run the command.

Open the results.txt that will appear, and copy and paste all the text to a reply. While still in that reply, highlight all that text and click on the # in the reply panel to wrap the text in code tags.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```This script will give a lot of info that saves the 20 question débâcle. .)

The script will have that info as the last post as well, we posted at the same time.

---

### Post by matt_symes on 2012-06-03
Hi

Is this an msdos partition table or a GUID partition table ?

That may be the problem as to why the partition table is not being recognised - if indeed it is not.

Have you considered shrinking a Windows partition using the Windows tool in your Windows install to create some free (unallocated) space on the drive for the Ubuntu install ? That way gparted would not have to resize the partition only recognise it.

I always prefer using the Windows tool to shrink a Windows partition.

Either of the above posted command should help to diagnose the problem.

Kind regards

---

### Post by ddimit on 2012-06-03
sudo fdisk -l command```


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdfbd58cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          64      208844      104390+   7  HPFS/NTFS/exFAT
/dev/sda2          208848  2643415424  1321603288+   7  HPFS/NTFS/exFAT
/dev/sda3      2746834944  3907024895   580094976    7  HPFS/NTFS/exFAT


```txt file
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             64       208,844       208,781   7 NTFS / exFAT / HPFS
/dev/sda2             208,848 2,643,415,424 2,643,206,577   7 NTFS / exFAT / HPFS
/dev/sda3       2,746,834,944 3,907,024,895 1,160,189,952   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda121 3,981,892,031,454,927,7341,439,580,750,140,855,239-2,542,311,281,314,072,494 -
/dev/sda122 296,666,591,524,205,8021,230,764,605,742,830,493934,098,014,218,624,692 -
/dev/sda123 3,383,479,271,481,628,7911,819,617,826,892,553,345-1,563,861,444,589,075,445 -
/dev/sda124 132,479,203,320,472,9494,384,101,774,728,110,2664,251,622,571,407,637,318 -

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        366C9F7C6C9F3599                       ntfs       
/dev/sda2        386CA1966CA14F84                       ntfs       
/dev/sda3        682ED28D2ED253A2                       ntfs       back-up
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
d441a0f503000300a398cd0c7ca980e5
Unknown GPT Partiton Type
ce4d86e2dee52e155befd904f5960473
Unknown GPT Partiton Type
819e1a83531b32ea52f0a371e9b39bb3
Unknown GPT Partiton Type
a464aabfb82a9295bf35d3db878d653f


```
what i want is to appear the magic "INSTALL ALONGSIDE WINDOWS 7" button

---

### Post by wilee-nilee on 2012-06-03
This is the culprit here.

**GUID Partition Table detected, but does not seem to be used**, this is in the script

There are helpers here that will advise you, this is beyond my pay range.

You might report yourself to the mods, lol, and ask for the header to be changed from what it is to a related one to this problem. ;)

The mods wild be happy to do this for you, and it will quicken the help. The Nasa reference is well a waste of time really.

---

### Post by matt_symes on 2012-06-03
Hi

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


It looks like you have a GUID partition table and i think that is confusing the installer.

I don't have any direct experience with GUID partition tables so i'll read up for you.

Let's see what cheesemill and wilee-nilee say. They may have come across this before.

Kind regards

---

### Post by matt_symes on 2012-06-03
Hi

Well now we know what the problem is, we can (hopefully) come up with a solution.

First thing i would do is boot into windows and shrink the partition to create some unallocated space on the drive for Ubuntu.

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

How much space to you intend to allocate for Ubuntu ? How much memory does the computer have (for a swap calculation) ?

Can i also make the suggestion that you image (make a backup) of the entire drive including all partitions just in case there are problems.

You can use Clonezilla or another program for this. That is my standard disclaimer out of the way :D

Kind regards

---

### Post by ddimit on 2012-06-03
i have 8 gb ram
i know how to shrink the volume from windows 7
im going for another restart and i will shrink for 100 gb unallocated space for ubuntu
im waiting for your new directions

---

### Post by matt_symes on 2012-06-03
Hi

> im going for another restart and i will shrink for 100 gb unallocated space for ubuntu

That's a massive allocation for Ubuntu and Windows may not allow you to shrink the C: partition by that amount. It depends on where it has stored the swap and hibernation files and the shadow storage files and other files. It will also depend on the size of the hard drive.

You will not need a swap partition unless you plan to hibernate with the amount of memory you have.

I will be afk for a while.

Kind regards

---

### Post by ddimit on 2012-06-03
thanks for the info but it allowed me
i have 100 gb unallocated space 
when you will be available again please tell me the next steps

---

### Post by matt_symes on 2012-06-03
Hi

You have a couple of options here. 

1. You can try to boot the LiveCD in UEFI mode.

2. You can fix or remove the GUID partition table using a) fixpart or  b) gdisk.

Fixpart was written by forum member srs5694 and a link for it is shown below.

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Download it. Make it executable and then run

```
chmod 755 <fix_parts_filename>
```

```
sudo fixpart /dev/sda
```

If you use gdisk, it will need to installed from the liveCD. You will need to enable the universe repository.

```
sudo apt-get install gdisk
```

It is a command line tool to manipulate GUID partitions.

*****BACKUP YOUR DRIVE BEFORE ATTEMPTING THESE CHANGES*****

Kind regards

---

### Post by wilee-nilee on 2012-06-03
> **ddimit said:**
> thanks for the info but it allowed me
i have 100 gb unallocated space 
when you will be available again please tell me the next steps

What matt_symes has linked you to is what I see often, suggested.

Backup your set up first as suggested.

---

### Post by ddimit on 2012-06-04
i have installed fparts (not the latest i think)
im typing
```
sudo fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda

MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help): 

```
and i dont know what of the above to choose
also i tried to install gdisk
but the next problem appears 
[IMG]http://img840.imageshack.us/img840/4548/screenshotfrom201206041.png[/IMG]

---

### Post by 3rdalbum on 2012-06-04
I can't actually be of any help here, but I'd just like to reassure you that the problems you're facing are definitely not normal. Usually, Ubuntu goes onto a computer like warm margarine onto hot toast. That's why I know so little about problems with installing Ubuntu - I've never had problems installing Ubuntu :-)

I hope everything gets sorted out, and I'm sure once you've got Ubuntu installed things will be a lot easier. Sorry I can't be of more help at this stage though.

---

### Post by matt_symes on 2012-06-04
Hi

From ```
man fixparts
```

> It can remove stray GUID Partition Table (GPT) data, which can be left behind on a disk that was once used as a GPT disk but then incompletely  converted
              to the more common (as of 2011) MBR form.


and

 > When it first starts, fixpart performs a scan for GPT data. If the disk looks like a conventional GPT disk, fixpart refuses to run. If the disk appears to be  a
       conventional MBR disk but GPT signatures are present in the GPT primary or secondary header areas, fixpart offers to delete this extraneous data. If you tell it
       to do so, the program immediately wipes the GPT header or headers. (If only one header was found, only that one header will be erased, to minimize the  risk  of
       damaging a boot loader or other data that might have overwritten just one of the GPT headers.)

Did it not offer to delete the GPT data for you at startup ? 

BTW. You did make a backup of the partition table first as detailed in the link i gave you ?

```
sfdisk -d /dev/sda > /path/to/usb_pendrive/parts.txt
```

Are your friend there to help you at the moment as what you are doing is pretty dangeurous and with one slip you could potentially lose your windows partition.

Is the drive from an old MAC PC ?

To mirror 3rdalbums comments, your setup is non standard !

Kind regards

---

### Post by ddimit on 2012-06-04
no it did not ask me on startup to delete the GPT data 
i have made a backup with acronis and saved the backup to an external hard drive
so please feel free to tell me what i have to do
if the only solution is to format my pc there is no problem
just tell me how to format it for making ubuntu recognize windows 7(when  i format my pc i just boot from dvd delete partitions and then i make one ntfs partition and installing windows 7 on it)
i dont know if the drive is an old mac pci bought  the whole PC one year ago

---

### Post by matt_symes on 2012-06-04
Hi

First things first. The name of the program to install is gdisk and not gptfdisk. It's in the universe repository.

As fixparts did not delete the GUID partition data, I think you may have a hybrid partition table and not stray GUID entries from a previous installation. However, i am not 100% sure of this.

You certainly have both GUID and MBR tables and i believe this is, ultimately, what's fooling the partition manager on the installer.

I am a bit loathe to give any advice until i have tried to get a second opinion from others who have more experience with GUID partition tables.

This may take some time though depending upon when people who may be able to help actually come on line.

Please be patient.

Anybody else with experience of GUID partition tables then, please, offer any advice.

Kind regards

---

### Post by oldfred on 2012-06-04
If gparted is not seeing partition table and fixparts was not the issue, it could be just that the NTFS partition(s) need chkdsk or a corrupted partition table.

Even new installs of Windows may need chkdsk and chkdsk is run automatically by Windows on resize. 

Some tools seem to set partition table entries incorrectly creating overlapping or over size entries.

Post this from Ubuntu liveCD terminal:
```

sudo fdisk -lu
```

---

### Post by ddimit on 2012-06-04
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdfbd58cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          64      208844      104390+   7  HPFS/NTFS/exFAT
/dev/sda2          208848  2438615424  1219203288+   7  HPFS/NTFS/exFAT
/dev/sda3      2746834944  3907024895   580094976    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 
```

---

### Post by matt_symes on 2012-06-04
Hi

> **ddimit said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdfbd58cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          64      208844      104390+   7  HPFS/NTFS/exFAT
/dev/sda2          208848  2438615424  1219203288+   7  HPFS/NTFS/exFAT
/dev/sda3      2746834944  3907024895   580094976    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 
```

> ```
**WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.**


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
<snip>
```

Maybe fixparts did do something as i can see no reference to the GUID partition table you had earlier. Maybe chkdsk fixed it. Did you run that ?

If you run the installer now, does it see the partitions ?

Kind regards

---

### Post by ddimit on 2012-06-04
hello i have successful installed ubuntu alongside windows 7
thanks all of you for your great help 
and i hope you will  have a nice summer

---

### Post by matt_symes on 2012-06-04
Hi

I'm glad it's fixed.

> **ddimit said:**
> hello i have successful installed ubuntu alongside windows 7
thanks all of you for your great help 
and i hope you will  have a nice summer

Did you run chkdsk as oldfred suggested on the drive ?

Kind regards

---

### Post by ddimit on 2012-06-04
no.. im sorry for telling that but the problem i think it was that i had a solid state hard driver plugged in on my motherboard but not all the cables connected.. then i told to my self what would happen if i completly unplug  all the solidsate  cables from my motherboard i did that and magically ubuntu found the windows 7
but im not sure if that was the problem i had followed your good directions maybe both of them worked

---

