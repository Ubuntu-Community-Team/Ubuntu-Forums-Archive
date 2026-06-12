---
title: "can't write to SD card"
date: 2010-01-05
forum: General Help
---

### Post by ray field on 2010-01-05
I keep an old 128MB SD card attached on a little drive to back up files on-the-fly but for some reason every other day it seems to revert to read=only.  I have checked the connection and the write-protect tab, everything seems to be okay, and yet every indication is it's write-protected.

here is the FSTAB entry

```
/dev/sdb1     /media/SD_BAK    vfat         rw,user,noauto 0 0  

```

I guess I could just leave it unmarked in FSTAB and it would automount correctly -- except I am a heavy user of an old DOS app and I think need to mount it persistently in order to use lredir.

---

### Post by MichealH on 2010-01-05
[LEFT]Can you read a file is it Read Only?
[/LEFT]

---

### Post by aeon.flux on 2010-01-05
did you check the hw lock button on a side of the card?

---

### Post by ray field on 2010-01-05
weird, I threw it in the Windows box, once it read okay, next time it came up corrupted.  so I picked out another 1GB card I had lying around, formatted it under Linux and have been using it for the last half hour without incident.  seems to be some flakiness with these things generally.

---

### Post by sur on 2010-02-04
I had a similar issue, finally got the solution that worked for me.

Follow these Steps to get the SD card automounted with write access

1) Create a directory 
```

cd /media
sudo mkdir sdcard

```

2) Change the owner of this directory to "you the user" like this 
```

sudo chown username:username sdcard

```

3) Get the UUID of your device..
connect the SD card to your computer and run this command
```

blkid

``` 
In my case, the output was
"/dev/mmcblk11p1: UUID="3035-3338" TYPE="vfat" "
So you see the UUID and the TYPE

4) Add the following as the last line in the file /etc/fstab
```

UUID=3035-3338 /media/disk     vfat    users,defaults,umask=007,gid=1000,uid=1000,noauto 0       0

```

NOTE: replace the UUID and the TYPE with what you get from the command "blkid"
and replace the uid and gid by your username's id... you can get it by using the command "id username"


5) Unmount the card, remove it, insert it again. It should work !

---

### Post by warfacegod on 2010-02-04
128 MB, I'm guessing would be rather old by now. It may simply be at the end of its life.



....Poor SD card. It served its master well. These are the times that we must reflect upon in our....


(Bugle playing Taps in the backgrounds.)

---

### Post by ray field on 2010-02-04
> **warfacegod said:**
> 128 MB, I'm guessing would be rather old by now. It may simply be at the end of its life.

yeah well what can I say, I'm a cheap *******.

good tip from sur -- I've managed to mount a (newer) card just with the card label without resorting to the UUID, but I'll keep that in mind the next time around.

---

