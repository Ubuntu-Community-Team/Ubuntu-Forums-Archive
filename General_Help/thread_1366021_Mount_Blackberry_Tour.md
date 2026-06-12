---
title: "Mount Blackberry Tour"
date: 2009-12-27
forum: General Help
---

### Post by prem1er on 2009-12-27
I'm trying to mount the memory card in my Blackberry Tour through the usb connection. When I use fdisk -l the device doesn't show up. What do I need to do in order to mount the device and read the files on it?

---

### Post by prem1er on 2009-12-28
I have this in my kern.log file. So the device is being detected, but how can I browse the files on it?


```
Dec 27 23:59:28 lahey kernel: [ 8926.290096] usb 2-3: new high speed USB device using ehci_hcd and address 8
Dec 27 23:59:28 lahey kernel: [ 8926.453575] usb 2-3: configuration #1 chosen from 1 choice
Dec 27 23:59:28 lahey kernel: [ 8926.464995] scsi11 : SCSI emulation for USB Mass Storage devices
Dec 27 23:59:28 lahey kernel: [ 8926.465579] usb-storage: device found at 8
Dec 27 23:59:28 lahey kernel: [ 8926.465585] usb-storage: waiting for device to settle before scanning
Dec 27 23:59:33 lahey kernel: [ 8931.460879] usb-storage: device scan complete
Dec 27 23:59:33 lahey kernel: [ 8931.461957] scsi 11:0:0:0: Direct-Access     RIM      BlackBerry SD    0003 PQ: 0 ANSI: 4 CCS
Dec 27 23:59:33 lahey kernel: [ 8931.463136] sd 11:0:0:0: Attached scsi generic sg2 type 0
Dec 27 23:59:33 lahey kernel: [ 8931.472595] sd 11:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by dev.null on 2010-03-18
> **prem1er said:**
> I'm trying to mount the memory card in my Blackberry Tour through the usb connection. When I use fdisk -l the device doesn't show up. What do I need to do in order to mount the device and read the files on it?

On Blackberry -
1. Options -> Memory

Media Card support: on
encryption mode: none
Media transfer protocol: on
mass storage mode support: on
Auto enable mass storage mode when connected: yes or prompt (and when you want to mount answer the prompt with 'yes'

<back> and "save"

now connect. It should auto-detect and auto-mount ('yes' if prompted on the mass storage mode)

---

### Post by prem1er on 2010-03-18
Wow. I never thought I would get this working and it has been driving me nuts. I new it was settings on the phone that was causing the problem, but I couldn't find any documentation on it. Thank you so much!

---

### Post by ezm on 2010-05-16
I am having a similar problem.  I can't mount my blackberry tour.  I don't want to sync the thing to any other program; I simply want to get access to the files on the memory card.  I have also already enabled the mass storage option in the memory options of my blackberry.  When I plug in the blackberry nothing occurs.  The blackberry goes to the clock screen, which is what it normally does under these circumstances, but that is it.  I don't get any request to enter the device password, which is what normally happens when I plug the device in under Windows.  Like the previous user, I can tell from the kernel.log that the device has been detected: 

[INDENT]May 16 14:06:24 extremophile kernel: [ 1140.600137] usb 1-3: new high speed USB device using ehci_hcd and address 12
May 16 14:06:24 extremophile kernel: [ 1140.734181] usb 1-3: configuration #1 chosen from 1 choice
May 16 14:06:24 extremophile kernel: [ 1140.741439] scsi11 : SCSI emulation for USB Mass Storage devices
May 16 14:06:24 extremophile kernel: [ 1140.743896] usb-storage: device found at 12
May 16 14:06:24 extremophile kernel: [ 1140.743901] usb-storage: waiting for device to settle before scanning
May 16 14:06:24 extremophile kernel: [ 1140.905222] usb 1-3: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
May 16 14:06:25 extremophile kernel: [ 1142.020164] usb 1-3: reset high speed USB device using ehci_hcd and address 12[/INDENT]

And yet the device does not show up when I issue the "sudo fdisk -l" command.  Any ideas?  I'd really like to get this working.

---

### Post by Yehudah on 2010-06-03
I have the same problem, my log looks like this:  (can't believe I typed that)

Jun  3 11:21:50 yehudah-laptop kernel: [ 1324.354022] usb-storage: device found at 17

Jun  3 11:21:50 yehudah-laptop kernel: [ 1324.354030] usb-storage: waiting for device to settle before scanning

Jun  3 11:21:50 yehudah-laptop kernel: [ 1324.867832] usb 1-3: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1

Jun  3 11:21:50 yehudah-laptop kernel: [ 1324.873954] usb 1-3: USB disconnect, address 17

Jun  3 11:21:50 yehudah-laptop kernel: [ 1325.244125] usb 1-3: new high speed USB device using ehci_hcd and address 18

Jun  3 11:21:51 yehudah-laptop kernel: [ 1325.381854] usb 1-3: configuration #1 chosen from 1 choice

Jun  3 11:21:51 yehudah-laptop kernel: [ 1325.389209] scsi527 : SCSI emulation for USB Mass Storage devices

It charges, the clock shows, and I've set up the media card as per the post above.

Any help?

---

### Post by mcativa on 2010-06-08
Try this...

[http://www.thinktek.ca/articles/article3.php](http://www.thinktek.ca/articles/article3.php)

...
In the syslog file I would see repeated "reset high speed USB device using ehci_hcd and address #" messages. Upon further investigation I learnt that this may be due to the setting for the maximum amount of data that will be transferred to or from the device in a single command, as set in /sys/block/sdb/device/max_sectors once the device is connected. The default setting is 240, which equates to 120KB. This value works for most devices, but the Bold doesn't like it. I changed it to 128 (aka 64KB) using "echo 128 > /sys/block/sdb/device/max_sectors", which is the default for Windows, and hey presto! It worked!

The next question was how to make this the default. Digging deeper into it I learnt that the udev system is responsible for detecting hot plugged devices now and it is controlled by scripts in /etc/udev/rules.d. I added the following line to /etc/udev/rules.d/80-programs.rules to set the default max_sectors value to 128 for all devices. It may result in a slight performance hit, but functionality is more important to me at this point. I may try playing with some benchmarks some day...

      # Blackberry Bold is not happy with max_sectors=240 - JayM 20090317
      SUBSYSTEM=="block", BUS=="usb", KERNEL=="sd*", ATTRS{idVendor}=="0fca", RUN+="/bin/sh -c 'echo 128 >
      /sys/block/%k/device/max_sectors'"
Note: that's only two lines... the SUBSYSTEM command should be one line. It's split for formatting...

Next time I plugged in the Bold and checked max_sectors it was set to 128 and everything worked as expected. Now I can copy files back and forth without any issues.
...

---

### Post by SoFl W on 2010-09-27
I was trying a few things that I found in the forums.  Seems I can either have barrybackup working or mass storage device working but not both.  Changing the configuration files around allows one but not the other.

I have a Blackberry Bold, but this was the last forum that I used to get the device working in mass storage mode.

EDIT:
I had password protected my Blackberry and while working on it the device would time out and it would not allow mass storage mode until I entered the device password, and then again for allowing mass storage mode.  My Blackberry Bold works with both Berrybackup and in mass storage mode provided it doesn't time out and need the password.

---

### Post by SoFl W on 2010-09-30
Tried it again today and couldn't enter mass storage mode, but barrybackup works.
UGH!
Anybody have the BB Bold working with Lucid 10.4?

EDIT:
Seems that after I safely remove the device, unplug it, plug it back it it wont recognize the Blackberry.  Works again after a reboot of the PC.  As far as I have it now I need to reboot my PC each time to have it recognize the Blackberry in Mass Media mode.  Not sure which is easier, taking the microSD card out or rebooting the PC.  
I wonder if there is some stored in memory setting that doesn't get reset after unplugging the device, but does when rebooting.

---

