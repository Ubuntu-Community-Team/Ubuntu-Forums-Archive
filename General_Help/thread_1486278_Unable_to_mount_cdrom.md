---
title: "Unable to mount cdrom"
date: 2010-05-17
forum: General Help
---

### Post by doetinchem on 2010-05-17
Dear All,
I have a problem to mount my cdrom as a regular user. After inserting a cd, I receive this error message:

"Error mounting: mount exited with exit code 1: helper failed with:
mount: must be superuser to use mount"

After mounting the cdrom as superuser with

"sudo mount /media/cdrom"

I can access the cd also as regular user. This behavior is inconvenient and I would like to be able to mount the cdrom as user. Therefore I checked my /etc/fstab which looks like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=380d0a68-274e-48b0-bf67-6cdba5dde734 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0acd2b92-a619-4d62-9f24-545a66df00cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0

Honestly, I do not have the experience to tell if this should be fine or not. Do you have any advice for me to fix this problem? I am running Ubuntu 9.10 with a 2.6.32-02063209-generic kernel.

Thank you very much,
Philip

---

### Post by dcstar on 2010-05-18
> **doetinchem said:**
> Dear All,
I have a problem to mount my cdrom as a regular user. After inserting a cd, I receive this error message:

"Error mounting: mount exited with exit code 1: helper failed with:
mount: must be superuser to use mount"

After mounting the cdrom as superuser with

"sudo mount /media/cdrom"

I can access the cd also as regular user. This behavior is inconvenient and I would like to be able to mount the cdrom as user. Therefore I checked my /etc/fstab which looks like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=380d0a68-274e-48b0-bf67-6cdba5dde734 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0acd2b92-a619-4d62-9f24-545a66df00cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0

Honestly, I do not have the experience to tell if this should be fine or not. Do you have any advice for me to fix this problem? I am running Ubuntu 9.10 with a 2.6.32-02063209-generic kernel.

Thank you very much,
Philip

Try:

/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0

---

### Post by doetinchem on 2010-05-18
No, it is not working. Thank you anyway.
Can I try something else?

---

### Post by alejandro.mc on 2010-05-25
This issue is starting to p.... me off..

---

### Post by doetinchem on 2010-05-25
Could you please explain me why?
Is it because the mounting is not working or because the question keeps coming back so often and you know an easy solution?
Please educate me.

---

### Post by alejandro.mc on 2010-05-25
Because I can't store my mkvs in dvds, I can't see my dvd drive, I have a 640 gb drive and only a 1 gb free..

I can't understand why after so many years of development sth as simple as the cd/dvd drive is not working properly..

Cheers!

---

### Post by houseworkshy on 2010-05-25
Not sure how to solve the cd/dvd problem on the hard drive but I know of a near sure fire solution to alejandros' storage problem.  This [http://www.puppylinux.com/](http://www.puppylinux.com/)
Try booting from it then loading it to ram.  It can also boot from a usb.  As I guess you can't burn iso's to disk from Ubuntu at the moment that may be the best way to go.  If it works I'd be inclined to make the first cd Puppy 5 as IMO it deserves a place on any pcs' cd rack.  Saved my bacon many a time.  
If you do have a disc drive hardware problem that won't help much but at least you'd know it was a hard rather than a soft problem.
if you don't have a hardware failure then you can even boot it from the unfindable by Ubuntu drive as it bypasses any error in you hd installation. Once in remove the disk and you can use the cd/dvd burner in puppy to backup to dvd/cd and clear some space.

---

