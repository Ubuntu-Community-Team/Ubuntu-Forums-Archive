---
title: "New Ubuntu User looking for help"
date: 2012-01-30
forum: General Help
---

### Post by Joshhua5 on 2012-01-30
I've just came from my entire life using Windows (Currently 17)
Due to windows giving me some rather... Troubling issued, I'm not going to point fingers (Windows 8 ) then rolling back was basically impossible with all sorts of hard drive problems. So I packed up and left for my Ubuntu 11.10 USB usb drive, which ultimately saved my leg.Let me list my specifications first, it may help.

AMD FX-8150
Gigabyte 990FXA-UD7
Corsair Vengeance 16GB(4x4) 1600Mhz
AMD Radeon 6970 (Gigabyte)
ASUS Xonar DX
Razor Mechanical Ultimate
Toughpower XT 875W
ASUS DRW-24B3ST
2x 500GB HDDS
1x 1TB WD Black
Coolermaster Sentinel Advance Gaming mouse
2x 23" LED 
1x 23" Polarized 3D LED

Firstly, Anyway (Well I know there are, since I've done it with windows) to recover the data from my unmountable harddrive, it went though a quick format from ntfs to ntfs. Apart from the WD, this has all my games(from steam) and quite a few things I wish to keep.

Secondly, my graphics drivers downloads as a .run and opens with gedit, How can I install my driver? (amd-driver-installer-12-1-x86.x86.run) On my screens I'm limited to a mirror display with 1920x1080, that will go away with the driver install right?

I'm using the 32bit version for Internet usage reasons for now. The entire 16GB of my ram is still usable? as it detects all of it. Slightly confused here since for Windows 32bit has a max of 4GB.

Thirdly, My DVD Drive doesn't seem to be working, it has power and it's door opening capabilities, but nothing that the computer detects such as it's presence.

Fourthly, My HDD's aren't being detected at least one of the 500GB is the rest aren't (the one being detected has Ubuntu on it) the other 500GB is being detected but it fails to mount. WD Black is apparently non existent. 

Any highly recommended software to use? or good go-to sites for problems I have?

---

### Post by Frogs Hair on 2012-01-30
2. Check Additional Drivers and install the recommended if available and needed .
3 . To find out if  32 or 64 bit is installed use the following command or open System Info and look under OS Type .```
uname -a
```

---

### Post by Joshhua5 on 2012-01-30
Under additional drivers, there's a Beta one and a normal, the normal one is installed or... Active as it says, still causes the problem. I wanted to use the one from AMD's website. but it comes at .run

---

### Post by xyzzyman on 2012-01-30
It installed the PAE kernel. Processes are still limited to 3GB of RAM each but it lets the 32bit OS but together they can use the 16GB's. (For future reference flash runs fine on 64bit Ubuntu, if that's why you went 32bit.)

As far as data recovery, you may want to read this [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/). It has a good walk through with screenshots. It's not going to retrieve filenames, etc, so steam games may have to be redownloaded from your steam account.

---

### Post by Joshhua5 on 2012-01-30
Under additional drivers, there's a Beta one and a normal, the normal one is installed or... Active as it says, still causes the problem. I wanted to use the one from AMD's website. but it comes at .run

---

### Post by grahammechanical on 2012-01-30
Please check this link for information about Ubuntu accessing more than 3GB RAM:

[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

Note this comment:

> Both the CD and DVD installer of Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD.

That should also be true of 11.10. It could explain why the 32bit Ubuntu is recognising all your RAM.

As regards your hard disks you can run Disk Utility. How many hard disks does that show in the left panel?

Also the File Manager will show your hard disks as devices. It also shows hard disk partitions as devices. It does not label hard disks drive C:, drive D:, and so one. That is how Microsoft labels hard disks. In Linux different labels are used.

When you click on a device in File Manager it changes the right panel in the same way as it does when you click on a folder. Clicking on a device mounts it. In other words hard disk are treated as folders by File Manager.

I am trying to find out how much you know about the way Linux/Ubuntu works and to see if the issues are due to not understanding the differences between the Microsoft way and the Linux way.

What error message do you get when you use File Manager to access these hard disks?

Regards.

---

### Post by Joshhua5 on 2012-01-30
> **grahammechanical said:**
> 
As regards your hard disks you can run Disk Utility. How many hard disks does that show in the left panel?

Also the File Manager will show your hard disks as devices. It also shows hard disk partitions as devices. It does not label hard disks drive C:, drive D:, and so one. That is how Microsoft labels hard disks. In Linux different labels are used.

When you click on a device in File Manager it changes the right panel in the same way as it does when you click on a folder. Clicking on a device mounts it. In other words hard disk are treated as folders by File Manager.

I am trying to find out how much you know about the way Linux/Ubuntu works and to see if the issues are due to not understanding the differences between the Microsoft way and the Linux way.

What error message do you get when you use File Manager to access these hard disks?

Regards.

I see two drives, the error I get when trying to mount the unmountable one is


Error mounting: mount exited with exit code 12: Failed to read last sector (1953517567): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb3': Invalid argument
The device '/dev/sdb3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Sounds like it needs to be formatted but then, it only makes recovering the data harder.

---

### Post by Frogs Hair on 2012-01-30
> **Joshhua5 said:**
> Under additional drivers, there's a Beta one and a normal, the normal one is installed or... Active as it says, still causes the problem. I wanted to use the one from AMD's website. but it comes at .run

See the page , but I would stick with one in additional drivers possible . Make sure any instructions you find are specific to the graphics driver and version of Ubuntu in use .   [http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric](http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric)

---

### Post by Joshhua5 on 2012-01-30
I'm currently scanning with Testdisk

but how about security, I used to have Trend Micro titanium, but since that's only windows. What alternatives are there?

---

### Post by Joshhua5 on 2012-01-31
big bump,


How can I fix a broken sector on a HDD

---

