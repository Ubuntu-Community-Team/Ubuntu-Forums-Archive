---
title: "dd (Data Description)"
date: 2011-08-27
forum: General Help
---

### Post by Ceiber Boy on 2011-08-27
when imaging a HDD with dd, dose it also copy the maintenance cylinders of the disk or those with negative numbers?

If it dose would that mean that the clone disk (assuming same capacity and sector size) would be undetectability / identically the same to the operating system?

Many Thanks

---

### Post by sbraz on 2011-08-27
the first bytes **dd** reads are related to the MBR (dd if=/dev/*dX of=/dev/*dY bs=446 count=1) so my guess is that those cylinders aren't copied.

i'm interested about those hidden sectors though, i've never played with them. what's in there? :)

---

### Post by Ceiber Boy on 2011-08-28
> **sbraz said:**
> the first bytes **dd** reads are related to the MBR (dd if=/dev/*dX of=/dev/*dY bs=446 count=1) so my guess is that those cylinders aren't copied.

i'm interested about those hidden sectors though, i've never played with them. what's in there? :)

I first about system area here:

[http://www.youtube.com/watch?v=vCapEFNZAJ0](http://www.youtube.com/watch?v=vCapEFNZAJ0)

skip forward to 5mins into the video, hope you find it interesting.

---

### Post by sbraz on 2011-08-28
> **Ceiber Boy said:**
> I first about system area here:

[http://www.youtube.com/watch?v=vCapEFNZAJ0](http://www.youtube.com/watch?v=vCapEFNZAJ0)

skip forward to 5mins into the video, hope you find it interesting.

yes it was interesting. i thought they used something like an eeprom for storing that kind of data but now i admit that it makes a lot more sense logically and economically to have a reserved area on the platters.

now: may i ask why are you interested in copying those areas to another drive? btw i think it could easily brick the target drive but maybe that's not relevant to you. :)

---

### Post by bakegoodz on 2011-08-28
Not sure what you mean by "maintenance cylinders" dd will copy all user accessible sectors of a drive, or rather all sectors that the drive's firmware makes available for use. If you need access to hidden sectors you need really expensive hardware and software that Data Recovery industry uses. When a drive is copied with dd it copies the bootloader, partition table, partition space, and if partition(s) don't take up all drive space unpartitioned area too. So a dd copy would exactly look the same to the operating system, same partition size unless you expand the partition with tools like Gparted.

dd is a legacy tool, not the best tool for most tasks. dd variants like dc3dd and ddrescue are used for forensics and data-recovery. Cloning tools like Clonezila and Partimage are much faster and practical for copying drives.

---

### Post by Ceiber Boy on 2011-08-28
> **sbraz said:**
> yes it was interesting. i thought they used something like an eeprom for storing that kind of data but now i admit that it makes a lot more sense logically and economically to have a reserved area on the platters.

now: may i ask why are you interested in copying those areas to another drive? btw i think it could easily brick the target drive but maybe that's not relevant to you. :)

I'm interested because i've never had to restore a cloned system onto a HDD that was not the source of the clone. If the scenario did arise where I had to put a clone onto a HDD that was not the source (due to the source malfunctioning), would the OS be able to tell (assuming same capacity and sector size) that it had woken up on a different HDD?

I hope that's clear.

---

### Post by sbraz on 2011-08-28
i've cloned a 320gb 5400rpm 8mb cache hitachi drive to a western digital 320gb 7200rpm 16mb cache.

i'm typing from it. ;)

---

### Post by sbraz on 2011-08-28
oh and if there's a difference in size.

--target disk is smaller than source: you have to resize/move the partitions accordingly BEFORE starting the clone. after cloning resize to fill up the space. if you are restoring from an image file you must first restore it to a larger drive, shrink partitions, then clone that drive. to avoid this issue you can resize the partitions prior to creating the image.

--target disk is larger than source: after cloning resize to fill up the space.

---

