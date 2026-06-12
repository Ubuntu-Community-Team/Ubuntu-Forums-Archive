---
title: "Does not recognize USB flash memory nor camera"
date: 2006-06-03
forum: General Help
---

### Post by s6dalane on 2006-06-03
I had no problems with USB devices under Breezy, but ever since i switched to Dapper, only my USB mouse works, it doesn't recognize my flash memory nor my camera (Olympus C-55)
My motherboard is Intel D845PESV and all the USB ports are integrated on it. I also tried to report a bug, but I got no response. Any help on how i should pursue my problem is welcome.

---

### Post by s6dalane on 2006-06-07
Anyone?

---

### Post by _simon_ on 2006-06-07
this may be obvious and something you already tried but try plugging each device in a different USB port than normal.

My other halfs Dapper ceased recognising her camera phone yesterday, we got it working again by plugging it in a different port :-k

---

### Post by ifokkema on 2006-06-07
[QUOTE=s6dalane]Anyone?[/QUOTE]
After you plug in a device, run:
```
dmesg |tail -n 20
```

There should be a mention of your usb device (and possibly an error).

---

### Post by s6dalane on 2006-06-08
It gives me the following:
> kaarel@ubuntu:~$ dmesg |tail -n 20
[4297342.554000] scsi0 : SCSI emulation for USB Mass Storage devices
[4297342.554000] usb-storage: device found at 4
[4297342.554000] usb-storage: waiting for device to settle before scanning
[4297342.554000] usbcore: registered new driver usb-storage
[4297342.554000] USB Mass Storage support registered.
[4297347.556000]   Vendor: Generic   Model: USB Flash Disk    Rev: 1.00
[4297347.556000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4297347.560000] usb-storage: device scan complete
[4297347.602000] Driver 'sd' needs updating - please use bus_type methods
[4297347.608000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[4297347.609000] sda: Write Protect is off
[4297347.609000] sda: Mode Sense: 00 06 00 00
[4297347.609000] sda: assuming drive cache: write through
[4297347.613000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[4297347.614000] sda: Write Protect is off
[4297347.614000] sda: Mode Sense: 00 06 00 00
[4297347.615000] sda: assuming drive cache: write through
[4297347.615000]  sda: unknown partition table
[4297347.622000] sd 0:0:0:0: Attached scsi removable disk sda
[4297347.634000] sd 0:0:0:0: Attached scsi generic sg0 type 0


I don't see any errors, but i cannot access the flash disk or is it hidden somewhere and i've been looking to wrong places?

---

### Post by ifokkema on 2006-06-08
[QUOTE=s6dalane]It gives me the following:


I don't see any errors, but i cannot access the flash disk or is it hidden somewhere and i've been looking to wrong places?[/QUOTE]

Your flash drive is recognized and appointed to /dev/sda, then:
```
[4297347.615000] sda: unknown partition table
```

What happens if you run
```
sudo fdisk -l /dev/sda
```

That should print out the partition table of your flash drive. Also, just to be sure, can you confirm that this drive still works on a different PC?

---

### Post by s6dalane on 2006-06-08
I have tried it on a different PC (Windows XP) and it works there.
I tried> sudo fdisk -l /dev/sdabut it gave me nothing.

---

### Post by ifokkema on 2006-06-08
[QUOTE=s6dalane]I triedbut it gave me nothing.[/QUOTE]
Hmm... it's appointed to the /dev/sda device, but then Linux just fails at interpreting the rest. I assume you see your flash device using usbview. Could you please try:
```
sudo apt-get install usbview
usbview
```
A screen will pop up showing your USB devices. Your flash drive should be mentioned.

Also, could you please send the output of:
```
ls -l /dev/sd*
ls -l /dev/sg*
```

---

### Post by s6dalane on 2006-06-08
Usbview shows my flash disk correctly.
> kaarel@ubuntu:~$ ls -l /dev/sd*
brw-rw---- 1 root plugdev 8, 0 2006-06-08 17:28 /dev/sda
kaarel@ubuntu:~$ ls -l /dev/sg*
crw-rw---- 1 root root 21, 0 2006-06-08 17:28 /dev/sg0


---

### Post by ifokkema on 2006-06-08
[QUOTE=s6dalane]Usbview shows my flash disk correctly.[/QUOTE]
Ok... we're getting on a point where my knowledge on this is running out.
1) You've proven the disk is fine (works on Windows, used to work on Linux).
2) When the disk gets plugged in, it is appointed to /dev/sda
3) /dev/sda is created successfully, but the problem is that the partition table is messed up.

I got two more ideas, don't think I can help you after those, sorry.
Does this:
```
sudo fdisk /dev/sda
```return an error? If not, and you're in the fdisk shell, what happens if you press 'p' (print partition table)?

What's the output of:
```
lsmod
```
(is going to be a long list).

---

### Post by mlho on 2006-06-08
probably just not mounting properly.

what do you get with **mount**?

---

### Post by mlho on 2006-06-08
apologies for double post, but this thread may be useful:
[http://www.ubuntuforums.org/showthread.php?t=191963](http://www.ubuntuforums.org/showthread.php?t=191963)

---

### Post by Scunizi on 2006-06-10
Strange... When I plug my usb thumbdrive in I find it under /media/usbdisk.  I also find my 2 SATA drives there and CD rom.  There is nothing in /dev that referances the usbstick.  I have found that Dapper will only recognize one usbstick at a time unless you make a modification to the fstab.

---

### Post by ifokkema on 2006-06-11
[QUOTE=Scunizi]Strange... When I plug my usb thumbdrive in I find it under /media/usbdisk.  I also find my 2 SATA drives there and CD rom.  There is nothing in /dev that referances the usbstick.[/QUOTE]
The directories in /media are the mount points, where you can access the files on your drives. However, in /dev/, there will be device entries that represents the actual devices. USB drives are often /dev/sda, /dev/sdb or the like.

[QUOTE=Scunizi]I have found that Dapper will only recognize one usbstick at atime unless you make a modification to the fstab.[/QUOTE]
Really? That would suck. I think (not sure) I've once hooked both my MP3 player and my external USB hard drive in at the same time, but I was just charging the player at that time, no file transfers.

---

### Post by wislon on 2006-06-11
I've had some success with getting this to work again. I can't get the darn thing to mount automatically, even tho I ended up putting an entry in my fstab for it:

/dev/sda1       /media/USBFlash auto    auto,rw,user,umask=000 0 0

(based on the parameters I used for another VFAT hard disk that I have. I tried using the parameters for floppy0, but no go).

I created a 'USBFlash' folder in /media.

When I plug the device in, nothing happens until I go to a terminal, and type in sudo mount -a, at which point the drive appears on my desktop and I can do what I need with it. I have to manually unmount it with a 'sudo umount /dev/sda1' or 'sudo umount /media/USBFlash' as well (right clicking on it and selected 'Unmount' doesn't work (I'm not root). 

It gets me by, but is irritating, particularly since the damn thing used to mount (and dismount) just fine in Breezy!

---

### Post by ifokkema on 2006-06-11
[QUOTE=wislon]I've had some success with getting this to work again. I can't get the darn thing to mount automatically, even tho I ended up putting an entry in my fstab for it:

/dev/sda1       /media/USBFlash auto    auto,rw,user,umask=000 0 0

(based on the parameters I used for another VFAT hard disk that I have. I tried using the parameters for floppy0, but no go).

I created a 'USBFlash' folder in /media.

When I plug the device in, nothing happens until I go to a terminal, and type in sudo mount -a, at which point the drive appears on my desktop and I can do what I need with it. I have to manually unmount it with a 'sudo umount /dev/sda1' or 'sudo umount /media/USBFlash' as well (right clicking on it and selected 'Unmount' doesn't work (I'm not root). 

It gets me by, but is irritating, particularly since the damn thing used to mount (and dismount) just fine in Breezy![/QUOTE]

Hmm... so let me get this straight... it doesn't mount when you're logged in as your user and only mounts when running mount -a with sudo. This looks like a permissions thing. Could you check which groups you are in? Just run
```
groups
```
to see. Are you in the plugdev group? If not,
```
sudo adduser <your username> plugdev
```

Maybe that would help. Will require you to log out and in again.

---

### Post by Scunizi on 2006-06-11
I did have this problem in Breezy & Dapper Flight 5 and fixed it by modifing Fstab & mtab.  Here's the text of what I had posted in the Breezy forum months ago.  Hopefully it will help

```
I have FINALLY found the solution to this problem. It was really quite easy after I learned a little about how the file system work and how the system mounts things. You have to remember, the system needs a place holder/directory for each device that is mounted. That is accomplished in the media directory. Also everything you type below is case/CASE sensitive. I have 2 internal SATA drives and 1 IDE internal. I also wanted to be able to plug in my 3 USB devices at the same time and have them recognized with icons displayed on the Desktop. The 3 devices are... 1gig usb stick, 256m Cruzer Mini usb stick, 1 256m mp3 player (creative rhomba). I had to do a little editing of the fstab and media directory in order to get everything working correctly. In my case I already had sda1, sdb1,2,3,5, and hda1.

1> Go to the consol and type sudo gedit /etc/fstab (enter) - This will open up your editor. It will ask for your password. Enter it.

2> In fstab I added these three lines
/dev/sdc1 /media/usb1 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sdd1 /media/usb2 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sde1 /media/usb3 vfat rw,user,fmask=0111,dmask=0000 0 0

Now click save at the top of the screen.

The vfat referance above is for Fat32 formatted devices. Anything other than that and you'll have to change the formatting designator and possibly the fmask. dmask=0000 simply means that any user of the system can read and write to the device. If I remember correctly, if you substitute 0000 with 1000 only the logged user who created all this will be able to use the device. Someone may correct me here if I'm wrong. 

You'll notice all my usb referances are sdc sdd sde because I already have 2 SATA drives in the machine that are labeled sda & sdb respectively (the numbers represent the different partitions on the harddrives) I you don't have any SATA drives then you should designate sda, sdb, sdc respectively. I made three seperate entries in case I plug in all three devices at the same time otherwise it won't make any differance.


3> Go back to your consol and click "File" "Open Tab". You'll now see two tabs at the top of the consol. Click the second one and you should have an active prompt like "mgarrow@ubuntu:/$". Type cd /media (enter). This will take you to the media folder/directory.
4> Now type
sudo mkdir usb1 (enter) (maybe enter password)
sudo mkdir usb2 (enter) (maybe enter password)
sudo mkdir usb3 (enter) (maybe enter password)
These lines give a place for the drives/devices to attach to. You can use other names if you want. I just did it this way for simpicity.

Now you're done! Restart your machine then plug in one of your usb devices. I may take a moment but the system should recoginze it, mount it and place an icon for it on the Desktop...
```

The reason for the change in sd? labeling is because I have two SATA drives in my machine.  If you don't use SATA drives you could start the naming sequence with sda, sdb, sdc etc....

---

### Post by bartman on 2006-06-15
s6dalane: I hope you don't mind if i borrowed your thread.

I have a similar but more severe problem. My USB stick also is recognised but there is no device in /dev associated with it. Here's my relevant dmesg output :
```
[4308908.733000] usb 4-1: new high speed USB device using ehci_hcd and address 7[
4308910.456000] usb 4-1: configuration #1 chosen from 1 choice
[4308910.457000] scsi3 : SCSI emulation for USB Mass Storage devices
[4308910.458000] usb-storage: device found at 7
[4308910.458000] usb-storage: waiting for device to settle before scanning
[4308915.458000]   Vendor: CREATIVE  Model: MuVo V200         Rev: 0021
[4308915.458000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4308915.460000] usb-storage: device scan complete
```
No entries after that! This got broken since i updated from breezy to dapper. Icons of my own mounts appeared on the desktop before the upgrade but not anymore since. But I have rules in fstab for other filesystems i mount while the usb stick has no rule.

---

### Post by akechi on 2006-06-15
Im also having issues with my USB flash drive not being recognized. I ran dmesg | tail -n 20 and got this:

> dek-ops@dek-ops-laptop:~$ dmesg |tail -n 20
[60859.583767] APIC error on CPU0: 40(40)
[60894.186700] APIC error on CPU0: 40(40)
[60968.113470] APIC error on CPU0: 40(40)
[61007.588177] APIC error on CPU0: 40(40)
[61349.221594] APIC error on CPU0: 40(40)
[61466.466486] APIC error on CPU0: 40(40)
[61471.061307] APIC error on CPU0: 40(40)
[61673.300874] APIC error on CPU0: 40(40)
[61828.734467] APIC error on CPU0: 40(40)
[61865.461776] APIC error on CPU0: 40(40)
[61942.405364] APIC error on CPU0: 40(40)
[62354.558369] APIC error on CPU0: 40(40)
[62452.281990] APIC error on CPU0: 40(40)
[62515.598819] APIC error on CPU0: 40(40)
[62721.105541] APIC error on CPU0: 40(40)
[64656.840881] APIC error on CPU0: 40(40)
[64669.329677] APIC error on CPU0: 40(40)
[66394.301724] APIC error on CPU0: 40(40)
[67213.948093] usb 3-1: new high speed USB device using ehci_hcd and address 2
[67214.947514] ehci_hcd 0000:00:13.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.

Does anyone know what this output means?   I also am having major problems with my ACPI as you can see. Battery not being read correctly, notebook will not shutdown, reboot correctly.

---

### Post by bartman on 2006-06-16
It the shutdown/reboot procedure hangs at "Deconfiguring network interfaces" it's a known issue of the 2.6.15-23 kernel which comes with dapper.

---

### Post by akechi on 2006-06-16
When i click Reboot or Shutdown, it completes the process, then the screen goes blank after it says "Now rebooting or Now halting system". Then I have to manually power down the system and power it back up.
I have Ubuntu installed on a notebook:  Compaq Presario V2555us

Sorry for going off topic, please move if need be.

---

