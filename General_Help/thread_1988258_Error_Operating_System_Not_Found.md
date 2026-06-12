---
title: "Error: Operating System Not Found"
date: 2012-05-27
forum: General Help
---

### Post by whathaveugot on 2012-05-27
Hi All,

I am currently having this problem of 'Operating System Not Found'. Recently I migrated my netbook from Ubuntu 10.04 to 12.04, and following that was experiencing system freeze/hang. Tried rebooting couple of times and after one of the reboots I got this message and its still the same. On booting up with live cd, my partitions are not showing up in 'Places'. So went for a dig and found this thread here: [http://ubuntuforums.org/showthread.php?t=1942310](http://ubuntuforums.org/showthread.php?t=1942310)

I tried both the commands and the following is the output:

[COLOR=Red]root@ubuntu:/home/ubuntu# e2fsck -C0 -p -f -v /dev/sda
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Could this be a zero-length partition?

root@ubuntu:/home/ubuntu# dumpe2fs /dev/sda | grep superblock
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Couldn't find valid filesystem superblock.
[/COLOR]
I am guessing my HDD has crashed but FYI its showing up in the BIOS. So is there any possible way that could help me out of this. I have also attached the results I got after running boot-info script and it does indicates that something is horribly wrong with the MBR. Any help would be highly appreciated.

Thanks a lot.

---

### Post by efflandt on 2012-05-27
First of all e2fsck and dumpe2fs are for a filesystem on a partition (like /dev/sda1), not an entire drive (/dev/sda).

The bad news is, your drive does not appear to respond at all.  I don't know how easy it is to access your drive, but either try reseating it to make sure that it is plugged in securely, or try using a USB enclosure to connect the drive to another computer to rule out a connection problem in your computer itself.

I was trying to help someone with a failing laptop drive which would no longer boot Windows.  I was only able to copy a few files to an external drive before the drive choked.  In a USB enclosure I could not even get an fdisk response for it.  A couple of weeks later on a whim, I connected the USB enclosure to my desktop PC and it automounted.  I was then able to copy the user's files except one directory that appeared to be related to a game.  Sometimes you just get lucky.

---

### Post by listerdl on 2012-05-27
Sorry cant help you too much BUT check our Rescatux - google it.

Its an amazing OS Grub Recovery that has never let me down.

Trust me I am constantly tinkering and breaking my machines due to being far too curious for my own good and I always use Rescatus to help me out.

Never fails!

---

### Post by idoitprone on 2012-05-27
check to see if there is bad sectors in the harddrive

here a link that tell you what to do
[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

I think you harddrive is borked

If you harrdrive is fine, then

use gparted and create a new mbr
then reinstall ubuntu

---

### Post by daslinkard on 2012-05-27
With the system hanging and freezing and now stating no OS, the HD is definitely gone.  Being that it is a netbook you're going to have to disassemble the entire machine to switch out the HD.  Of course though you could possibly run through a USB drive.

Definitely though your HD is gone.

---

### Post by whathaveugot on 2012-05-28
@idoitprone....i did had a go on Disk Utility initially and on running any of the three self-tests I got same message: "Not completed (a fatal error has occured)". So I guess I have to agree with @daslinkard that my disk is dead.

So now I'm gonna try Rescatux as per @listerdl and see if that could possibly help.....

> 
I was trying to help someone with a failing laptop drive which would no  longer boot Windows.  I was only able to copy a few files to an external  drive before the drive choked.  In a USB enclosure I could not even get  an fdisk response for it.  A couple of weeks later on a whim, I  connected the USB enclosure to my desktop PC and it automounted.  I was  then able to copy the user's files except one directory that appeared to  be related to a game.  Sometimes you just get lucky. 	


@efflandt...I've been thinking of doing this but am wondering whether I need to plug that USB enclosure in an Ubuntu box? Will Windows box help? Please could you clarify?

Thanks folks!

---

### Post by daslinkard on 2012-05-28
whathaveugot,

I have done data recovery utilizing Windows XP, Vista, Windows 7 and Ubuntu.  I have found I have been able to read more failing/failed HD's with Linux than I have any Windows OS.

I think your best bet here is getting your HD out, putting it in a HD enclosure, and plugging it in to another machine to see what happens....if it will even read?  Good luck!

---

### Post by whathaveugot on 2012-06-03
> **listerdl said:**
> Sorry cant help you too much BUT check our Rescatux - google it.

Its an amazing OS Grub Recovery that has never let me down.

Trust me I am constantly tinkering and breaking my machines due to being far too curious for my own good and I always use Rescatus to help me out.

Never fails!

I downloaded the Rescatux ISO image and tried to dump it in usb using 'dd' (via Windows) but when I fired up the command to dump-

dd --progress bs=1M if=d:\rescatux.iso of=\\?\Device\Harddisk2

I got this: "Error native opening file". FYI, the "--size" option didn't worked saying 'unknown command -size'

Same thing repeated when I tried Super Grub Disk 2 ISO. Can anybody tell me what went wrong? 

Cheers.

---

