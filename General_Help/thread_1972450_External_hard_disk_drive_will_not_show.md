---
title: "External hard disk drive will not show"
date: 2012-05-03
forum: General Help
---

### Post by leopoldbirkholm on 2012-05-03
Hello,

I have an problem with mounting external hard disk drives on my Ubuntu computer. Let me start with some basic info about my computer.

Manufacturer: MSI
Model: X370
CPU/APU: AMD E-350 Dual Core
Ubuntu 12.04 Precise Pangolin with the latest updates.

Search-word on Google and on Ubuntu forums "External drive won't mount", "drive not found" and an combination of these.

I found that I can list the drives that system sees.
```

sudo fdisk-l

```

The result of fdisk is
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000070ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   969471999   484734976   83  Linux
/dev/sda2       969474046   976771071     3648513    5  Extended
/dev/sda5       969474048   976771071     3648512   82  Linux swap / Solaris


```

No sdb drive is found. I have tried with three different drives, all modern. I can't figure out what I am doing wrong. :confused:

Thank you for taking the time to read my post. I appreciate it.

---

### Post by zero2xiii on 2012-05-03
Hay,
I dont follow, can you not mount ANY usb harddrive? Or only this one?

Please post the output of:

```
lsusb
```
No sudo needed but can be added for safe measures. This will show us if the USB device is picked up or not. From there we can trouble shoot the mounting part.

Cherz

---

### Post by leopoldbirkholm on 2012-05-04
> **zero2xiii said:**
> Hay,
I dont follow, can you not mount ANY usb harddrive? Or only this one?

Please post the output of:

```
lsusb
```
No sudo needed but can be added for safe measures. This will show us if the USB device is picked up or not. From there we can trouble shoot the mounting part.

Cherz

Hello zero2xiii and thank you for replaying.

I am sorry that I was not clear. I cannot mount any USB and make them stay mounted.

This morning I re-tried with my WD external. I hooked it in and typed your command. The output was then this:
```

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 1058:1010 Western Digital Technologies, Inc. 

```

I thought. Wow, does it work now? So I went to Nautilus and looked for the folder. No-where to be found. Retype
```

lsusb

```
Remember, the WD external drive is still connected. Now the output is:
```

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Perhaps it is something wrong with WD? Trying an other WD home-made Blue series 320 GB external drive. Same code, lsusb. The output is now:
```

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

No change. I can see the LED light and feel the hard drive spinn but no mount.

---

### Post by leopoldbirkholm on 2012-05-04
The three USB-drives I have trying to work with my Ubuntu machine is:
[LIST=1]
[*]Buffalo MiniStation 465 GB drive
[*]Western Digital 465 GB drive
[*]Western Digital Blue series 320 GB homemade
[/LIST]

With homemade I mean I took the hard drive from an non-working computer and put it into an enclosure.

---

### Post by zero2xiii on 2012-05-04
Hay,

Wow that is strange. It is picked up, then discarded. I wonder why.

Let me see now. Lets try this:

```
sudo dmesg -c
```
This clears the log, after being displayed to screen. Now plug in your drive, wait a few moments and then:

```
sudo dmesg
```

And post me the output please. And remove your drive from the usb port.

I am going to assume that it is an error regarding "ehci_hcd".

After you have done the above, we are going to disable ehci_hcd:

```
cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'
```
I found the above from [here]("http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/")
It is just so much easier than explaining the entire process by hand.

After you have done this, plug the device back in. Again do:

```
sudo dmesg -c
sudo dmesg
```

and post the new output. This should tell us what is happening from the system side of things. Please only do this with ONE drive. One that you know works if at all possible.

Cherz

---

### Post by leopoldbirkholm on 2012-05-04
> **zero2xiii said:**
> Hay,

Wow that is strange. It is picked up, then discarded. I wonder why.

Let me see now. Lets try this:

```
sudo dmesg -c
```
This clears the log, after being displayed to screen. Now plug in your drive, wait a few moments and then:

```
sudo dmesg
```

And post me the output please. And remove your drive from the usb port.

Cherz

The output of ```
~$ sudo dmesg
[  359.064330] usb 1-2: new high-speed USB device number 3 using ehci_hcd
[  359.299880] Initializing USB Mass Storage driver...
[  359.301176] scsi7 : usb-storage 1-2:1.0
[  359.301504] usbcore: registered new interface driver usb-storage
[  359.301512] USB Mass Storage support registered.
[  359.340410] usbcore: registered new interface driver uas
[  360.302921] scsi 7:0:0:0: Direct-Access     WD       5000BPV External 1.75 PQ: 0 ANSI: 4
[  360.307792] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  360.312711] sd 7:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  360.313304] sd 7:0:0:0: [sdc] Write Protect is off
[  360.313317] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  360.313919] sd 7:0:0:0: [sdc] No Caching mode page present
[  360.313930] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  360.321550] sd 7:0:0:0: [sdc] No Caching mode page present
[  360.321565] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  360.365552]  sdc: sdc1
[  360.369670] sd 7:0:0:0: [sdc] No Caching mode page present
[  360.369685] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  360.369696] sd 7:0:0:0: [sdc] Attached SCSI disk
[  367.611410] ehci_hcd 0000:00:12.2: force halt; handshake f841c024 00004000 00000000 -> -110
[  367.611425] ehci_hcd 0000:00:12.2: HC died; cleaning up
[  367.611542] usb 1-2: USB disconnect, device number 3
[  367.617661] scsi 7:0:0:0: [sdc] killing request
[  367.617801] scsi 7:0:0:0: [sdc] Unhandled error code
[  367.617810] scsi 7:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  367.617823] scsi 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 09 b2 00 00 52 00
[  367.617851] end_request: I/O error, dev sdc, sector 2482
[  367.696391] scsi 7:0:0:0: [sdc] Unhandled error code
[  367.696406] scsi 7:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  367.696419] scsi 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 09 24 00 00 8e 00
[  367.696448] end_request: I/O error, dev sdc, sector 2340
[  367.696586] FAT-fs (sdc1): FAT read failed (blocknr 2338)
[  367.712956] usb 1-3: USB disconnect, device number 2

```

With the code ~$ sudo dmesg I at least could open an folder with the external drive before it crashed and burned (OK, not readable then - sorry, no flames!)
I have now removed the drive and will now try the rest you wrote. :)

---

### Post by leopoldbirkholm on 2012-05-04
The output of the last suggestion:
```

sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'
sed: couldn't flush stdout: No such device

```
And the WD drive was attached.

---

### Post by leopoldbirkholm on 2012-05-04
OK, so I re-read the article [Unable to enumerate USB device]("http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/").

I first typed in
```

cd /sys/bus/pci/drivers/ehci_hcd

```
Then
```

ls 

```
I followed by noticing the number 0000:00:12.2 and 0000:00:13.2. Then made this input
```

sudo sh -c 'echo -n "0000:00:12.2" > unbind'
Enter
sudo sh -c 'echo -n "0000:00:12.2" > unbind'
Enter
sudo dmesg -C
Enter
sudo dmesg -c
Enter
sudo dmesg
Enter

``` 

I then re-connected my drive and this time the window stayed so now I am trying to copy over an video and see if this work. Will post progress later.

---

### Post by zero2xiii on 2012-05-04
> **leopoldbirkholm said:**
> The output of ```
~$ sudo dmesg
[  359.064330] usb 1-2: new high-speed USB device number 3 using ehci_hcd
[  359.299880] Initializing USB Mass Storage driver...
[  359.301176] scsi7 : usb-storage 1-2:1.0
[  359.301504] usbcore: registered new interface driver usb-storage
[  359.301512] USB Mass Storage support registered.
[  359.340410] usbcore: registered new interface driver uas
[  360.302921] scsi 7:0:0:0: Direct-Access     WD       5000BPV External 1.75 PQ: 0 ANSI: 4
[  360.307792] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  360.312711] sd 7:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  360.313304] sd 7:0:0:0: [sdc] Write Protect is off
[  360.313317] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  360.313919] sd 7:0:0:0: [sdc] No Caching mode page present
[  360.313930] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  360.321550] sd 7:0:0:0: [sdc] No Caching mode page present
[  360.321565] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  360.365552]  sdc: sdc1
[  360.369670] sd 7:0:0:0: [sdc] No Caching mode page present
[  360.369685] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  360.369696] sd 7:0:0:0: [sdc] Attached SCSI disk
[  367.611410] ehci_hcd 0000:00:12.2: force halt; handshake f841c024 00004000 00000000 -> -110
[  367.611425] ehci_hcd 0000:00:12.2: HC died; cleaning up
[  367.611542] usb 1-2: USB disconnect, device number 3
[  367.617661] scsi 7:0:0:0: [sdc] killing request
[  367.617801] scsi 7:0:0:0: [sdc] Unhandled error code
[  367.617810] scsi 7:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  367.617823] scsi 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 09 b2 00 00 52 00
**[  367.617851] end_request: I/O error, dev sdc, sector 2482**
[  367.696391] scsi 7:0:0:0: [sdc] Unhandled error code
[  367.696406] scsi 7:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  367.696419] scsi 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 09 24 00 00 8e 00
[B][  367.696448] end_request: I/O error, dev sdc, sector 2340
[  367.696586] FAT-fs (sdc1): FAT read failed (blocknr 2338)[/B]
[  367.712956] usb 1-3: USB disconnect, device number 2

```


This might be the problem. The Bold parts about the read failures. It disconnects just after the last read failure.

I await your further feedback. At least we have the drive open now. That is a good thing.

Cherz

---

### Post by leopoldbirkholm on 2012-05-04
Ok so I went out for an errand and did turn of my computer. Now on reboot, the problem has come back. When connecting the external drive, it shows the folder for a couple of seconds and then stops.

I input this in Terminal
```

sudo dmesg -c
Enter
sudo dmesg -C
Enter
sudo dmesg
Output
sudo dmesg
[   91.352203] usb 1-1: new high-speed USB device number 3 using ehci_hcd
[   91.552389] Initializing USB Mass Storage driver...
[   91.553362] scsi7 : usb-storage 1-1:1.0
[   91.553653] usbcore: registered new interface driver usb-storage
[   91.553661] USB Mass Storage support registered.
[   91.554541] usbcore: registered new interface driver uas
[   92.595976] scsi 7:0:0:0: Direct-Access     Packard  Bell Silver           PQ: 0 ANSI: 2 CCS
[   92.599226] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   92.601717] sd 7:0:0:0: [sdc] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[   92.602569] sd 7:0:0:0: [sdc] Write Protect is off
[   92.602576] sd 7:0:0:0: [sdc] Mode Sense: 34 00 00 00
[   92.603309] sd 7:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   92.618212]  sdc: sdc1
[   92.624579] sd 7:0:0:0: [sdc] Attached SCSI disk
[  123.115614] ehci_hcd 0000:00:12.2: force halt; handshake f841c024 00004000 00000000 -> -110
[  123.115630] ehci_hcd 0000:00:12.2: HC died; cleaning up
[  123.115758] usb 1-1: USB disconnect, device number 3
[  123.185617] usb 1-3: USB disconnect, device number 2

```

I will re-do the steps about, with editing an file and see if that solves it.

---

### Post by leopoldbirkholm on 2012-05-04
An other note is when I get it to work, I get USB version 1.1 instead of USB version 2 and that makes the transfer speed about 1 MByte per second instead of 12 or 24.

---

### Post by zero2xiii on 2012-05-04
> **leopoldbirkholm said:**
> An other note is when I get it to work, I get USB version 1.1 instead of USB version 2 and that makes the transfer speed about 1 MByte per second instead of 12 or 24.

Hay,

Yes this is only a temporary fix. Disabling the ehci_hcd blocks devices on that pci controler to run at "high speed" or usb 2.0 speeds. For some reason this is a bug or something on some hardware. However we can try something else. I Just have to re-open a session on my opera so I will continue in a new post.

---

### Post by zero2xiii on 2012-05-04
Oka,

Sorry about that. But it seems like if I load a saved session, it closes all currently open tabs. Cant remember where to change the settings.

Anyway, here we go even further down the rabit hole. Btw, this is pretty deep inside the workings of linux/ubuntu. We are not messing with a program but the actual workings of the usb drivers. So take careful note of what you do, so it can be undone if you would mess up. 

I recommend scripting your entire terminal session so we can follow the steps exactly later on.

To set it up open up the terminal (or terminals) you are going to use and type:
```
script -f -a terminal_session1.txt

```
This will create a file called "terminal_session1.txt" under your home folder with the exact 'script' of that terminal session. To exit when you are done, type:
```
exit
```

Right now that that is out of the way.
We are going to test two possible solutions.
First up we are going to leave the usb speed as usb 2.0 speeds and switch off autosuspend:

```
cd /sys/module/usbcore/parameters/

```
We will be working in this directory (please make sure you remembered to active script before continuing. As you will be doing a few reboots to test different parameters.

```
sudo echo -1 >./autosuspend
```
if this gives you a permission error try:
```
sudo sh -c 'echo "-1" >./autosuspend '
```

Now you can either reboot the machine and test the drive now or continue and just do everything and hope something will work. I would recommend doing it step by step however and reboot.

Next we can change the time for the initial 64-byte USB_REQ_GET_DESCRIPTOR request:

```
sudo echo "10000">./initial_descriptor_timeout
```
again if this gives you a permission error try:
```
sudo sh -c 'echo "10000">./initial_descriptor_timeout '
```

Again reboot and see if the issue is resolved.

Lastly we are going to try and change the schemes around so the old one is tried first (usb 1.1 and then 2.0). This will affect the speed again, but not the above two:

```
sudo echo "Y">./old_scheme_first
```
if this fails due to invalid argument try:
```
sudo echo "1">./old_scheme_first
```
again if you get permission error try one of the following:
```
sudo sh -c 'echo "Y">./old_scheme_first '
```
```
sudo sh -c 'echo "1">./old_scheme_first '
```

PS The permission errors might be caused because sudo does not give you sufficient rights and we are not allowed to advice you to run commands as root as it is very dangerous.

One of the above should also help you to fix the issue. I am hoping it is only a issue due to the susspending of the device, at worst the waiting time. If you do the last thing, you can just aswell keep running it on usb 1.1.... It will work, but obviously speed will be an issue.

After all this, please report back. If something worked, and so forth. If it did, we can make sure it is a permanent fix. If you are forced to use it as a usb 1.1 device, I am unsure how to fix that as to keep usb 2.0 speeds.

Best of luck and remeber "script". Should something go wrong.

Cherz

---

### Post by leopoldbirkholm on 2012-05-07
@ zero2xiii, thank you for taking time to help me.

I tried your solution but they did not work. So I have re-installed the system and starting from scratch, so to speak.

After re-installing the system, I noticed two tings that did not happen with the first installation. The audio works fine from start and also the Wi-Fi.

First, the USB-problem seemed solved. But after transferring one file on 700 MB it died again. I will do now two things. Start the text-logging using your script and open an folder to share via Ubuntu One where I will put out the .txt files.

I have created an folder. It's on SkyDrive since I could not figure out how to make an folder public on Ubuntu One. 

[Click here for the SkyDrive folder.]("https://skydrive.live.com/redir.aspx?cid=2556cffceefa1239&resid=2556CFFCEEFA1239!635&parid=root")

---

### Post by zero2xiii on 2012-05-08
Hay,

Wow that is strange.

The last command:
```
sudo sh -c 'echo "1">./old_scheme_first '
```

Is never tried? Or am I looking over it? Hmmf no matter, it is strange. Did my original help fix your problem, with only the speed being downgraded to usb1.1, but the drive functioned?

I am guessing it has something to do with the usb controler. Check in your BIOS if "Legacy USB Support" is enabled or not? Switch it over to the other option and try then.

If all this fails, during GRUB hit e, then append to the end of the boot line of your linux (usualy the last words are something like "quitesplash" or such, my boot flags are non standard so I am unsure what the usual are) just put a space after the last word in the line and append "irqpool" and then hit ctrl + X I think to boot using those boot flags. Then try the drive.

If NON of this works. I am all out of ideas. Something of this usualy works, I have never had anything that still didn't work up to this point.

Cherz

---

### Post by leopoldbirkholm on 2012-05-10
The issue remains. The only why I can fix it is by disable USB 2 and use USB 1.1. The solution for that I quote zero2xiii.

> **zero2xiii said:**
> 

```
sudo dmesg -c
```
This clears the log, after being displayed to screen. Now plug in your drive, wait a few moments and then:

```
sudo dmesg
```

... remove your drive from the usb port.

I am going to assume that it is an error regarding "ehci_hcd".

After you have done the above, we are going to disable ehci_hcd:

```
cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'
```
I found the above from [here]("http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/")
It is just so much easier than explaining the entire process by hand.

After you have done this, plug the device back in. Again do:

```
sudo dmesg -c
sudo dmesg
```


I cannot find any other way around this problem. To use external drives like USB drives on a MSI X370, you must disable the highspeed (compared to USB 1.1) USB and use the old USB 1.1. That means about 1 Mbit per second.

So, with sad heart, I must go back to Micrsoft on this unit. :cry:

---

### Post by iyas120 on 2012-05-16
Maybe this solution can help you

[http://ubuntuforums.org/showthread.php?p=11882892](http://ubuntuforums.org/showthread.php?p=11882892)

In terminal:
```
 sudo gedit /etc/modprobe.d/blacklist.conf
```

Add the following line, save, and reboot:
```
 blacklist rts5139
```

My MSI X370 work fine now and any usb device can run smoothly

---

### Post by iyas120 on 2013-01-11
Using ubuntu 12.04.1 and above will solve usb problem for amd E series chipset. New kernel is better for these laptop

---

