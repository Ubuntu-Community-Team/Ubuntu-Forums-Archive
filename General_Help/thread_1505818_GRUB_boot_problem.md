---
title: "GRUB boot problem"
date: 2010-06-09
forum: General Help
---

### Post by ken poy on 2010-06-09
hello,  i am a very new Ubuntu Linux user.  i installed from a download at level 9.10.
this ran without problems for sometime.  the update manager kept bugging me to apply 10.04LTS.  so i finally did apply some 200+ updates.  now in GRUB i get level 2.6 31-21 and intermittently the boot hangs with a blank or garbage screen.  i see similar problems listed with circumventions.  can someone net this out for me.  is there a bug which will be fixed or do i need a circumvention but which one??  i have also had system hangs which require a reboot.  a little nervous thanks  ken

---

### Post by Jahocolips on 2010-06-09
I would suggest you restore GRUB...

   [LIST]
[*]Boot from a 9.10 Live CD, or from a flash drive

[*]Open a terminal and enter the command
```
sudo fdisk -l
``` 
This displays your partitions...

[*]Now you mount the Linux partition (Look for "Linux" under "System")
```
sudo mount /dev/(Linux) /mnt
```
Where (Linux) is some "sda4", or something where Linux is at

[*]Now that it's mounted just install GRUB again
```
sudo grub-install -root-directory=/mnt "path"
```

[*]End with unmounting
```
sudo unmount /mnt
```
[/LIST]

Keep me posted with how things go.

---

### Post by ken poy on 2010-06-16
Thanks for the update.  i tried the grub install
1  i booted from my 9.10 memory stick download
2  the sudo fdisk -l  showed sda4  Extended
                                        sda5  Linux
                                        sda6  Linux Swap / Solaris
3  did the sudo mount /dev/sda5 /mnt
so far things seem to be going okay
4  did the sudo grub -install -root-directory=/mnt "path"
   received grub command not found.  tried upper case with same results.
   not sure about spaces in the command.
also i think i need  umount not unmount command at end.
thanks    ken

---

### Post by ken poy on 2010-06-16
hello,  this is an update to my previous.

i now do the mount and the grub-install

the grub command is found but i get an unrecognized option  -root-directory=/mnt
this is the DIR part and i did specify  /mnt "path"
not sure what i need here.      thanks ken

---

### Post by warfacegod on 2010-06-16
"umount" is correct.

More info here, Section .13 [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

