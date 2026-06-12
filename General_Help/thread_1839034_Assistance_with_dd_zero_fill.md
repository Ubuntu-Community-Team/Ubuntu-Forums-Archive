---
title: "Assistance with dd zero fill"
date: 2011-09-04
forum: General Help
---

### Post by Petrovic on 2011-09-04
I used dd to zero fill with the command **dd if=/dev/zero of=/dev/sdh bs=4k conv=notrunc** to overwrite a drive which had been filled with windows based virus'(story below). After it completed, I checked to see if it had woked with the command **dd if=/dev/sdh | hexdump -C | grep [^00]**
 Came up with all sorts of hash figures:
001000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
001000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
001000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|

There were pages of 'em. I took this to mean that the data hadn't been zeroed out on the first pass for whatever reason. Noticed a couple of folders were still present on the drive, tho lacking contents, so deleted them with nautilus then ran a second pass and it came back with three lines:

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00|................|
*
950a60000

I'm asking if this is the marker of a successful fill, or is there still a trace left behind with that 950a60000. Would above command zero fill the MBR should the virus have planted itself there, which I'm pretty sure it has, or is a separate command required?
I also noticed that gparted wouldn't touch the drive after it had been filled, until I removed and remounted. But that's of no consequence. 
Thanks for any assistance. 

Story:
I have a mates laptop for some virus removal. Ran Natty from a usb stick, poked around his drive a bit, marked the info to be backed up and went to sleep. Booted laptop, but now windows won't load, Natty usb isn't recognised as a boot device, and machine starts looking for DHCP server! So I pulled the hdd plugged it into my machine via usb caddy, backed up data then formatted and removed the partition. Re-partition and replace in laptop. Installed windows, then load into windows for first time. Install Avast from usb, run32.dll error. Reboot now leads to eternal windows boot loop. Then comes dd.
So, I decided to zero fill.

---

### Post by gordintoronto on 2011-09-05
I haven't used dd, but /dev/sdh seems a bit odd. Is there just one partition on the drive?

(sudo fdisk -l)

---

### Post by Petrovic on 2011-09-05
Yeah, it was a single 40gb partition. It's /sdh because it was plugged in via usb caddy and mounted as such.

---

### Post by dcstar on 2011-09-05
> **Petrovic said:**
> Yeah, it was a single 40gb partition. It's /sdh because it was plugged in via usb caddy and mounted as such.

Just use **gparted** to create a new Partition Table on the device, that will wipe any Windows rubbish.

---

### Post by jarotek on 2011-09-05
@dcstar: that will wipe the old partition table in the Master Boot Record, but will not overwrite the actual data on the partition.

---

### Post by Petrovic on 2011-09-07
Sorry about the delay in replying, been having some family issues. 

> **dcstar said:**
> Just use **gparted** to create a new Partition Table on the device, that will wipe any Windows rubbish.

Removing and replacing the partition was one of the first things I did. Even said so in my first post. My first train process after anti-virus failure is format and repartition. dd was the next logical step after that failed. 

Ok, answered my own question. Found this on another forum...

> Linux-based solution

If you can still somehow fire up Linux - say, via Tom's Root-Boot floppy - you can simply invoke "dd", like so:

dd if=/dev/zero of=/dev/hda bs=512 count=1

Yep, that's it. That MBR is gone. Obviously, you have to be root to do this. 

Seems I had it right, so might run a few more passes and see what I can dig up. 

Thanks helpful folks.

---

### Post by dcstar on 2011-09-08
> **jarotek said:**
> @dcstar: that will wipe the old partition table in the Master Boot Record, but will not overwrite the actual data on the partition.

Which won't matter as soon as you create a **new** partition and install/write to it as that will overwrite the existing data.

Doing that will solve any "Windows virus" issue which was the OP's original problem, all else is irrelevant.

---

