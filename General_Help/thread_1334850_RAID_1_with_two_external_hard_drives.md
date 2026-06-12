---
title: "RAID 1 with two external hard drives"
date: 2009-11-22
forum: General Help
---

### Post by coolnfunky_raj on 2009-11-22
Hi 

I have a Dell 1501 laptop running Ubuntu server 9.04. If i buy 2 external hard drives, can i setup a RAID 1 system so that when ever i copy files to one of the two drives, the same data is copied to the other as well automatically?

Thanks in advance

---

### Post by whoop on 2009-11-22
As long as your not using usb to connect the drives (that's not smart):D
Also, with raid1, you do not copy to one of the two drives, you will only see one drive.

---

### Post by coolnfunky_raj on 2009-11-22
HI whoop

It does not matter to me if i see one disk or two. I want the disks to be mirrored automatically without me copying them two times. Can this be done with ubuntu or do i have to buy the expensive RAID hard drives?

if not USB, how else should i connect 2 drives to a laptop?

---

### Post by Snow986 on 2009-11-22
eSATA or firewire would definitely be preferred to USB, but if USB is all you got then not a whole lot you can do!

---

### Post by whoop on 2009-11-22
> **coolnfunky_raj said:**
> HI whoop

It does not matter to me if i see one disk or two. I want the disks to be mirrored automatically without me copying them two times. Can this be done with ubuntu or do i have to buy the expensive RAID hard drives?

if not USB, how else should i connect 2 drives to a laptop?

Well ubuntu supports software raid (I use it myself on some machines). I have never tried to connect to identical usb drives as a software raid array. Technically it could work, but performance will probably suck, and it could get irritating if the drives don't map to the exact same folders when mounted.
I only connected software raid arrays via SATA ports (but that probably not an option for a laptop).

---

### Post by coolnfunky_raj on 2009-11-23
> **whoop said:**
> Well ubuntu supports software raid (I use it myself on some machines). I have never tried to connect to identical usb drives as a software raid array. Technically it could work, but performance will probably suck, and it could get irritating if the drives don't map to the exact same folders when mounted.
I only connected software raid arrays via SATA ports (but that probably not an option for a laptop).

Did you use mdadm for this? 

If I say, 
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/xxx1 /dev/xxx2 
where xxx1 and xxx2 are the two external drives, and if i copy paste files/directories in one drive, will it automatically be mirrored to the other?

---

### Post by whoop on 2009-11-24
> **coolnfunky_raj said:**
> Did you use mdadm for this? 

If I say, 
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/xxx1 /dev/xxx2 
where xxx1 and xxx2 are the two external drives, and if i copy paste files/directories in one drive, will it automatically be mirrored to the other?

Yeah, just about... You have to mount md0 (after you created it with mdadm) to a directory and read/write through that directory.
As an example I mounted md0 to /home in /etc/fstab:
```

/dev/md0        /home ext3 nodev,nosuid,relatime 0 2

```

Here's a complete thread on me messing with raid mdadm and the likes:
[http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328)
Maybe there's some useful stuff for you on there (although it's not with usb devices :D)....

---

