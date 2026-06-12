---
title: "deleted everything on external hd"
date: 2010-03-23
forum: General Help
---

### Post by rmedved on 2010-03-23
So the other day I was trying to repartition my external hard drive and somehow accidentally wiped the whole thing out. I tried using testdisk to restore it and I thought I did ok but know when I try to mount the hd i get the following error

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 10 in /etc/fstab is bad
mount: /dev/sdb1: can't read superblock

I don't know much about editing things like this so I downloaded storage device manager in hopes of automatically editing my fstab, which no says:

 system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda4
UUID=3bdd4555-0066-4b39-8129-1604516cd406  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda3
UUID=20392bfe-e56c-4388-8beb-5dcc706c9478  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
none /proc/bus/usb usbfs devgid= robbie,devmode=664 0 0# /etc/fstab:
/dev/sdb1                                  /media/sdb1    vfat         owner,users,user            0  0  

I'm really hoping that I didn't lose everything as my entire music and photo collection was on that drive... any help pleeease...

I am not a total noob but I don't know a whole lot either

---

### Post by Arand on 2010-03-24
If you have space enough, make a raw dd copy of the whole disk, loopmount this and do the operations there, as a safety measure

Things to ***try***:
[LIST]
[*]Uncomment the /dev/sdb1 line in your fstab and mount using:```
sudo mkdir /media/external && sudo mount /dev/sdb1 /media/external
```

[*]Use fsck.vfat with flags (-b possibly?) to use a different superblock, note that using fsck incorrectly might just as well trash the contents of the drive even more.

[*]Instead use photorec, which will hopefully get the files out (might be able to specify audio files), however they will be terribly disorganised
[/LIST]
- Arand

---

### Post by rmedved on 2010-03-25
I am running photorec now, it seems to be working, however it's  changing all the extensions on my m4a files to mp4, is there a way to change these all at once when it's done? Also, if I stop photorec do you know if it will pick up where it left off? Thanks for the help.

Cheers

---

