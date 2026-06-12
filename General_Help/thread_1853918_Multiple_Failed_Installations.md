---
title: "Multiple Failed Installations"
date: 2011-10-03
forum: General Help
---

### Post by Automatiic on 2011-10-03
Hello, Ubuntu!
As you can see, this is my first post because this is also my first few days working with Ubuntu. How about some background followed by what's been happening? Basically, I am the new and only IT Administrator for the company I work for. All of their licensing will expire soon for their Windows XP machines, Server 2003 R2 and their Antivirus software. They need to upgrade because Microsoft will be discontinuing support for WinXP soon so it would be best to move to Server 2008 R2 and Windows 7. The computers, however, will not support Windows 7. So, I had the bright idea to migrate the entire business to Ubuntu Server and Ubuntu Desktop. 

I took a spare gaming machine I had at home (to be a dummy server) and some extra unused client PC's at the office and setup a dummy network through a switch and a KVM. I wanted to test everything before I deployed it on our active IT Infrastructure. I downloaded Ubuntu 11.04 Server and Ubuntu 11.04 Desktop. I tried to install Ubuntu Server on the "Server" and halfway through installation, it says "Please insert the disc labeled: 'Ubuntu-Server 11.03 _Natty Narwhal_ - Release AMD64 (20110426". The problem with that, however, is I only have one disc. This happens repeatedly. I thought it could be an issue with the partitioning so I formatted the drives and partitioned them myself using Acronis (yes I used to the proper formats). Needless to say, I do not have Ubuntu Server running. 

Now for the clients. It says that the installations has finished and then when it restarts, the machines boot to a grub rescue> prompt. What is the issue? I could see the installation failing on one machine for some crazy issue but I have tried installing this on 6 PC's now and they have all failed with one issue or another (some of them I didn't write down so I don't remember what they were). Everyone says Ubuntu is fantastic, stable and reliable and I want to believe that. But not even being able to simply install the OS makes me second-guess my decision to move everything to it. I would love to get this working and become a Ubuntu fan. Please help!

---

### Post by Quackers on 2011-10-03
Did you leave the default setting for grub when installing on the clients or did you change where it was to install?
Are you using a separate boot partition on those pc's?
Are the hard drives completely empty?

In respect of the clients please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Automatiic on 2011-10-03
Thank you for the reply!

No I let it install to the default locations on the clients and on the server. I booted to Acronis and wiped all partitions off of all of the drives on each computer before trying to install the second time so yes they were bare drives. The only thing I can think of is that the server is setup as a RAID 5. Would that make any difference?

I will do what you said in a bit after I finish fixing some issues that some users are having in the office. I will post that log as soon as I get the chance. Thanks again!

---

### Post by oldfred on 2011-10-03
Is your server perhaps have an NEC DVD drive?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/682159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/682159)
Fixed in 11.10 Alpha.

---

### Post by Automatiic on 2011-10-03
Here is the Results.txt file you requested! 


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of 
    /dev/mapper/isw_dijcbjdbaf_Volume0 and looks at sector 1 of the same hard 
    drive for core.img. core.img is at this location and looks in partition 1 
    for /boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

isw_dijcbjdbaf_Volume01: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   625,151,999   625,149,952   7 NTFS / exFAT / HPFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: isw_dijcbjdbaf_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_dijcbjdbaf_Volume0: 320.1 GB, 320079134720 bytes
255 heads, 63 sectors/track, 38914 cylinders, total 625154560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_dijcbjdbaf_Volume01   *          2,048   625,151,999   625,149,952   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dijcbjdbaf_Volume0
isw_dijcbjdbaf_Volume0p1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on isw_dijcbjdbaf_Volume01



========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/mapper/isw_dijcbjdbaf_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dijcbjdbaf_Volume01: No such file or directory

```

---

### Post by Automatiic on 2011-10-03
As far as whether or not the drives are NEC drives, I'm not sure. GIve me a few and I'll take it apart to find out. There's no "NEC" label on the trays. Just your standard DVD-RW blah blah blah

Thank you guys again for all of your support. Ubuntu team rocks!

---

### Post by Automatiic on 2011-10-03
Just checked. Yes... they are NEC drives. Why do I feel like that is a very bad thing...? haha

---

### Post by oldfred on 2011-10-03
Your results.txt shows RAID. Not sure if they now include the drivers for that or not now with the Desktop install. Normally better to use server or the alternate (text based) installer which are not liveCDs.

Do you want to keep the RAID as it is this:
Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)

Script may show RAID with the install of additional drivers, not sure about "fakeraid".
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

---

### Post by Automatiic on 2011-10-03
The results file above is from my Laptop that I am trying to install it on as well. It has a RAID, yes. But the Server I'm using is in a RAID 5 as well and I used the server version on it and I was getting the error message reported in my first post. So using the server version on a machine with a RAID setup didn't work either. And why did you want to know whether or not my optical drives were NEC. They are NEC so... is that bad?

---

### Post by oldfred on 2011-10-03
In post #4 I had a link to the bug report on NEC drives.

Do you want the nVidia RAID on the desktops? That is unusual, but a few use it on desktops. I do not know RAID well enough to offer much advice (other than how to remove it if you want). Some have said Linux's RAID is better but I do not know if that is just us.

---

### Post by Automatiic on 2011-10-03
Ahh ok I see that now. I overlooked it. Sorry about that

And no the only machines I have a RAID on are my dummy server (RAID 5) and my Gaming Laptop (Striped RAID). It's good for a server to have a RAID but I don't see why the installation would be asking for another disc when there isn't one just because I have a RAID setup. 

As for the Desktop version, I am installing it now on a machine that does NOT have a RAID. We'll have to see if that fixes the issue or not

---

### Post by oldfred on 2011-10-03
If in BIOS you have ever turned on a RAID setting or if the drive was in a RAID set, the drive retains RAID internal settings that can cause issues.

If you are sure you do not want RAID as this will damage RAID configuration.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by Automatiic on 2011-10-03
Let me throw another wrench into this whole fiasco. I would disassemble the RAID and try it without one on the server I dont think it would fix anything and this is why...

On the Server, I have 4 250GB SATA HDD's. 1 of them is all by itself. The other 3 are in the RAID 5. I initially tried installing the server version to the RAID and it failed. The second time, I disregarded the RAID and attempted to install it to the single drive that is NOT in the RAID and I got the same message. :(

---

### Post by oldfred on 2011-10-03
On the server it is probably the NEC issue. Is server new enough to boot from USB flash drive? 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I changed to only use flash drives as they are reusable and on my larger flash drives I have a way to install multiple ISOs and boot, so I have several installs & repairs disks on one flash drive.

---

