---
title: "help! ruined fstab! (i think)"
date: 2010-12-30
forum: General Help
---

### Post by Mesqueeb on 2010-12-30
Hi!
I think I ruined my fstab!
Now when I boot up it gives me a black command line screen where I can 'log in' into my Ubuntu account it seems, but no more graphics..........................
this is my current fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=cafd6c39-dde7-43d0-a95d-66d3a53cb7db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=274b841f-dc6b-43b0-a8eb-da5d7bf13ae8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

The story behind it:
I found a script online to mount the iphone with gtkpod iPod manager, after I did that and rebooted I got the message "the disk drive for /media/iPod is not ready yet or not present"........
so I followed this guys advice:
> boot into recovery mode from grub
login to the terminal and run
sudo nano /etc/fstab
remove the line that contains /media/iPod
after going to recovery mode I saw grub, but most things were displayed as strange dimes... (maybe because originally my OS isn't in english) anyway, I pressed the grub thing, and some things happened, but I stayed on the menu... so I guessed just to press resume then, and that got me to a black screen with command line.
there I edited the fstab (with nano, because gedit was impossible) and after that i reboot, and now this........

only command line.....

Thanks for any help!!!!!

-Mesqueeb

---

### Post by jetpeach on 2010-12-30
i can't be of much help figuring it out, but this thread might be useful
[http://ubuntuforums.org/showthread.php?t=537200](http://ubuntuforums.org/showthread.php?t=537200)

particularly if there is a backup version (maybe save your current version to another backup first too, but then try)
sudo cp /etc/fstab.pre-uuid /etc/fstab
to see if that backup will work

i think you can see if the fstab is working without rebooting by trying 
sudo mount -a
and see what it says or errors

for your refering, here is my fstab, in case it helps (ubuntu 10.10, one hard drive all default options, of course your UUID's will be different on your system)

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c35b205b-a7a1-40b0-bfb8-54be9317287b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5267f6c1-4950-44c2-a6bb-985497ed7b24 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by WorMzy on 2010-12-30
I can't see a problem with your fstab, and it sounds like Ubuntu is booting up fine, it's just not starting the graphical interface.

Can you run the following command:
```
sudo service gdm restart
```

Does that give an error? If so, post it here.

---

### Post by Mesqueeb on 2010-12-31
Yes, it would seem indeed it wasn't my fstab file after all, after rebooting again it told me it started in low graphics mode and said some things about nvidea.... I pressed to boot once in low graphics then, got the command line, and tried startx. Which worked like a charm. My nvidea suddenly got corrupt I guess, don't know why. Anyway, I was able to get what information I needed, and just reinstalled ubuntu on a different hdd.

Is there a way of deleting everything ubuntu related files on my old hdd besides the home folder with my files?
Just select all besides 'home' and press delete? xD

- Mesqueeb

---

