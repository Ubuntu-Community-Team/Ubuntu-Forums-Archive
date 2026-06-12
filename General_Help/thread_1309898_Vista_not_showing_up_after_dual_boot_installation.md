---
title: "Vista not showing up after dual boot installation"
date: 2009-11-01
forum: General Help
---

### Post by mardis on 2009-11-01
I partitioned my hard drive and tried to install Ubuntu 9.10 as a dual boot system. When I start up, however, GRUB lists Ubuntu only, and I can't boot in Windows. I'm running Vista on the other partition. When I load Ubuntu I can see the other partition and if I open it, all the files still seem to be intact. I ran  sudo gedit /boot/grub/menu.lst in the terminal and this is what I get ...

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dibichafhg_Volume05 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dibichafhg_Volume05 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

Vista just isn't showing up. Any ideas? By the way, I am brand new to Linux and Ubuntu (which is why I was trying to make a dual boot system). Any help would be greatly appreciated. I was going to try to edit the above menu, but I thought that might be a bad idea if I didn't really know what I was doing.

Thanks

---

### Post by crosstalk on 2009-11-01
Did you use Wubi to install it? This is different from repartitioning the drive, and it does everything automatically. If you repartitioned the drive, please post the partitions you created.

You probably need to add an entry for Vista, but I wouldn't know how to do that.

Unfortunately, I am not knowledgeable enough about GRUB to help you any further.

I hope this helps.

---

### Post by mardis on 2009-11-01
I partitioned the disk in Windows with the disk manager prior to installing Ubuntu. First I used the disk manager to shrink the Vista partition and then I used the remaining free space to install Ubuntu. It worked out to roughly 700 GB for Vista (that's as small as it would shrink) and 300 GB for Ubuntu. I have two 1TB drives set up in a RAID1 configuration.

 I made a disk with the .iso image for the installation.

---

### Post by mardis on 2009-11-01
I booted from the Vista disk and ran a check. No errors were found with startup/boot. Is this a problem that something like SuperGrub Disk might be able to fix?

Alternatively should I add a few lines such as ...

title           Microsoft Windows Vista Business
root            (hd0,1)
savedefault
makeactive
chainloader     +1

to the sudo gedit /boot/grub/menu.lst?

Thanks

---

### Post by ranch hand on 2009-11-01
Run;
```

sudo update-grub

```
This should fix it.

Read link in my sig.  Check the links, particularly the first 3.

---

### Post by mardis on 2009-11-01
I ran sudo grub-update and nothing changed. I followed your link and then ran the 

sudo grub-mkconfig

which showed the Ubuntu partitions much like the sudo gedit /boot/grub/,emu.lst but then went on to say ...

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows Vista (loader) on /dev/mapper/isw_dibichafhg_Volume01
menuentry "Windows Vista (loader) (on /dev/mapper/isw_dibichafhg_Volume01)" {
grub-probe: error: no mapping exists for `isw_dibichafhg_Volume01'
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
 
Should I add something like ...

menuentry "Windows Vista (loader) (on /dev/mapper/isw_dibichafhg_Volume01)" {
        linux (hd0,1)/boot/vmlinuz
        initrd (hd0,1)/boot/initrd.img
}
I'm not too sure about the second and third lines of code (or the first for that matter).

Thanks again

---

### Post by RJ12 on 2009-11-01
> **mardis said:**
> I booted from the Vista disk and ran a check. No errors were found with startup/boot. Is this a problem that something like SuperGrub Disk might be able to fix?

Alternatively should I add a few lines such as ...

title           Microsoft Windows Vista Business
root            (hd0,1)
savedefault
makeactive
chainloader     +1

to the sudo gedit /boot/grub/menu.lst?

Thanks

I maybe wrong but SuperGrubDisk should help, and if it dosent ive heard it can boot OSes directly from it so you could use as a temp fix.

Plz understand that if im wrong its not my fault and its just a idea i recommend using ideas from more professionals though.

---

### Post by ranch hand on 2009-11-01
```

sudo update-grub

```
Not grub-update

---

### Post by mardis on 2009-11-01
I'm sorry, that was a typo. I used the code sudo update-grub to no effect.

---

### Post by ranch hand on 2009-11-01
I would use a custom entry in grub2.

---

### Post by pootan on 2009-11-01
@ranch hand

When I had the same the same grub issue with upgrading from 8.10 to 9.04 I was told to run this command 

sudo aptitude install grub-pc

from instructions here: [http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

would this help the OP any?

---

### Post by mardis on 2009-11-01
That's kind of where I'm hung up. I'm guessing I can't just cut and paste the custom entry from your link. Any tips on how to modify the wording so as to make it apply to my system? I realize this is probably a silly noob question, buy I am (regrettably) a silly noob. 

Thanks ranch hand

---

### Post by jord_101 on 2009-11-01
You guys seem to have got technical, so its over my head now, but i had a similar problem with my xp untill i looked down... probably just me who wasn't smart enough to look down straight away. Anyway sorry

---

### Post by ranch hand on 2009-11-01
@ pootan
Grub-pc is grub2.  9.10 uses grub2 as default.  For that matter, if you are using 9.04 (without grub2) you will have a lot of the files needed due to updates in grub-common.

The problem seems to be one of the quirks in os-prober that have not been completely corrected.  We are using 1.97beta4.

I think that you are using 1.96 which is what is still in the 9.04 repo (I don't know why, 1.97beta is better).

---

### Post by ranch hand on 2009-11-01
> **mardis said:**
> That's kind of where I'm hung up. I'm guessing I can't just cut and paste the custom entry from your link. Any tips on how to modify the wording so as to make it apply to my system? I realize this is probably a silly noob question, buy I am (regrettably) a silly noob. 

Thanks ranch hand
I am not sure what entry you are talking about but this is the one I would use from drs305;
```

echo "Adding Windows 43_custom" >&2
menuentry "Windows Vista 43_custom" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
} 			 		

```
The stuff between the " " does nothing an you can change that to anything you want, it is just title.

Set root is pretty plain, just remember that hd0 is the first drive (counting starts with 0) and the partition number is the one that gparted uses (counting starts from 1).

The uuid can be found for your partitions by running;
```

blkid

```
and just plugging it in.

Yes, I see that you are a noob.  My join date is before (2 weeks) my first actual experience with Linux of any kind.  So that makes me all of about a month and a half less noob than you.

I do have the advantage of testing 9.10 since alpha1.  I also do not use anything but Linux (bought this box with Vista on it and new in 3 days it had to go or I would have a stroke).

Have FUN.  Follow the suggestions on my link for setting up your custom file and the bugger will be on the top of your menu.

---

