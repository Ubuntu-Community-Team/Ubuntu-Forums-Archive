---
title: "no devices on konqueror &gt; services &gt; storage devices"
date: 2006-04-21
forum: General Help
---

### Post by urrestieta on 2006-04-21
hi

i dont get any devices but the floppy drive on Konqueror > services > storage devices (i am translating from spanish "dispositivos de almacenamiento" so i am not sure that this is the exact name of this option)

I can mount the devices manually and the fstab file hasnt changed so i think i might have stopped some daemon on System settings > System services. I was tunning the system yesterday and i set some daemons off there. Later this problem started. I am not sure if this would be the reason because i did many other things to the system but this sounds like the most likely to be the cause.

anyone can help fixing this ? I really like this because i hate having to type mount /blah /blah -blah ... everytime

thanks!

---

### Post by urrestieta on 2006-04-21
more details : usb drive is also displayed and auto-mounted properly when connected to the usb port.

---

### Post by GoldBuggie on 2006-04-21
i'm guessing you are having the problem of the storage media not showing in kde and that is helped by adding hal to some grups
I have hal in
```
groups hal
hal : hal disk cdrom floppy plugdev
```
For you I would guess the disk and plugdev need to be added so do
```
sudo adduser hal disk 
```
and
```
sudo adduser hal plugdev
```
restart and it should be solved

---

### Post by urrestieta on 2006-04-21
bingo!
but i wonder what did i do to cause the problem.
many thanks!

---

### Post by urrestieta on 2006-04-25
Funny enough I am still missing one drive. This is /dev/hdc1 that mounts on /mnt/data
the content of fstab for this drive is
/dev/hdc1	/mnt/data	vfat	rw,users,noauto	0	0
exactly same parameters for all the other drives

I thought that this might be because when i did 
sudo adduser hal disk 
sudo adduser hal hotplug

that drive was not properly included in the fstab (been messing around testing)

so I tried
sudo deluser hal disk 
sudo deluser hal hotplug

and include the right stuff into the fstab, then again
sudo adduser hal disk 
sudo adduser hal hotplug

nothing changed. I am triying to find out about this hal system and see if there is a way to add a new drive or similar

any ideas? thanks

---

### Post by ColonelOops on 2006-04-26
Great!
I was always wondering why the disk drives don't show up in system:/media.
Thanks guys!

Col. Oops

---

### Post by adbot asdakjsfhs on 2008-07-23
Hey, shouldn't the user be in these groups rather than hald username? What about security!?

---

