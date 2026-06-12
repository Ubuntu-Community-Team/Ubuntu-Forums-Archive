---
title: "Problem with cd rom."
date: 2009-12-05
forum: General Help
---

### Post by malikge on 2009-12-05
Hello. 
I am using Ubuntu 8.10, After the installation my Cd Rom is not working. After inserting the cd when I click on CD-rom drive it gave error:

       Unable to mount media.
       There is probably no media in the drive.

Any help on that...
Thanks.

---

### Post by phillw on 2009-12-05
> **malikge said:**
> Hello. 
I am using Ubuntu 8.10, After the installation my Cd Rom is not working. After inserting the cd when I click on CD-rom drive it gave error:

       Unable to mount media.
       There is probably no media in the drive.

Any help on that...
Thanks.

This may sound daft, but ..... Have you tried a couple of different CD's ?
If you have, try cleaning the cd-rom drive with cd/dvd cleaning cd/dvd

Regards,

phill.

---

### Post by wojox on 2009-12-05
What does:

```
cat /etc/fstab
```

show ?

---

### Post by malikge on 2009-12-05
cat /etc/fstab shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6c0bf092-28de-427a-9e3e-06fa31e306d8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=40cd79e9-39d7-4c61-a50c-b64300a9ff74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by wojox on 2009-12-05
What happens when you put in a disk , open a terminal and issue:

```
sudo mount /dev/scd0
```

---

### Post by malikge on 2009-12-06
When I put in a disk nothing happens.
After entering sudo mount /dev/scd0 it asks for password and after that it gave :

                    mount: No medium found

Is there a problem with my Cd Rom?

---

### Post by malikge on 2009-12-06
Any help???

---

### Post by mkvnmtr on 2009-12-06
I am not going to be much help but mine is doing the same thing. After 8.10 it mounts in read only. It is that way also in 9.04 and 9.10. Fresh installs or upgrade. I have come to think it is my cd but the cleaning idea is a good one. If that does not work I think when I have tim I will try burning from the live cd or another distro. It reads fine just will not mountwith a blank disk.

---

### Post by Phantastes on 2010-01-11
Hi, I am having the same issue with 9.10. My CD drive is not listed under Places. It does not recognize any CDs. 
If I run, sudo nautilus and then go to Places - Computer, I see cdrom listed there. But clicking that only ejects the cd, it does not seem to be able to mount it. If I do not run nautilus as root I cannot even see the cdrom under Places - Computer.

Any help would be very welcome! I've tried switching the IDE cable but no luck. I've search all over for a solution but still no go. My fstab says:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c6e464db-8abe-4188-afb9-447f95c042c4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=af88164e-22d8-41fe-a58d-251a7be6de74 none            swap    sw              0       0
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

