---
title: "Error message when attempting for format disk using gparted"
date: 2011-05-15
forum: General Help
---

### Post by ClientAlive on 2011-05-15
Hi,

I'm trying to re-format an external usb hard drive in ext4 using gparted. I selected:

Device > Create Partition Table

Then, in the window that pops up, selected:

"msdos" in the drop down list

Then:

Partition > New

Then selected "ext4" and "/"

Then:

Edit > Apply All Operations


I get the error message I've attached (first one the name ends "_01")

Then I tried to run it again the same way. That error message attached (mane ends "_02")

Can anyone help? It is a 232.88 GB drive. Could that be the issue?

Thanks.

---

### Post by doas777 on 2011-05-15
unmount it first with:
```
sudo umount /dev/sdb1
```

or right click the disk in nautilus and select "unmount"

---

### Post by ClientAlive on 2011-05-16
> **doas777 said:**
> unmount it first with:
```
sudo umount /dev/sdb1
```

or right click the disk in nautilus and select "unmount"


I'm not sure I understand what you are getting at. This is the disk I am trying to format. The problem isn't mounting or unmounting. it's formatting the thing.

---

### Post by debd on 2011-05-16
you need to unmount a partition before you can perform any operation on it.

---

### Post by ClientAlive on 2011-05-17
> **debd said:**
> you need to unmount a partition before you can perform any operation on it.


I ended up getting it worked out. I just had a hard time with this idea you're talking about. It just didn't make sense to me how something can be that way. I learned, though, that there's a difference between unmounting something and unplugging it. Linux still knows its there - weird as that is. Linux is just weird to me. I'm sure it's going to take a lot of getting used to.

Thanks for the help guys.

---

### Post by debd on 2011-05-17
>  I learned, though, that there's a difference between unmounting something and unplugging it.
:D nice that you finally got it.

---

### Post by doas777 on 2011-05-17
> **ClientAlive said:**
> I ended up getting it worked out. I just had a hard time with this idea you're talking about. It just didn't make sense to me how something can be that way. I learned, though, that there's a difference between unmounting something and unplugging it. Linux still knows its there - weird as that is. Linux is just weird to me. I'm sure it's going to take a lot of getting used to.

Thanks for the help guys.
the same concept comes into play when you are checking your disks for errors. fsck can't run on a disk that is mounted.

the issue with mounting, is that while a disk is mounted, there is nothing an application can do to prevent other apps from reading off or writing to that disk. if your disk checker moves a block, and a running application was trying to read or write that block, then disaster ensues. unmounting the drive helps to ensure that only one applicaiton has exclusive access to the drive.

cheers!

---

### Post by ClientAlive on 2011-05-17
> **doas777 said:**
> the same concept comes into play when you are checking your disks for errors. fsck can't run on a disk that is mounted.

the issue with mounting, is that while a disk is mounted, there is nothing an application can do to prevent other apps from reading off or writing to that disk. if your disk checker moves a block, and a running application was trying to read or write that block, then disaster ensues. unmounting the drive helps to ensure that only one applicaiton has exclusive access to the drive.

cheers!


Cheers man!

Wouldn't it be cool if someone wrote some script or something that changed that? That would be a cool feature to give to the community.

I'm not sure you could get away with this with the local disk but I bet you could with an external disk - just write something that identifies any other app trying to access the drive and tell it to sleep then when what you were running on it is done, wake it up and let it continue. You could probably do it with something already built into the sytem. Possible utilize something in the kernel even. Then you would just have to make a call to that thing in the kernel and have it run what you want it to? I don't know, something like that - Huh?

:D

---

