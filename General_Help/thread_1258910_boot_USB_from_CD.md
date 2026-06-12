---
title: "boot USB from CD"
date: 2009-09-05
forum: General Help
---

### Post by skalra63 on 2009-09-05
Hey guys, just wondering if you could help. 

I have used the live cd (9.04) to install Ubuntu. I have used the install program to install it to a 4GB USB flash drive (also tried it on an 8GB). I have it formatted to ext2. When I try to boot from the USB it runs through about 11 seconds of the boot but then hangs on the following:

sd 2:0:0:0: [sda] Attached SCSI removable disk
sd 2:0:0:0: Attcahed scsi generic sg1 type 0

After this it seems to hang and then it comes up with BusyBox.

It appears that the USB installation actually works. when booting directly from the usb from my laptop (not virtual machine), Ubuntu loads, which to me indicates that the issue is with the USBCD ISO I made from the following web page [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB).
 
Anyone able to assist? Basically I am trying to help someone use their laptop with a failed ide connector on the motherboard (whole board will need to be replaced). I was hoping that they could use Ubuntu and boot from USB but their laptop does not support booting from USB....which is why i need this cd to work.

Any help would be greatly apprehciated.


                                                                                                  
                                                                                                                                                                                    
                        skalra63                   [View Public Profile]("http://ubuntuforums.org/member.php?u=906409")                   [Send a private message to skalra63]("http://ubuntuforums.org/private.php?do=newpm&u=906409")                             [Find More Posts by skalra63]("http://ubuntuforums.org/search.php?do=finduser&u=906409")

---

### Post by phillw on 2009-09-05
Would it not be simpler just to use the standard Ubuntu CD, and select the "Live" option ?

As the machine doesn't support booting from a USB Drive - You're going to need to do boot from a CD

If, as you say both the hard-drive & CD-Drive are out of operation and you cannot boot from USB, I'm afraid I am 
a bit stuck.

If it is just to get the information off the existing hard drive, you can get a usb carrier for the 2.5" drives to allow
then to plug into USB on a working computer.

Phill.

---

### Post by VipX1 on 2009-09-05
I have it working, 9.04 also on a 8GB USB. The USB is FAT32 and is an active partition. Try an active FAT32 format. A boot partition must always be active.

---

### Post by skalra63 on 2009-09-05
thanks for the replies.

The reason that I am trying to get this to work is because the laptop#s owner cannot afford to get the laptop repaired or buy a new one.

The cd drive works fine, it looks like it is just the one ide connector (to the hard drive) that has gone.

I was hoping to get the cd working so that they will then be able to use the dvd drive after loading Ubuntu. If they were to use the live cd, they wouldnt be able to do this.

Hi Vipx1,

I don't think that the issue is the installation on the USB itself as i can boot from the USB without issue (my bios will allow me to do this).

I think it is the boot cd ( the one on the link that starts the USB disk) that isnt working correctly but I am a novice and so am not sure what the actual issue is.

---

### Post by skalra63 on 2009-09-06
Anyone else with any ideas?

---

### Post by scion xd on 2009-09-06
Did you try to use a program called uNEtbootin, if so the you neen to format hte flash drive to FAT32 with Partition Manger. I just installed my ubuntu on lap top with a flash drive, because i was to cheap to use a CD.

---

### Post by skalra63 on 2009-09-06
hi scion xd

I have not tried that program. The issue does not appear to be the Ubuntu installtion as it works fine on a pc that is able to boot from usb.

The problem is that the person I am trying to help does not have the option to boot from USB in the BIOS. That's why I am using this CD. Does this program allow the USB to boot even though the BIOS does not allow it?

---

### Post by scion xd on 2009-09-06
NOi dont  think so, because i had to configure bios to boot from USB.

---

### Post by P4man on 2009-09-06
I know what you're trying to do should be possible (never tried it myself), but why don't you install grub on the internal drive, and use that to dual boot ? Is it because grub stage 1 is not able to read the USB drive without bios support ? Just asking..

Other than that, perhaps this is easier:

[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html)

---

### Post by skalra63 on 2009-09-06
Hi P4Man,

The reason I don't want to do it that way is because I beleive there is an issue with the IO channel on the IDE that connects to the disk.

The disk works fine in other laptops, the cd drive works all the time so i think its just that channel.

So I am trying to find a way of being able to use the laptop without the internal hard drive.

In regards to the GRUB cd, how would it boot the USB drive?

---

### Post by P4man on 2009-09-06
hmmm.. good question. I thought grub would be able to read USB devices by itself, but it does seem it can't, so you'll need to put the kernel on that cd as you where trying.

Anyway, you where following this howto:
[https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD](https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD)

right?
Did you have a livecd inserted when you tried that copy command? You need one for this.

---

### Post by skalra63 on 2009-09-06
Hey P4Man!

Yes, I am using the LiveCD. I did try doing it from an installation when the LiveCD ones wern't working but that wouldn't find the casper files.

---

### Post by mike555 on 2009-09-06
There are live cd versions of boot managers that let you boot a USB ...... you might try here , they have in the download two versions of .iso's ,one lets you burn it to a cd and use live (no install) to start any partition including USB ...... [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by skalra63 on 2009-09-06
Hi Mike,

Thanks for the link. I have skimmed the page and found it interesting though it looks like if i want to boot a USB using a cd, it will require the user to enter commands on boot.

I would prefer if it was seamless like the boot disk is supposed to be.

---

