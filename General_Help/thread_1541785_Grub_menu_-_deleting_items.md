---
title: "Grub menu - deleting items"
date: 2010-07-29
forum: General Help
---

### Post by Quackers on 2010-07-29
On booting my laptop the grub menu shows the following items

Ubuntu, with Linux 2.6.32-24 generic

Ubuntu, with Linux 2.6.32-24 generic (recovery mode)

Ubuntu, with Linux 2.6.32-21 generic

Ubuntu, with Linux 2.6.32-21 generic (recovery mode)

Memory test (memtest86+)

Memory test (memtest86+) serial console 115200

Windows Vista (loader) (on /dev/sda1)

Windows Recovery Environment (loader) (on /dev/sda2)

MAC OS X (32 bit) (on /dev/sda3)

MAC OS X (64 bit) (on /dev/sda3)


I use the first entry to load Ubuntu
I use the seventh item to load Vista
I use the ninth item to load Snow Leopard

Is it safe to delete all the other entries (so that just the 3 I use remain)?
If that is the case could somebody recommend the proper way to do this please. I have read many different threads with varying instructions.
I have only just got all 3 OSes booting properly. I wouldn't want to mess that up :(

Thanks

---

### Post by scouser73 on 2010-07-29
If you already have [**[COLOR="Red"]Ubuntu Twea[/COLOR]**k]("http://ubuntu-tweak.com/") installed then click on it.

Select Package Cleaner & click Unlock and then enter your password if required.

then select Clean Kernels [This is the bit the removes only the old kernels and leaves the newest in place]

Then click Cleanup and the old kernels will be removed.

Side Note:

Ubuntu Tweak is a great piece of software, so have a look about and you may see other things that you may want to install.

---

### Post by hhh on 2010-07-29
Are you using Ubuntu Lucid? If so you're using Grub2, so see this...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

So, to get rid of the memtests, in terminal run
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

To get rid of the recovery mode entries, do
```
gksu gedit /etc/default/grub
```and delete the "#" before the line "GRUB_DISABLE_LINUX_RECOVERY=true"

then, to see your changes, run 
```
sudo update-grub
```
and reboot.

It's usually recommended to keep an extra kernel entry just in case. If further updates give you more kernel entries, you can remove them via Synaptic. You find the image and header entries (it's 1 of each and they'll have the kernel number as part of them) that match the oldest kernel and mark them for removal.

HTH

---

### Post by Quackers on 2010-07-29
Thanks for the heads up Scouser73. It is installed and I am browsing through it now :-)

---

### Post by Quackers on 2010-07-29
Thanks hhh, invaluable info for me (the merest of noobs :-))

---

### Post by Quackers on 2010-07-29
My grub menu says Grub menu v1.98 - 1ubuntu7
Would that be grub or grub2?
Thanks

---

### Post by hhh on 2010-07-29
Grub 2.

---

### Post by Quackers on 2010-07-29
I suspected it would be, but with it saying v1.98 I wondered.
Many thanks.

---

### Post by Quackers on 2010-07-29
Ok, with the help of Scouser73 and hhh I'm now down to 5 items;

Ubuntu, with linux 2.6.32 - 24 generic          -   used for booting Ubuntu
Windows Vista (loader) (on /dev/sda1)           -   used for booting Vista
Windows Recovery Environment (loader) (on /dev/sda2)    -   NOT USED
MAC OS X (32 bit) (on /dev/sda3)                -   used for booting Snow Leopard
Mac OS X (64 bit) (on /dev/sda3)                -      NOT USED

Any ideas on deleting the 2 unused items?
Many thanks.

---

### Post by oldfred on 2010-07-29
You can turn off osprober so it only finds Ubuntu and add your own entries into 40_custom. If you every add another operating system turn on the prober and copy that entry.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Copy the windows entries from this before turning off prober:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by Quackers on 2010-07-29
Thanks for that oldfred, I will be reading up shortly.
Just one thing though. Although I have started to use Ubuntu most of the time, I need to boot into Vista and Snow Leopard sometimes. Perhaps when I can find my way around Ubuntu more easily I will become a full-time user, but at the moment that is not the case. Presumably if I turn off the osprober I would not be able to boot the other OSes.

---

### Post by oldfred on 2010-07-29
If you copy the boot stanza's to 40_custom you will still be able to boot them. It just will not find updates for new systems. Once in 40_custom you can manually edit to your hearts content. 

This is part of my 40_custom which lets me still boot windows and chainload to several other systems:
```

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry " " {
set root= 
}

menuentry "Lucid Lynx on sda Chainboot" {
set root=(hd0)
chainloader +1
}

menuentry "9.04 on sdb Chainboot" {
set root=(hd1)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}
```

---

### Post by Quackers on 2010-07-29
Thanks again oldfred.
I am still reading the threads you posted links to. In particular the custom boot menu. It's just a matter of getting my beans together and biting the bullet :-)

---

