---
title: "Ubuntu 11.04 and Windows 7 dual boot issues"
date: 2011-08-15
forum: General Help
---

### Post by anandsr on 2011-08-15
I have a machine with one hard disk and an ssd; I had Vista installed on the hard disk and Windows 7 installed on the ssd. I decided to replace the Vista with Ubuntu, and having done that, I seem to have lost the option to  boot into Windows 7. There were a bunch of partitions on the hard disk before, and I got rid of Vista's "C:" and replaced it with two partitions: one for "/" and a 4G one for "swap". Note that I can still access the ssd and the other partitions, but the Windows boot option is missing on reboot. 

There ought to be a simple way to tell grub that Windows is installed on the ssd, but I can't figure that out :( I also searched around the forum for an answer that wouldn't require re-installing anything but haven't found one. Here's the info from boot_info_script.sh I have attached the RESULTS.txt file. I appreciate any help I can get to fix this. Thanks!

---

### Post by Mark Phelps on 2011-08-15
Boot into Ubuntu.  Once there, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB menu and add an entry for Win7 Loader.  When you reboot, you will then see the GRUB menu.

---

### Post by anandsr on 2011-08-15
I have already tried that. It doesn't work. I only see the following in the output of update-grub (and the options on reboot seem to match these).

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-10-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by anandsr on 2011-08-15
I tried following the steps in [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/]("http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/") and that didn't work. I got "BOOTMGR missing" when selecting windows after following that option.

---

### Post by Primefalcon on 2011-08-15
hmmm what you might want to do is boot from a windows cd and do a fixmbr on whatever drive your ssd is...

then go into linux do the update grub as listed above...

my guess is that your windows boot record was on vista and is no longer in existance... so that needs to be fixed

---

### Post by anandsr on 2011-08-15
Unfortunately, that hasn't worked for me either. I booted using the windows CD, went to the command prompt and did the following:

> bootrec /ScanOS
bootrec /FixMbr

The latter command seemed a bit magical to me since it didn't take any other options...and it didn't work for me. I guess I need to RTFM about bootrec and go back and try to make it work. In case, anybody else has any other bright ideas, let me know. Thanks!

---

### Post by Primefalcon on 2011-08-15
well what I am saying is do both in said order..

for example

at the windows prompt

first off boot to the recovery console type in 

```
map arc
```
to get a listing of drives by arc

then what you want to do is fix the mbr for your windows 7 partition via (wich is the ssd your looking for here....)

```
fixmbr \device\win7drive
```

then after having finished that boot into windows and do the ```
sudo update-grub
```

---

### Post by anandsr on 2011-08-18
Thanks to everybody for their help. I finally managed to fix the issue after trying out many different things. For some reason, the windows repair failed to work until I removed the other hard disk. After that, it worked even though I did have to do the repair twice for some reason. Once that was fixed, re-installing and updating grub fixed the issue overall. (I had to re-install grub on the primary hard disk since it had broken during the variety of things I was trying out.)

---

