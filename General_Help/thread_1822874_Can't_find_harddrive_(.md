---
title: "Can't find harddrive :("
date: 2011-08-11
forum: General Help
---

### Post by the reaper x on 2011-08-11
Hello. This happened quite a long time ago. Let's take it from the beginning. Okay. This computer was my dad's until he got a new one and I got this. But he had some backups on one of the harddisks on the computer. The computer had two harddisks. They were both the same I think.
One  ATA WDC 320GB  mounted on /dev/sda1
And another one i can't seem to find.  The one i find now is the backup harddisk I think so the backup files is gone :(  But my dad didn't trusted me so he took backup of the backups. So thats not the problem. The problem is I have lost my 320GB extra space :(

Theory: I tried to upgrade the ubuntu 10.10 to 11.04 in the ubuntu update tool. That went wrong on the reboot. Said something about jetty error or something. So I went outside to play a little and when i came in it was still on the same screen. I force-turned it off and rebooted. Black screen, but suddenly it got purple. I thought it was okay. But then again the jetty error screen. It was the first week after 11.04 got released.
Then I got sad and just dowloaded ubuntu 11.04 from another computer onto an usb stick. And installed ubuntu by deleting all in the harddisk thingy where you choose where to put ubuntu. Now i get that by deleting all i deleted the backups and installed ubuntu. Thats okay. But where is the other harddisk now?

I was stupid again. I installed vista now about 4 weeks ago and there it was. The harddisk. It stood it was in a bad condition so i replaced the ubuntu to dual boot one the working harddisk. Now i installed ubuntu again because I released  why I deleted windows.

So once again i was alone with one harddisk and ubuntu.

Now when i open the disktool i only see one disk :(

Please someone help me try to get the harddisk back again.

Greetings Reaper-x

---

### Post by TeoBigusGeekus on 2011-08-11
Does the drive show in bios?

---

### Post by mendhak on 2011-08-11
Was it one hard disk with two partitions?

When you boot into Ubuntu, have a look at your hard disks in the Disk Management utility.  Has the entire hard disk space been given over to Ubuntu?

---

### Post by Hostie on 2011-08-11
Reaper-X

How many physical disks do you have? If more than one, then do they both show up in the bios?

now, if you have two and you did the erase all disk and install ubuntu its possible that you only wiped one disk and not both.  which leads to my next question which is what format is this "other" disk in.

If not more than one, i dont see how this would have worked at all, but if it is only one what did you use to partition the drive, and to what formats?

---

### Post by the reaper x on 2011-08-11
I have two harddisks on 320GB each. I found both of them in the bios.

[IMG]http://i621.photobucket.com/albums/tt292/kneistol/DSC00647.jpg[/IMG]

Now where can i find what type of format the harddisk i can't find is?
And how would i possibly be able to fix it if i can't see the harddisk other places then the bios...


I'm going outside now. I'l be back to answer right when i come home. Bye.

Hope you will take the time to answer me :)

---

### Post by CatKiller on 2011-08-11
> **the reaper x said:**
> It stood it was in a bad condition

Hard drives do just die. It's a wonder they work at all, frankly.

[This tool]("http://support.wdc.com/product/download.asp?groupid=606&sid=30&lang=en") might help you determine if there's anything you can do.

---

### Post by Mark Phelps on 2011-08-11
You could try opening a terminal and entering "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out all the drives and partitions.

---

### Post by the reaper x on 2011-08-11
> snowboard@****:~$ sudo fdisk -lu
[sudo] password for snowboard: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004dc1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   616753151   308375552   83  Linux
/dev/sda2       616755198   625141759     4193281    5  Extended
/dev/sda5       616755200   625141759     4193280   82  Linux swap / Solaris

Disk /dev/sdf: 8002 MB, 8002732032 bytes
97 heads, 21 sectors/track, 7673 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        3450    15617401     7806976    c  W95 FAT32 (LBA)
snowboard@****:~$ 
This is what i get. I will now look at the tool to check... Will come back and edit.


EDIT: Have now tested the software and it only finds one driver.

        Model                                              Drive port                  STATUS                            Code
WDC WD3200JS-63PDB1                          0  0x09F0             NO ERROR FOUND                   0000

Can't find the other one :(

---

