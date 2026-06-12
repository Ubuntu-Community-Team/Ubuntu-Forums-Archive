---
title: "external hard drive saying read only please help!!"
date: 2009-07-01
forum: General Help
---

### Post by jcm1107 on 2009-07-01
I don't know if it was something I did or something my five year old could have clicked when I turned my back, but my external hard drive that was working great just decided to say read only when I try to put a folder in it. How can I change this?

---

### Post by tvtech on 2009-07-01
you can change this in several ways.  

the easiest is to open a terminal 

type 

```
username@localhost:~$gksu nautilus
```

you will be prompted to enter your administrative password. 

navigate to your external hard drive

I'll assume it automounts under media

right click it and select [COLOR="Red"]properties.[/COLOR]
change your permissions here then exit out of nautilus and terminal.  You should be all good to go.

This is way easier than changing permissions from the command line.

hope that helps!

---

### Post by merlinus on 2009-07-01
You can try changing the permissions.

Alt+F2
gksu nautlilus

navigate to the mountpoint, rightclick. select properties and then permissions.

---

### Post by jcm1107 on 2009-07-01
thanks for the rapid help!!! I restarted my computer and for some reason that fixed it but I typed into a terminal what tvtech said to do and I think that would of fixed it.

---

### Post by npm1 on 2009-07-02
Hi i'm user npm1----new to this forum
recently i've just installed juanty jackalope (9.04 release of ubuntu)...doing so i decided to use my external hard drive----so one day with everything plugged in including my external hard drive.. i switched my computer on....everything loaded as expected but then after logging in a window loaded asking me to type my root password in for that external hard drive under neath that field was two radio buttons one "for this session only" and another "every time" i can't extactly how this window looked but the computer obviously thought i had added an internal Hard drive

---

### Post by npm1 on 2009-07-02
the help is changing the permissions as i have already tried the nuatilius function you've explained and options including the one with the sudo instead of the gksu-----------------
i've even attepted to edit my fstab in the etc but when lloading the file i didn't understand or now which line to change..............................

---

### Post by npm1 on 2009-07-02
my fstab is as follows: 
[I]

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8a61fafc-a2fd-4afa-bffc-a14c9d623eda /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca1126e6-a476-4ac1-b0c5-620091587f3d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/I]

the question is which line do i edit ---i.e. to change permissions

by the way my external hard drive is 650gb,western digital connected through usb and is a FAT32 filesystem.........i do not want to reformat or loose dataon it

---

