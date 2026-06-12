---
title: "Booting Problem"
date: 2010-06-16
forum: General Help
---

### Post by xZxGangsta457zXz on 2010-06-16
i have windows 7 pre-installed on my Acer laptop, i installed ubuntu from a disc and it created a partition for me, after i booted into windows 7 a while later i deleted the ubuntu partition i had, then i shutdown my laptop, the next morning when i turned on my laptop i get a message that says

error: no such partition
grub rescue>

now i tried installing ubuntu again but the 3rd or 2nd option in the partition part of the ubuntu installation is no longer there so i have no idea how to install it without deleting any of my files, i dont have any discs for my laptop as the os came pre-installed but im thinking of going to my friends house and making a windows 7 repair disc found here [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html).
if there is another way of fixing this problem without deleting any of my files itd be great :).

---

### Post by bcbc on 2010-06-16
boot ubuntu using the install cd you have (select 'try without changes'). Then go to System, Administration, Software Sources and on the first tab, make sure the Universe repository is enabled (second checkbox).

Then go to a terminal (Applications, Accessories, Terminal) and run 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

This will install the windows boot loader (actually it's equivalent to windows bootloader). You can ignore the warnings after the first command as they apply to using lilo for booting linux.

Alternatively, if you can get that windows repair CD then you can just install the windows bootloader: ```
bootrec.exe /fixmbr
```

---

### Post by xZxGangsta457zXz on 2010-06-16
> **bcbc said:**
> boot ubuntu using the install cd you have (select 'try without changes'). Then go to System, Administration, Software Sources and on the first tab, make sure the Universe repository is enabled (second checkbox).

Then go to a terminal (Applications, Accessories, Terminal) and run 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```This will install the windows boot loader (actually it's equivalent to windows bootloader). You can ignore the warnings after the first command as they apply to using lilo for booting linux.

Alternatively, if you can get that windows repair CD then you can just install the windows bootloader: ```
bootrec.exe /fixmbr
```

i get this after copying sudo apt-get install iilo sudo lilo -M /dev/sda mbr in terminal

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 210 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

---

### Post by bcbc on 2010-06-16
that's strange, I get:
```
$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 56 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ lucid/main mbr 1.1.10-2 [23.0kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ lucid/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 2s (181kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 139473 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

```

Not sure why it's not working for you; if you can't install lilo, then you'll have to use a windows repair disk.

---

### Post by xZxGangsta457zXz on 2010-06-16
ok thanks anyways.

---

### Post by oldfred on 2010-06-16
You can download a repair only CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by cuberts on 2010-06-16
> **xZxGangsta457zXz said:**
> i have windows 7 pre-installed on my Acer laptop, i installed ubuntu from a disc and it created a partition for me, after i booted into windows 7 a while later i deleted the ubuntu partition i had, then i shutdown my laptop, the next morning when i turned on my laptop i get a message that says

error: no such partition
grub rescue>

now i tried installing ubuntu again but the 3rd or 2nd option in the partition part of the ubuntu installation is no longer there so i have no idea how to install it without deleting any of my files, i dont have any discs for my laptop as the os came pre-installed but im thinking of going to my friends house and making a windows 7 repair disc found here [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html).
if there is another way of fixing this problem without deleting any of my files itd be great :).Boot from your CD that you have, and then click on install Ubuntu, on the desktop. Just follow the steps that it tells you to do. Also are you able to boot from your Ubuntu partition at all

---

### Post by xZxGangsta457zXz on 2010-06-16
> **cuberts said:**
> Boot from your CD that you have, and then click on install Ubuntu, on the desktop. Just follow the steps that it tells you to do. Also are you able to boot from your Ubuntu partition at all
no i combined it with another partition

---

### Post by xZxGangsta457zXz on 2010-06-29
sorry for bumping this thread but, is it possible to burn a disc while on ubuntus try me stage?

---

