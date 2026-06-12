---
title: "External hard drive not detected on 9.10"
date: 2010-01-04
forum: General Help
---

### Post by Rodemire on 2010-01-04
Hi all,

My Toshiba 500Gb USB hard drive is not being detected anymore when i insert it in 9.10. It only started doing this from last week, it was fine before (and it works fine in Windows XP). The connections are fine and all, because when i type "lsusb", i see it as follows:

-----------------------------------------------------------------------------------------------------
Bus 001 Device 003: ID 19d2:0063 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
** Bus 002 Device 004: ID 0930:0b09 Toshiba Corp. **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
--------------------------------------------------------------------------------------------------------

Also,i typed "sudo fdisk -l" and got the following:

----------------------------------------------------------------------------------------------
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb678b678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551       60801   467901157+   f  W95 Ext'd (LBA)
/dev/sda5            2551       30979   228355911    7  HPFS/NTFS
/dev/sda6           30980       60801   239545183+  83  Linux

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa375a375

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
----------------------------------------------------------------------------------------

I have two internal hard drives, a 20Gb (sdb) and a 500Gb (sda) and the external hard drive seems not to be picked up as above.

I also tried "dmesg" after plugging the external hard drive and this was the output of the last couple of lines:

-----------------------------------------------------------------------------------------------------
[ 1008.377727] usb 1-6: USB disconnect, address 2
[ 1051.652060] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 1051.804489] usb 1-6: configuration #1 chosen from 1 choice
[ 1051.813956] usb_storage: `' invalid for parameter `delay_use'
------------------------------------------------------------------------------------------------------

Would anyone be able to help me understand why it is not being auto-mounted like it used to be and is there a way i can maybe manually mount it?

All help is appreciated,

NB: I posted on someone else's thread here: [http://ubuntuforums.org/showthread.php?t=1370616](http://ubuntuforums.org/showthread.php?t=1370616) and one of the guys recommended i start my own thread.

Thanks again.

PS: How do i put the output of my commands into a square with borders?

---

### Post by Rodemire on 2010-01-05
Bump.

---

### Post by audiomick on 2010-01-05
Hi.
Cant help you with the drive, sorry.

If you want to
```
put your output into a box
```
in your posts, you select the text and click on the # symbol at the top of the message window.

Hope you get your drive sorted...:)

---

### Post by Leppie on 2010-01-05
> **Rodemire said:**
> NB: I posted on someone else's thread here: [http://ubuntuforums.org/showthread.php?t=1370616](http://ubuntuforums.org/showthread.php?t=1370616) and one of the guys recommended i start my own thread.
that was me, and i updated that thread this morning ;)

> **Rodemire said:**
> PS: How do i put the output of my commands into a square with borders?
click the hash icon (#) in the message tool bar, or use the [code] tags.

---

### Post by anaconda on 2010-01-05
If you cant see your USB-disk from the output of "sudo fdisk -l" then you also cant mount it manually.

But have you tried connecting the USB-hd to a different USB-port? preferably one that is directly in your machine (eg. not divided to multiple USB ports)

I once had a problem, where the usb-disk would work only if connected directly to the machine...

---

### Post by Rodemire on 2010-01-05
> **anaconda said:**
> If you cant see your USB-disk from the output of "sudo fdisk -l" then you also cant mount it manually.

But have you tried connecting the USB-hd to a different USB-port? preferably one that is directly in your machine (eg. not divided to multiple USB ports)

I once had a problem, where the usb-disk would work only if connected directly to the machine...

Ya, I tried connecting to all the usb drives and no difference was noted. Its weird i guess.

>  click the hash icon (#) in the message tool bar, or use the [code] tags. 	

Thanks for this tip. I always wondered how to do it and was scared to ask. Lol

---

### Post by john newbuntu on 2010-01-05
I had a similar problem a few months back that just disappeared later.  At that time, I did not investigate it.  Can you try with a different kernel and see if you are able to read the drive?
On googling your dmesg error: usb_storage: `' invalid for parameter `delay_use'
you might want to try setting usb_storage.delay_use=1 and see if that helps.
This is in the file /etc/default/grub for the GRUB_CMDLINE_LINUX_DEFAULT variable.  Once you set this, run "sudo update-grub2" and then reboot.
If it does not help, just revert back to the original file and run sudo update-grub2 again.

---

### Post by Leppie on 2010-01-05
could you post the output of the following command:
```
$cat /sys/module/usb_storage/parameters/delay_use
```

---

### Post by Rodemire on 2010-01-06
> **john newbuntu said:**
> I had a similar problem a few months back that just disappeared later.  At that time, I did not investigate it.  Can you try with a different kernel and see if you are able to read the drive?
On googling your dmesg error: usb_storage: `' invalid for parameter `delay_use'
you might want to try setting usb_storage.delay_use=1 and see if that helps.
This is in the file /etc/default/grub for the GRUB_CMDLINE_LINUX_DEFAULT variable.  Once you set this, run "sudo update-grub2" and then reboot.
If it does not help, just revert back to the original file and run sudo update-grub2 again.

> **Leppie said:**
> could you post the output of the following command:
```
$cat /sys/module/usb_storage/parameters/delay_use
```

Okay, i will try these suggestions when i get home. I will also post the output here. Thanks guys.

---

### Post by Rodemire on 2010-01-06
> **Leppie said:**
> could you post the output of the following command:
```
$cat /sys/module/usb_storage/parameters/delay_use
```

It returns:

```
 cat: /sys/module/usb_storage/parameters/delay_use: No such file or directory 
```

I went to the file system and there is no such folder. I took a screenshot as attached:

---

### Post by Leppie on 2010-01-06
try loading the usb_storage module:
```
modprobe usb_storage
```

then connect the usb drive and see if it is detected

---

### Post by Rodemire on 2010-01-11
> **john newbuntu said:**
> I had a similar problem a few months back that just disappeared later.  At that time, I did not investigate it.  Can you try with a different kernel and see if you are able to read the drive?
On googling your dmesg error: usb_storage: `' invalid for parameter `delay_use'
you might want to try setting usb_storage.delay_use=1 and see if that helps.
This is in the file /etc/default/grub for the GRUB_CMDLINE_LINUX_DEFAULT variable.  Once you set this, run "sudo update-grub2" and then reboot.
If it does not help, just revert back to the original file and run sudo update-grub2 again.

Could you please show me a screenshot of how this will look like in the file (/etc/default/grub). I tried it and it didnt seem to change anything, and i am now thinking maybe i didnt do it correctly.

---

### Post by Rodemire on 2010-01-11
> **Leppie said:**
> try loading the usb_storage module:
```
modprobe usb_storage
```then connect the usb drive and see if it is detected

Hi Leppie, 

the command gives the following output, 

```
 WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-vmc, it will be ignored in a future release.
FATAL: Error inserting usb_storage (/lib/modules/2.6.31-14-generic-pae/kernel/drivers/usb/storage/usb-storage.ko): Operation not permitted 
```Thats not good right?!

PS: It still doesnt pick up the hard drive after the modprobe. 
Thanks for your help thus far guys.

---

### Post by Leppie on 2010-01-11
sorry, you need root permissions to do that:
```
sudo modprobe usb_storage
```

also move the modprobe.conf (but do not overwrite an already existing modprobe.conf in the destination dir):
```
sudo mv /etc/modprobe.conf /etc/modprobe.d/modprobe.conf
```

---

### Post by Rodemire on 2010-01-11
> **Leppie said:**
> sorry, you need root permissions to do that:
```
sudo modprobe usb_storage
```also move the modprobe.conf (but do not overwrite an already existing modprobe.conf in the destination dir):
```
sudo mv /etc/modprobe.conf /etc/modprobe.d/modprobe.conf
```

the results above are after i had done it with sudo. With or without sudo it still presents the same results.

I will move the .conf, what does that do? If i may ask.:-)

Thanks Leppie, i know this must be mind boggling right now and infuriating but i really appreciate the help hey.

---

### Post by Leppie on 2010-01-11
it should contain the parameters for the usb_module to be used when loading the module.

could you post the contents of the other file mentioned in the error /etc/modprobe.d/blacklist-vmc and the file /etc/blacklist.conf? (and maybe the output of "ls -l /etc/modprobe.d/")

---

### Post by Rodemire on 2010-01-12
> also move the modprobe.conf (but do not overwrite an already existing modprobe.conf in the destination dir):
```
sudo mv /etc/modprobe.conf /etc/modprobe.d/modprobe.conf
```Hi Leppie, 

This piece of code turned out to be the winning one. Moving the modprobe.conf to /etc/modprobe.d was what was needed. In some way it now makes sense to me the error messages i was receiving. Basically my modprobe.conf was in the wrong folder hence it giving the following warning.
```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
```

Secondly, the modprobe.conf was not properly written,  when i opened it it was written as:

```
 usb_storage.delay_use= 1
```I noticed there was a space between the "=" and the "1", hence the reason why it was giving me this error:

```
 `' invalid for parameter `delay_use'
```So i removed the space and my memory sticks and hard drives were automatically detected.

Looking back there was no way i could have understood what was happening without you guys, thanks again Leppie and john newbuntu. Now i don't need to go to Windows to access my external drives.

---

### Post by Leppie on 2010-01-12
glad you've been able to resolve the issue :)

---

