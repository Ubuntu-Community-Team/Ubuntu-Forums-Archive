---
title: "External HDD install has nuked my internal HDD"
date: 2011-10-21
forum: General Help
---

### Post by LurkMoar on 2011-10-21
G'day, total noob here so please forgive my unintentional ignorance.

I have installed Ubuntu 11.04 onto a 2TB USB external HDD. I created a 100GB partition in the misguided belief that I could use the internal HDD to boot Windows and plug in my USB drive when I wanted to use Linux. It seems that it has completely nuked my internal HDD. 

I can hear the the collective "You idiot" trust me. And of course while thinking that it would not touch the internal HDD I also thought a backup would be a waste of time. 

So my questions are, is there any possible way I can recover anything from the internal HDD? (missus had uni assignments on there) and where did I go wrong/what should I avoid next time?

TIA for any help

Captain Facepalm

---

### Post by Quackers on 2011-10-21
Welcome to UF :-)
What do you mean by "nuked"? What happens if you disconnect the external HDD and then try to boot from the internal?

---

### Post by LurkMoar on 2011-10-21
By nuked I mean borked and by that I mean it seems to have formatted the entire drive. If I disconnect the USB drive it just wont boot at all. I checked the drive through System Settings > Disk Utility, it just shows as unallocated space. 

Cheers for the reply

LM

---

### Post by Quackers on 2011-10-21
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by LurkMoar on 2011-10-21
Hope this is what you are after

Cheers mate


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 


```

---

### Post by Quackers on 2011-10-21
Well, it's definitely empty! Not even a bootloader. I assume that the 320GB drive is your internal hard drive?
It is not normal for this to happen. To lose the bootloader too is unusual even if the drive has been formatted!
Depending on what has happened, it may be possible to recover the lost partitions (and all or some of the data) by using testdisk - see links below.

You could also wait to see what others think too.

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by LurkMoar on 2011-10-21
Ill check that out, thanks again mate I'll let you know how I go

---

### Post by LurkMoar on 2011-10-21
Worked like a charm Quackers, still have an issue with booting Windows, but all the really important stuff has been saved. 

I could not be more thankful, I will hopefully be able to google my way to fixing the boot issue.

Cheers

LM

Boot issue solved, Vista boots off internal and Ubuntu boots from external. 
Now to learn Ubuntu

---

### Post by Quackers on 2011-10-21
That's good news, well done! :-)
I have no idea what wiped your internal drive unless you did some partitioning along the way.

If you set your bios so that the external hard drive boots before the internal hard drive Ubuntu will boot first but only when the external drive is attached. When not attached, Windows will boot.

Have fun :-)

---

