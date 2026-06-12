---
title: "New Kogan e-book reader does not mount in 10.04"
date: 2010-08-23
forum: General Help
---

### Post by jsampaio57 on 2010-08-23
Kogan put in the market last week (20/08/2010) in Australia a new e-book reader. As usual, it runs under gnu/Linux v. 2.6. However, when connected to Linux (Ubuntu 10.04, and Debian 5.5) it does not work. 

the result of lsusb is: (the device is the Netchip)

...
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0525:a4a5 Netchip Technology, Inc. Linux-USB File Storage Gadget
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
...

In principle the device seems to use a usb 2.0 interface, but Bus 001 Device 006 is a usb 1.1.

The result of dmesg is:

...
[ 3250.344034] usb 1-4: new high speed USB device using ehci_hcd and address 6
[ 3250.476365] usb 1-4: config 1 interface 0 altsetting 0 bulk endpoint 0x82 has invalid maxpacket 64
[ 3250.476372] usb 1-4: config 1 interface 0 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64
[ 3270.476241] usb 1-4: configuration #1 chosen from 1 choice
[ 3275.476146] usb 1-4: can't set config #1, error -110

I tried the latest version of Calibre (0.7.15), released Saturday [21/08] to include Kogan, but I get the following message in the "Debug device detection (Preferences > Advanced):

...
 ['0x525', '0xa4a5', '0x319', '', 'File backed Storage Gadget', ''],
 ['0x1d6b',
  '0x1',
  '0x206',
  'Linux 2.6.32-24-generic-pae ohci_hcd',
  'OHCI Host Controller',
  '0000:00:13.2'],
...
Looking for KOGAN
	(1317, 42149, 793, '', 'File backed Storage Gadget', '')
...
Trying to open Kogan Device Interface ... failed...
...
Opening of the following devices failed
<calibre.devices.misc.KOGAN object at 0xab4a50c>
Traceback (most recent call last):
  File "/home/kovid/build/calibre/src/calibre/devices/__init__.py", line 117, in debug
  File "/home/kovid/build/calibre/src/calibre/devices/usbms/device.py", line 637, in open
  File "/home/kovid/build/calibre/src/calibre/devices/usbms/device.py", line 607, in open_linux
DeviceError: Unable to detect the KOGAN disk drive. Your  kernel is probably exporting a deprecated version of SYSFS.

It seems to have a conflict. In the output of dmesg it says that the device is a high-speed ehci_hce, and the output of Calibre says that it is a ohci_hcd (and that the kernel is exporting a deprecated SYSFS)!!!

The e-reader works normally in Windows XP-pro (sorry) but failed in all my boxes (2 desktop and 1 laptop running 10.04, and 1 laptop running Debian 5.05)

Maybe somebody can help to solve this problem. Thanks,

cheers...
Jorge

---

### Post by coeus on 2010-08-24
I've had the same problem on 10.04

Some people have had success from reading the whirlpool forums, but they do not specify if they are using 32 or 64 bit.  I am using 64, how about yourself?

---

### Post by jsampaio57 on 2010-08-24
> **coeus said:**
> I've had the same problem on 10.04

Some people have had success from reading the whirlpool forums, but they do not specify if they are using 32 or 64 bit.  I am using 64, how about yourself?

I have browsed and even posted in the whirlpool, but I didn't find any successful case there (I will revisit). I am using a 64 machine running 32, but my other machines are 32 and run 32 (I share downloaded .deb's so I save downloading time and I tired of keeping A64 and i386 versions - In the end I didn't noticed much difference...). Anyway, I had no success with anyone of them, including one using Debian 5.05. Today I chatted with Kogan support and I was told that they don't have a Linux machine to test, but that tomorrow they will come back to me. They asked me to send an email with details, and I did it. Now I am waiting. If I hear something from them, I forward to here.

---

### Post by wwood on 2010-08-25
> **jsampaio57 said:**
> If I hear something from them, I forward to here.

Thanks, I'm interested to hear what they say too.

---

### Post by jsampaio57 on 2010-08-25
> **wwood said:**
> Thanks, I'm interested to hear what they say too.

Kogan's support (chat at [http://www.kogan.com.au/support](http://www.kogan.com.au/support) or email at [email]support@kogan.com.au[/email]) told me today that they are investigating the issue. It seems to me that there is a conflict in the USB ports. The device seems to be an ehci_hdc (480Mbps) and somehow it tries to mount in a ohci_hdc (12Mbps). Under windows (sorry) the connection is very slow for a USB 2.0. (it took hours to copy the 1700+ eBooks to my PC). Between the PC and a simple pen drive it is much faster.

Anyone can go to chat with Kogan support ([http://www.kogan.com.au/support](http://www.kogan.com.au/support)) (Australia East Time) and put a little "pressure" ;).

---

### Post by wwood on 2010-08-25
Can you simply copy the ebooks to an sd card directly (or via a camera or something), and then open them on the kogan?

---

### Post by satish_j on 2010-08-25
Have you checked the settings in the pdf reader device that tells something about PC connections?
I recently faced similar issue with my cell phone not mounting even though it was detected in 'lsusb' command...turned out that the setting in my cell phone was changed from 'Mass storage' to 'Pc suite'..Changed back to Mass storage and the card was detected successfully..

---

### Post by jsampaio57 on 2010-08-25
> **wwood said:**
> Can you simply copy the ebooks to an sd card directly (or via a camera or something), and then open them on the kogan?

Yes, of course (am using a 16Gb card); but this involves removing the device from the leather cover, opening the SD port, removing the SD card, installing in a card reader, sticking in the USB port of the PC... and reversing the operation, and this can't be done with the internal 2G memory. In addition, if the facility is there we must be able to use it. What surprises me is that Kogan' eBook reader runs under Linux (as most readers). Cheers...

---

### Post by jsampaio57 on 2010-08-25
> **satish_j said:**
> Have you checked the settings in the pdf reader device that tells something about PC connections?
I recently faced similar issue with my cell phone not mounting even though it was detected in 'lsusb' command...turned out that the setting in my cell phone was changed from 'Mass storage' to 'Pc suite'..Changed back to Mass storage and the card was detected successfully..

There is no PC connection option in the "Settings". The "Device Settings" allows to chance the Device Name and select the language. The device shows in the lsusb, and the dmesg shows a lot of conflicts. Cheers...

---

### Post by jsampaio57 on 2010-08-25
> **wwood said:**
> Can you simply copy the ebooks to an sd card directly (or via a camera or something), and then open them on the kogan?

Of course I can, but this doesn't work with the internal memory.

---

### Post by jsampaio57 on 2010-08-25
[QUOTE=wwood;9763099]Can you simply copy the ebooks to an sd card directly (or via a camera or something), and then open them on the kogan?[/QUOTE

Nothing from Kogan up to now. Yesterday I chatted with the support and he/she told me that they are investigating.

---

### Post by jsampaio57 on 2010-08-27
For those with sufficient technical knowledge and are willing to help. The following message is printed after the device is connected and dmesg is issued:

usb 1-4: new high speed USB device using ehci_hcd and address 2
usb 1-4: config 1 interface 0 altsetting 0 bulk endpoint 0x82 has invalid maxpacket 64
usb 1-4: config 1 interface 0 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64

(this is fro a Laptop Toshiba Satellite Pro T110 running Ubuntu 10.04)

What concerns me is the "invalid maxpacket 64". What can be done?

Cheers... Jorge

---

### Post by wwood on 2010-08-27
> Yes, of course (am using a 16Gb card); but this involves removing the device from the leather cover, opening the SD port, removing the SD card, installing in a card reader, sticking in the USB port of the PC... and reversing the operation, and this can't be done with the internal 2G memory. In addition, if the facility is there we must be able to use it. What surprises me is that Kogan' eBook reader runs under Linux (as most readers). Cheers... 
> **jsampaio57 said:**
> Of course I can, but this doesn't work with the internal memory.
Calm down, no need to reply twice&#11822;

I'm no expert, but could you try removing the echi kernel module, to force the kogan to load in a more backwards compatible way? Perhaps the script at
[http://moserei.de/index.php/tag/disable-ehci]("http://moserei.de/index.php/tag/disable-ehci")
might be of use?

---

### Post by jsampaio57 on 2010-08-27
> **wwood said:**
> Calm down, no need to reply twice&#11822;

I'm no expert, but could you try removing the echi kernel module, to force the kogan to load in a more backwards compatible way? Perhaps the script at
[http://moserei.de/index.php/tag/disable-ehci]("http://moserei.de/index.php/tag/disable-ehci")
might be of use?

Sorry for that.
I tried the script but I got an error:
jorge@AMD64:~$ sudo ./force_ohci.sh "0525:a4a5"
./force_ohci.sh: 9: Syntax error: "(" unexpected

I tried also without " ":
jorge@AMD64:~$ ./force_ohci.sh 0525:a4a5
./force_ohci.sh: 9: Syntax error: "(" unexpected

I'm still concern with that "invalid maxpacket 64"

Cheers... Jorge

---

### Post by wwood on 2010-08-27
> **jsampaio57 said:**
> 
jorge@AMD64:~$ sudo ./force_ohci.sh "0525:a4a5"
./force_ohci.sh: 9: Syntax error: "(" unexpected

Try running it using bash, instead of plain old sh, which for some reason is specified in the shebang (line 1). So, either modify the first line to be 
```
#!/bin/bash
```
or simply run
```
$ sudo bash force_ohci.sh "0525:a4a5"
```


> **jsampaio57 said:**
> 
I tried also without " ":
jorge@AMD64:~$ ./force_ohci.sh 0525:a4a5
./force_ohci.sh: 9: Syntax error: "(" unexpected

Quotes shouldn't matter:

```
$ echo "0525:a4a5"
0525:a4a5
$ echo 0525:a4a5
0525:a4a5
```

> **jsampaio57 said:**
> 
I'm still concern with that "invalid maxpacket 64"

I've read that that isn't a big problem.


Sorry I can't try these things out, mine was supposed to have arrived by now. How long did you wait for it to arrive? I'm in Melbourne.

---

### Post by wwood on 2010-08-28
Sorry, that script is not going to work for other reasons too, I'd say. The files that it refers to don't appear to exist (on my 10.04 at least).

I can't seem to find a way to disable usb2 for a specific device. I realise this isn't an ideal solution, but could you try disabling usb2 in your bios and see if that helps?

In older kernels modprobe -r ehci would probably work, but now ehci is part of the kernel itself so that no longer works.

---

### Post by jsampaio57 on 2010-08-28
> **wwood said:**
> Sorry, that script is not going to work for other reasons too, I'd say. The files that it refers to don't appear to exist (on my 10.04 at least).

I can't seem to find a way to disable usb2 for a specific device. I realise this isn't an ideal solution, but could you try disabling usb2 in your bios and see if that helps?

In older kernels modprobe -r ehci would probably work, but now ehci is part of the kernel itself so that no longer works.

Yes, neither modprobe -r or rmmod works. I tried changing the shebang to /bin/bash; it complains about /proc/bus/usd/devices that doesn't exist.
There is a /sys/bus/usb/devices, but it doesn't work either.
I have already tried disabling usb 2.0 in the bios. As you see, I've been struggling with this with no success. I don't have the technical knowledge, and it seems that those that have, do not have this device. Maybe after you receive yours, you'll be more successful than me.

Sometimes it is disappointing because there are people that know what is going on (at least somebody built and assemble those things) This reader runs under linux, and somebody made it to work with windows, but didn't care if it would work with linux or not. Even Kogan doesn't know what todo. Come on! somebody built this!!!, or maybe it had felt from Heaven.


(I put the order for the Kogan early August and received it on the 19 of August - and I am in Perth)

Cheers...

---

### Post by wwood on 2010-08-28
I can commiserate. It looks like a bug even under windows though, because as you say, while it is capable of usb2, it only runs at usb1 speeds on windows. So if there is a firmware update to fix it on windows, it'll then run under linux too. Here's hopin'.

Anyway, I'll get back to you when I've had a play. No harm in learning more about the linux kernel.

---

### Post by jsampaio57 on 2010-08-30
I was contacted by Kogan support. They said that they developed a firmware for the issue. However in the end of the message they said that "... is should work with your MAC"... OMG!!! I said clearly that the problem is under Linux!!! Anyway, I followed the instructions as in the email, but for my disappointment, the procedure did not work (not that the firmware didn't fix the issue, but that the upgrade didn't happen). Here I transcribe the email from Kogan.

--- begin of email
Hi Jorge,
We have developed a firmware upgrade for this issue.
Please follow the instructions to do the firmware upgrade:-

1> Download the zip file from the following link:-
[http://rapidshare.com/files/415613433/IE1006068.rar](http://rapidshare.com/files/415613433/IE1006068.rar)
2> Unzip the file and copy all the files not folder to the SD card.
3> Make sure that there is no other content on the SD card.
4> Turn on the e-book reader.
5> Insert the SD card
6> Once the e-book finish loading the SD card press the down button on
the left hand side and press the reset button at the same time.
7> Keep the down button pressed and release the reset button. Keep the
down button pressed till it display U-disk boot
8> Once the upgrade finished remove the SD card and press the reset button.
9> The e-book will re-start and then it should work with your MAC.

Please let me know how you go?
Kindest Regards,
Adam
----- end of email

(tun unrar, I had to install ... unrar) 
Before I start the procedure, I jotted down the original firmware number (Settings>About Product): V.1.1.0.0.3
Then I followed the instructions. I was expecting it display the "U-disk boot", which never happened. Firmware still the same! Maybe the procedure as instructed is wrong. I am sending another email to Kogan, to check it out. 

I keep trying!!!
Cheers... Jorge

---

### Post by jsampaio57 on 2010-09-02
Kogan asked me to send the device back to them. The original problem is a buggy firmware and, in addition, my device is buggy too, because it is not booting with the U-boot. A rep called me and asked me to follow the procedure across the phone (:!:)... surprise! Didn't work. I sent it yesterday.

---

### Post by lisati on 2010-09-02
> **jsampaio57 said:**
>  "... is should work with your MAC"...
D'oh! ):P

I've had similar with people trying to get me to use Windows commands to get Windows software working when I've already told them that it's Ubuntu. :D

---

### Post by deepee_oz on 2010-09-03
I have the same problem.
Did the firmware upgrade today and it completed without error.
However, the device still doesn't mount.
I'll email Kogan support and let them know.

I thought I'd backup the e-book folder on a Windows machine prior to the upgrade. It took oven an hour for around 500MB of .txt files!

---

### Post by deepee_oz on 2010-09-03
My trigger finger was a bit too itchy...

I'd been making some config changes to Pulse Audio prior to trying to mount the e-book reader.

I rebooted my system, tried again and can now mount the Kogan as a 1.9GB Filesystem.

Happy days!


[   83.992054] usb 1-4: new high speed USB device using ehci_hcd and address 5
[   84.125076] usb 1-4: configuration #1 chosen from 1 choice
[   84.192704] Initializing USB Mass Storage driver...
[   84.192910] scsi2 : SCSI emulation for USB Mass Storage devices
[   84.193277] usbcore: registered new interface driver usb-storage
[   84.193284] USB Mass Storage support registered.
[   84.204469] usb-storage: device found at 5
[   84.204474] usb-storage: waiting for device to settle before scanning
[   89.204198] usb-storage: device scan complete
[   89.204675] scsi 2:0:0:0: Direct-Access     Linux    File-Stor Gadget 0319 PQ: 0 ANSI: 2
[   89.209190] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   89.222558] sd 2:0:0:0: [sdb] 3643392 512-byte logical blocks: (1.86 GB/1.73 GiB)
[   89.222916] sd 2:0:0:0: [sdb] Write Protect is off
[   89.222922] sd 2:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[   89.222926] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   89.225423] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   89.225435]  sdb:
[   89.237307] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   89.237317] sd 2:0:0:0: [sdb] Attached SCSI removable disk

---

### Post by wwood on 2010-09-03
Hoorah!

Is it as slow on linux as for windows?

---

### Post by deepee_oz on 2010-09-05
Yes it's still slow transferring files.
I just ran a quick test with around 200MB of MP3's.
Took around 5 minutes.

However, for the main purpose of uploading e-books it will suffice.

---

### Post by jsampaio57 on 2010-09-06
> **deepee_oz said:**
> I have the same problem.
Did the firmware upgrade today and it completed without error.
However, the device still doesn't mount.
I'll email Kogan support and let them know.

I thought I'd backup the e-book folder on a Windows machine prior to the upgrade. It took oven an hour for around 500MB of .txt files!

Did you compare the version number before and after the upgrade? The instructions says that during the upgrade, after pressing down button and reset, the screen should show U-disk boot. It never showed the message in my tries, and the version number didn't change (what number it shows in your device?). But it seems that it went OK with you. I sent my device back to Kogan and they sent it back to me today. Should arrive tomorrow or day after. So, it is still slow after the upgrade, isn't it?  What a shame, that is a USB2.0. Once I downloaded the books to a windows (1.7Gb) and when I tried to upload again it indicated 190min to finish the upload!!!. Even USB1.1 would be faster than that. At least you don't have to remove the SD whenever you need to add a file.
Cheers...
Jorge

---

### Post by jsampaio57 on 2010-09-06
> **deepee_oz said:**
> Yes it's still slow transferring files.
I just ran a quick test with around 200MB of MP3's.
Took around 5 minutes.

However, for the main purpose of uploading e-books it will suffice.

This is better! 200 MB in 5 min is 4 times faster than 1.7GB in 3 hours+ (that's under windows).

---

### Post by deepee_oz on 2010-09-06
I forgot to check the firmware version before the upgrade but the current version shows as V.1.1.0.03
Hardware Version is S16.601.2.0
Software Version is V3.0

---

### Post by wwood on 2010-09-06
> This is better! 200 MB in 5 min is 4 times faster than 1.7GB in 3 hours+ (that's under windows).
Is windows as wildly inaccurate as it used to be? Maybe run an actual test rather than just accepting what it is predicting?

---

### Post by jsampaio57 on 2010-09-06
> **wwood said:**
> Is windows as wildly inaccurate as it used to be? Maybe run an actual test rather than just accepting what it is predicting?

No,no; that was the real (proper!) time that took to upload the 1.7GB from my pc to the reader. The gauge kept swinging between ~150 and ~190 minutes.

---

### Post by jsampaio57 on 2010-09-06
> **deepee_oz said:**
> I forgot to check the firmware version before the upgrade but the current version shows as V.1.1.0.03
Hardware Version is S16.601.2.0
Software Version is V3.0

In the instruction to upgrade the firmware (step 7) it says that one should keep the down button pressed until the device displays "U-disk boot". Did you see the the "U-dist boot" in the screen during the upgrade. I didn't see anything like that. The device simply boot normally, with no measurable delay. What is weird is that you said that the firmware number is V.1.1.0.03. As far as I remember, this is exactly the number before the upgrade, and also the same after I have followed the procedure, which I suppose didn't work (firstly because there were no U-disk boot message, secondly because the number didn't change, and thirdly because after the "upgrade" the device continued not mounting and giving the same error messages after dmesg. (I tried in 4 different machines, 3 running Ubuntu 10.04 and one running Debian 5.05. I also tried after booting with Live CD)

Is there anybody here that has NOT run the upgrade process to check the firmware version number? Cheers...

---

### Post by jsampaio57 on 2010-09-08
I received my reader back from Kogan. I checked the version and it says V.1.1.0.03, which means that it is the same version as before (I wonder if the upgrade files changed the version number). Kogan's support keeps insisting that "I should press and hold the down button (that is the lower button in the LHS of the device) while pressing and releasing the reset buttom in the back" :-\" 

Finally the device mounts now, but not without problems. I downloaded the Kogan eBooks folder to my PC (~1.7 MB) and it took 2.35min. I uploaded the same folder into the SD card and it took 2:45min. Then I deleted the original folder from the internal memory and tried to upload it to the internal memory. At the first try, the process hung after ~20%. I ended up aborting the transfer and, after reconnected, the internal memory turned into read-only; I rebooted reader and PC, reconnected... same. I had to reformat the internal memory to make it read-write. Then I tried upload again; it took 8:31 min. During the upload, the process interrupded 2 times, while dmesg presented the following messages:
[  650.112019] usb 2-5: reset high speed USB device using ehci_hcd and address 4
[  733.100015] usb 2-5: reset high speed USB device using ehci_hcd and address 4

Anyway. it seems to work (barely) now. Kogan put the firmware upgrade again available at [http://www.sendspace.com/pro/dl/5bi36u](http://www.sendspace.com/pro/dl/5bi36u)
 (the link at rapidshare expired)

Cheers...

---

