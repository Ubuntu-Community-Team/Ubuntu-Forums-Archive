---
title: "Drops to Busybox"
date: 2011-05-29
forum: General Help
---

### Post by farkinid on 2011-05-29
Hi guys, 

I've got quite a problem today. I'll give you the background on my computer 1st.

The computer I'm using has 2 hard drives.
/dev/sda = windows 7 (320GB hitachi drive)
/dev/sdb = Ubuntu 9.10 (250GB WD drive)

The ubuntu drive was previously on my old desktop and was working fine. I bought this new desktop and attached the Ubuntu drive with no problems. Booting was not a problem either (I use my bios to select which drive I want to use).

Recently I purchased a new hitachi 1TB hard drive. When I attached the 1TB into the desktop, windows boots fine. However, Ubuntu fails to boot. It gives me the error
"Gave up waiting on root device". If I remove the 1TB, everything boots as per normal.

Any advice or help? I can produce my fstab if it will help (but I'm not sure if it would)

---

### Post by Rubi1200 on 2011-05-30
Have you tried booting into Ubuntu then attaching the 1TB drive and then running ```
sudo update-grub
```

Might be worth a try.

---

### Post by farkinid on 2011-05-30
when I try to update grub, I get the error

> grub-probe: error: cannot find a GRUB drive for /dev/sdb1. check your device.map.

---

### Post by linuxinstalledfromhdd on 2011-05-30
It sounds like the MBR on the windows drive is interfering with the MBR on the Ubuntu drive.  Since you didn't install Ubuntu on the desktop system and you didn't install windows on the desktop system, they both have their own specific MBR.  You could try booting from a nice live disc of Ubuntu with both drives in there and reinstall Ubuntu to the first drive, and that would probably fix it.  You would need to shrink the first drive a bit so you can fit the installation of Ubuntu. The live disc installer will help you shrink it to make space for the new install as well. :)

BTW - Did you physically set the windows drive to "slave" with the jumper?

---

### Post by Rubi1200 on 2011-05-31
I suggest you try the following:

Make sure the Ubuntu disk is plugged in and then boot into Ubuntu and run the following commands with the new 1TB drive attached:

```
sudo grub-install --recheck /dev/sdb
sudo update-grub
```

If this fails to resolve the problem, please post the results of the boot info script. There is a link at the bottom of my post with instructions.

---

### Post by farkinid on 2011-05-31
Thanks for all the help guys. Its been very educational. I got the system to boot normally with all drives attached by switching sata ports on the motherboard. It seems that my Ubuntu drive was plugged into port 3 and my new 1TB was put into port 2.

After plugging Ubuntu into 2 and 1TB into 3, it boots fine. However, I have a problem with mounting the 1TB on boot. I get the message :
```
Unable to mount 1000GB FileSystem
Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount /dev/sdc1 on /media/Mirror
```At first glance, it looks like a root issue but, I have already done the following :-

[LIST=1]
[*]I have already added the following codes to my fstab
```
 /dev/sdc1 /media/Mirror ext4 
rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush     0        2
```
[*]I have taken ownership of the /media/Mirror directory using ```

sudo chown -R yee:yee /media/Mirror
```
[*]Also, my dmesg | tail results are as follows
```
[   19.996140] vboxdrv: Successfully done.
[   19.996141] vboxdrv: Found 4 processor cores.
[   19.996383] vboxdrv: fAsync=0 offMin=0x207 offMax=0x14a12
[   19.996714] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.996715] vboxdrv: Successfully loaded version 3.2.10 (interface 0x00140001).
[   20.606384] EXT4-fs (sdc1): Unrecognized mount option "shortname=mixed" or missing value
[   27.634479] EXT4-fs (sdc1): Unrecognized mount option "shortname=mixed" or missing value
[   28.549710] eth1: no IPv6 routers present
[   32.297752] EXT4-fs (sdc1): Unrecognized mount option "shortname=mixed" or missing value
[ 2078.367633] usb 2-1.4: USB disconnect, address 4
```
[/LIST]


I'm not sure how to proceed anymore

---

### Post by drs305 on 2011-05-31
I'm not familiar with a couple of your fstab entry options (which means little), but apparently the system doesn't like this one;
>  32.297752] EXT4-fs (sdc1): Unrecognized mount option **"shortname=mixed"** or missing value

You might try removing that and see what happens.

You can test fstab entries in a terminal. Close everything you can and the run "sudo umount -a" and then "sudo mount -a". It won't unmount 'busy' partitions but should show any errors for those that it can operate on.

---

### Post by matt_symes on 2011-05-31
Hi

```
shortname=mixed
```

From man mount

> Mount options for vfat
       First of all, the mount options for fat are recognized.  The dotsOK option is explicitly killed by vfat.  Furthermore, there are
<snip>

       **shortname={lower|win95|winnt|mixed}**

              Defines  the  behaviour for creation and display of filenames which fit into 8.3 characters. If a long name for a file exists, it will always be preferred display. There are four
              modes: :

              lower  Force the short name to lower case upon display; store a long name when the short name is not all upper case. This mode is the default.

              win95  Force the short name to upper case upon display; store a long name when the short name is not all upper case.

              winnt  Display the shortname as is; store a long name when the short name is not all lower case or all upper case.

              mixed  Display the short name as is; store a long name when the short name is not all upper case.It an option for vfat and 8.3 files names. 

If you are using ext4 as your fstab suggests then you must remove it as drs305 has pointed out.

Kind regards

---

### Post by farkinid on 2011-05-31
Thanks for the quick reply. To be honest, I'm not very sure whats with the complicated fstab options. I copied it off [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive).

Seemed to be the safest thing to follow. I will run a remount after I've backed up my server. (should be done in an hour). Lets hope chaning the options work. I've decided to switch to 
```
defaults,errors=remount-ro
```

---

### Post by farkinid on 2011-06-01
Alright, just a quick update. After changing the options, its working. 

Thanks alot guys. Much appreciated

---

### Post by Rubi1200 on 2011-06-02
Excellent! Glad you got things sorted out in the end.

Enjoy :)

---

