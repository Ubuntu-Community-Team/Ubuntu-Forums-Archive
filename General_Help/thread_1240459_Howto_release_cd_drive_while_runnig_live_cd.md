---
title: "Howto release cd drive while runnig live cd"
date: 2009-08-14
forum: General Help
---

### Post by krotus on 2009-08-14
Ok, may sound stupid at first. But is it possible? I dont need whole system (X) up, i want just to dd cdrom image out to ntfs hard drive partition. Thx.

---

### Post by Ocxic on 2009-08-14
you;ll need to copy the cd into an .iso.

dd if=/dev/cdrom of=/livecd.iso

then mount the iso:

sudo mount /livecd.iso /cdrom -o loop

then unmount the cdrom drive 

sudo umount /dev/cdrom

now /dev/cdrom my not be the location of you cd drive on your computer, run "mount" to see what /cdrom is mounted with and replace /dev/cdrom with what you have. (Do Not "umount /cdrom" or your system may stop running and you'll have to reboot)

your gonna need at least 1.5GB of memory(RAM) to do this, as the live cd runs in memory, 
  alternatively you could make a bootable usb stick and use that, and your cdrom drive will be free.

---

