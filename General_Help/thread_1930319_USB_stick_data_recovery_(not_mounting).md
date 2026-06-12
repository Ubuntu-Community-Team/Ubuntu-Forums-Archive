---
title: "USB stick data recovery (not mounting?)"
date: 2012-02-23
forum: General Help
---

### Post by MsKK on 2012-02-23
Hello dear Ubuntuers:

A friend of mine had some data in a USB stick she wants to recover (no backup... I know). I plugged it in on my computer and it is recognized by Gnome (says "Silicon Motion,Inc. USB MEMORY BAR") but it displays a winking red light.

So far I've tried the following. I looked at the log messages and it says this:

```
me@whatever:~$ dmesg | tail

[15003.072631] usb 1-1: new high speed USB device using ehci_hcd and address 16
[15004.005412] usb 1-1: configuration #1 chosen from 1 choice
[15004.006238] scsi16 : SCSI emulation for USB Mass Storage devices
[15004.007114] usb-storage: device found at 16
[15004.007123] usb-storage: waiting for device to settle before scanning
[15009.004551] usb-storage: device scan complete
[15009.005672] scsi 16:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
[15009.008150] sd 16:0:0:0: Attached scsi generic sg2 type 0
[15009.027615] sd 16:0:0:0: [sdc] Attached SCSI removable disk

```

So at least it does something when I plug it in. However, it seems that it is not mounted because when I do an fdisk, I get:

```

me@whatever:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13caef07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30040   241296268+  83  Linux
/dev/sda2           30041       30401     2899732+   5  Extended
/dev/sda5           30041       30401     2899701   82  Linux swap / Solaris

```

I also tried dd and ddrescue to no avail:

```

me@whatever:~$ sudo dd if=/dev/sdc of=/tmp/r1
dd: opening `/dev/sdc': No medium found


me@whatever:~$ sudo ddrescue -r 3 /dev/sdc /media/external/image /media/external/logfile
ddrescue: cannot open input file: No medium found
```

I also looked at this website [Ubuntu Documentation > Community Documentation > DataRecovery]("https://help.ubuntu.com/community/DataRecovery") but I think my problem is more basic than that. (Mounting the USB first). If I could only find a way to mount it or make it recognizable for any program, maybe I could get an image and work from there. 

I am out of ideas :confused: . Anyone has ever experienced something similar or has any suggestions? Thank you in advance!! :D

BTW I am using Ubuntu 10.04

---

### Post by dragonfly41 on 2012-02-23
You could try installing [COLOR=DarkRed]**usbmount**[/COLOR] .. works for my USB devices

---

### Post by winh8r on 2012-02-23
open a terminal and enter:

```
sudo apt-get install testdisk 
```

plug in the external drive and run testdisk by entering in the terminal:

```
sudo testdisk
```

it should detect the drive and allow you to navigate through it and recover files.

The second part of the testdisk utility is photorec which will also allow recovery of a wide range of filetypes from damaged/deleted filesystems.

You can read more about them at:

[http://www.cgsecurity.org/wiki/Main_Page]("http://www.cgsecurity.org/wiki/Main_Page")

---

### Post by MsKK on 2012-02-24
Unfortunately usbmount didn't do anything and I tried testdisk but it didn't even see the USB drive (see picture). 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213189&stc=1&d=1330094371[/IMG]

Any other ideas? :(

Ah! I also tried gparted but it didn't see the USB stick either

---

### Post by spegru on 2012-02-25
Data recovery is more important than linux principles so I suggest you try another pc or 3. If none of them work it sounds hopeless though

---

### Post by sudodus on 2012-02-25
If the file allocation table is destroyed, but the file data is still there, you can use ***PhotoRec*** to recover the data. Your computer can at least see, that there is a device [sdc]. Let us hope that PhotoRec can use that information (although obviously dd could not do it). Maybe booting some other OS from a live CD or USB drive, would see it, for example a live ***SystemRescueCD***, or ***Knoppix*** drive.

---

### Post by royb1972 on 2012-02-25
try to install foremost

sudo apt-get install foremost

after go-

cd /dev
ls

see what sd? your usb is

create a folder in your computer, for example-
mkdir home/user/directory

than run the command

sudo foremost -t all -i /dev/sd* - your usb sd number

---

### Post by MsKK on 2012-02-27
**spegru**: I already tried several other PC's with no success. 

**royb1972**: I already tried foremost but when I do as recommended, the terminal hangs with a message that says "Processing: stdin"

**sudodus**: Photorec doesn't even notice there is a USB device connected. I'll try booting from another OS but I must admit I don't have much faith in this. 

Anyways, thanks everyone for your advice and if you have any other ideas, please let me know. I am not giving up on this thing!!! ](*,)

---

### Post by sudodus on 2012-02-27
I am thinking of a way to make the USB drive visible, so that sudo fdisk -lu and photorec could see that there is a partition. So if you ***edit only the partition table*** the data on the rest of the drive should remain untouched.

Try first with ***gparted***! Delete all partitions and then make one primary partition. No more, exit!

If that does not work, try with ***fdisk***, but if it cannot see the drive, maybe it is broken electronically, and very hard to recover. Read the manual page ```
man fdisk
``` before using it! To edit (not only listing), fdisk runs interactively with a simple text interface. I have used it, and know that it works.
--
Then if a partition is created, run ***photorec*** again!
--
There might be some advanced commercial recovery software (for a modest price), or some specialized company (for a very high price) that can recover the data, if really necessary.

---

### Post by MsKK on 2012-02-27
How can I delete the partitions with gparted if it doesn't even see the device? I'm sorry, my knowledge of linux is only user-level. Could you tell me the commands?

---

### Post by sudodus on 2012-02-27
> **MsKK said:**
> How can I delete the partitions with gparted if it doesn't even see the device? I'm sorry, my knowledge of linux is only user-level. Could you tell me the commands?
Sorry, I forgot and did not check at the beginning of the thread. I thought for a moment that you could see the drive but not the partitions, but it is only dmesg that can see [sdc].

Maybe you can find something useful on the internet, for example
browsing for ***recover usb drive*** which finds this software for $45
[[COLOR="Red"]_http://www.usbdriverecovery.com/_[/COLOR]]("http://www.usbdriverecovery.com/")
and these software versions for $45-80
[[COLOR="red"]_http://www.usbdrivedatarecovery.com/_[/COLOR]]("http://www.usbdrivedatarecovery.com/")

There are free demo versions that show what can be recovered, but there is no recovery done until you $pay.

And you can probably find much more useful. Of course, most of it is for Windows, but the file system of USB sticks is usually a windows system anyway.

---

### Post by dragonfly41 on 2012-02-27
Back to basics .. 


[LIST]
[*]Does your USB port work with other USB devices?
[/LIST]

[LIST]
[*]Have you tried other USB ports?
[/LIST]

[LIST]
[*]Can the USB device be seen by another PC?
[/LIST]

[LIST]
[*]Have you google searched this string (in your first post) ..
[/LIST]
> usb 1-1: new high speed USB device using ehci_hcd and address 16

---

### Post by MsKK on 2012-02-28
> 
[LIST]
[*]Does your USB port work with other USB devices?
[/LIST]


yes

> 
[LIST]
[*]Have you tried other USB ports?
[/LIST]


yes. The same thing happens. It is not a problem from my computer but from the USB stick. 

> 
[LIST]
[*]Can the USB device be seen by another PC?
[/LIST]


I used another computer with Windows. The red light of doom turned on but the device was not recognized nor visible. 

> 
[LIST]
[*]Have you google searched this string (in your first post) ..
[/LIST]


yes, but couldn't find anything helpful. Maybe I don't know how to search properly and I thought people here could have a better insight as what to do. Thanks for your help, though. I'm thinking about the "hardware" solution (take everything apart) if nothing else works.

---

### Post by dragonfly41 on 2012-02-28
I'm wondering if you friend just yanked out the USB stick from her computer instead of using the "safely remove" option to unmount first.  

There may be a lock flag on the device.  Just a theory.

This thread gives one simple solution to "device not recognized" but it doesn't explain why the USB device fails on multiple computers.

[http://answers.microsoft.com/en-us/windows/forum/windows_vista-hardware/usb-device-not-recognized-error-keeps-popping-up/6be4581d-8fbd-407f-815e-b475c35ca586?page=1](http://answers.microsoft.com/en-us/windows/forum/windows_vista-hardware/usb-device-not-recognized-error-keeps-popping-up/6be4581d-8fbd-407f-815e-b475c35ca586?page=1)


[EDIT[ since that link above is Windows related .. here is a ubuntu suggestion ..

[http://askubuntu.com/questions/9923/usb-flash-drive-not-recognized](http://askubuntu.com/questions/9923/usb-flash-drive-not-recognized)

Note:  this suggestion downgrades USB performance _so do some research_ first to see if this approach is relevant.

---

