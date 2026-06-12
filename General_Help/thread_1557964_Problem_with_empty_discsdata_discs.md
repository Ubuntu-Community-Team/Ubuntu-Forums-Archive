---
title: "Problem with empty discs/data discs"
date: 2010-08-21
forum: General Help
---

### Post by Quackers on 2010-08-21
When I insert a movie on dvd, it mounts and gives me options to choose a dvd player. The cd/dvd/bluray icon in Places shows a dvd in the drive. I can eject the dvd from this screen too.
When I load a data disc or an empty dvd the cd/dvd drive disappears from Places and the drive spools down. It just refuses to mount at all. Please see screenshots of Places.

---

### Post by AlphaLexman on 2010-08-21
Let's take a look at your 'fstab' ->
```
cat /etc/fstab
```
and post the results.

---

### Post by Quackers on 2010-08-21
Here we go 

```
mike@mike-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=fcd9dfad-cafb-45aa-a2ef-c604a194808a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=25e2ec92-c462-4ef8-a538-36116ac8787c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a65962f1-18e9-4aeb-934e-fa2ecdeaad65 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=0615874e-e425-412e-81b5-4a1467f615cc none            swap    sw              0       0

```

---

### Post by AlphaLexman on 2010-08-21
I have this line in my 'fstab' ->
```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```You'll want to add it to your [ /etc/fstab ] You may need to change '/dev/scd1' to /dev/scd0' if your laptop has only one optical drive. Enter the command & password when asked:
```
gksudo gedit /etc/fstab
```from a terminal.

Copy my code, paste to gedit and save.

Eject the CD tray and put the blank CD back in.

Also, you may have to logout and login.

---

### Post by Quackers on 2010-08-21
Thanks, I'll try that now.
Just out of interest, having installed Ubuntu with the dvd drive, and being able to play CD's and DVD's from within Ubuntu, and the cd/dvd drive appearing in Places, it seems strange that I now need to tell Ubuntu that the CD/DVD drive exists!

---

### Post by Quackers on 2010-08-21
Just the same.
If I go to Places > Computer the cd/dvd drive shows up. When I put in a blank dvd and the drive spools up the cd/dvd drive completely disappears from Places > computer and no options appear for what to do with the dvd.

---

### Post by Rubi1200 on 2010-08-21
As above for the steps:
```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```Maybe try replacing scd1 with scd0 and see what happens?

---

### Post by Quackers on 2010-08-21
I tried scd0 first but had no joy. When I tried scd1 a new entry "cdromo" appears in Places > Computer and when I try to double click on it I get this pop up

---

### Post by AlphaLexman on 2010-08-21
In fstab change /media/cdrom0 to /media/cdrom

No number, zero or one after cdrom.

---

### Post by Rubi1200 on 2010-08-21
Hmm...

I don't know if this will help, but take a look here:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

EDIT: didn't see previous post as I submitted this.

---

### Post by Quackers on 2010-08-21
No good, I'm afraid. As soon as the drive spools up the cd/dvd drive disappears from Places > Computer. It's like it unmounts the whole drive from the system.
This is from lshw output

  *-cdrom
                description: DVD-RAM writer
                product: BD-MLT UJ-220S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

---

### Post by AlphaLexman on 2010-08-21
Can we gather that your optical drive is a:

[LIST]
[*]blu-ray player
[*]dvd-burner/player
[*]cd-burner/player
[/LIST]
The 'blank' discs you are trying to mount, are they:

[LIST]
[*]cd-r
[*]cd-rw
[*]dvd-r
[*]dvd-rw
[/LIST]
Some brands of discs are incompatible with certain drives. You may need to try different brands of blank media.

---

### Post by Quackers on 2010-08-21
My drive plays and records everything, + or -, bluray, dual layer.
My earlier eforts involved a data disc of the dvd+rw type.
I have tried again with a cd-rw and although the drive stays mounted in Places, when I double-click on the drive I get this

---

### Post by AlphaLexman on 2010-08-21
If you have one, try a non 'rw' disc, a cd-r or dvd-r and see if it mounts. There is usually a sub-format that allows read-write to an optical drive, if windows has seen this disc before linux has, it might be un-[mount, read]able.

---

### Post by Quackers on 2010-08-21
Ok, that makes sense. I'll try a R disc.
We are definitely on the right track though, because now the drive stays mounted in Places AND the eject button now works. The eject button never worked before :-)
I'll get back to you in a mo.

---

### Post by Quackers on 2010-08-21
I just tried a CD-R and a DVD + R and both have the same problem. The disc type is recognised perfectly in Places, and the eject button works, but it has an error mountint the disc.
Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/cdrom does not exist

---

### Post by AlphaLexman on 2010-08-21
Post the output of ->
```
ls -l /media/
```Normally '/dev/cdrom' is a soft link to an actual device, such as /dev/cdrom0 or /dev/scd0
And /media/cdrom is the 'mount point' for the /dev/cdrom.

Post the output of ->
```
mount
```just to eliminate some things.

---

### Post by Quackers on 2010-08-21
They're all working now. I've called the device /dev/cdrom but most important of all, I've deleted the space between the /dev/cdrom and /media/cdrom

Many thanks for your help Alpha.
I still don't really understand why there was no entry already in fstab, as the drive was clearly recognised for pre-recorded CD's and DVD's.

---

### Post by AlphaLexman on 2010-08-21
Please use the 'Thread Tools' and mark the thread as solved.

Thanks! O:)

---

### Post by Quackers on 2010-08-21
Sadly, I spoke too soon :-(
Neither + or - RW's are working (cd or dvd) and at bootup it is saying that the drive is not ready or present and to press S to skip loading or press M for manual recovery. If I press S the system loads ok, but why does the system expect the drive to be ready/present, when it never used to?

---

### Post by Quackers on 2010-08-21
These are 2 errors when trying to mount a CD-RW

---

### Post by Quackers on 2010-08-21
Ok, CD's can now be mounted, played, erased/recorded etc.
DVD's, can be played.
DVD -R and +R are ok now.
DVD -RW and +RW just unmount the drive. Brasero doesn't recognise that one is loaded and can't do anything with one.

And Ubuntu at bootup is still saying that the utf iso drive is not ready/not present and I have to press S to continue a normal boot.

---

### Post by Quackers on 2010-08-21
An update.
After googling around it seems that this has been a problem in the past.
It seems a workaround is possible.
When a DVD-RW or DVD+RW is put in and spools up, the cd/dvd drive disappears from Places > Computer. The disc is completely unrecognised. Brasero doesn't know there is a disc in the drive.
However, Gnomebaker does recognise the disc and will read it, write to it and erase it.
That can't be right. Is this a bug? Is anybody else having this problem? In the past it seems to have affected laptops much more than desktops. Anybody? :-)

---

### Post by Quackers on 2010-08-22
Another update. I wasn't happy with the situation so I deleted what I had put into the fstab and started again.
After a reboot (just in case) I find that I can now get recognised
CD-R
CD-RW
DVD-R
DVD+R
&
DVD+RW  but only if it has data or a movie on it. If it is blank it is not
        recognised - other than to make the cd/dvd drive disappear from Places >
        Computer display.

Unfortunately, I don't have examples of the other disc types to check them. Not sure why - I have plenty of discs :-)

---

