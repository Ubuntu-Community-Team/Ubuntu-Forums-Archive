---
title: "Linux and Windows 7 HELP"
date: 2010-01-04
forum: General Help
---

### Post by Psyphin-X on 2010-01-04
i know this might have been pposted before but i have looked everywhere and tried everything but can;t fix it.

i dual booted vista and linux, i just got windows 7 and installed that. then something happened and i had to reinstall linux and now the GRUB bootloader doesn't allow me to enter windows 7. it still has vista acually. i beleive what happened was linux over wrote the windows 7 loader.

can anyone tell me how to get back into windows 7. at this point i don't care if i still have linux or not, i just need to get into my windows 7.

Thank You.

---

### Post by audiomick on 2010-01-04
If it is grub2, i.e. it is a fresh installed 9.10, 
```
sudo update-grub
```
should do it.

I think that works with legacy grub as well.

---

### Post by Psyphin-X on 2010-01-04
thanks, but i did that and it only found windows vista loaders.

i know windows 7 is there i can access the stuff on it through linux, but i just can't log onto windows 7.

any other guesses?

---

### Post by Psyphin-X on 2010-01-04
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done


thats what came up

---

### Post by Psyphin-X on 2010-01-04
it's like windows 7 doesn't exist anymore.

---

### Post by Psyphin-X on 2010-01-05
now what ive tried is i installed windows 7 on my second hard drive that had linux. then completly reformated my first hard drive. now im getting a grub error. shouldnt  that have deleted linux and over written the grub loader with the windows 7  loader?

any help would be great

---

### Post by Psyphin-X on 2010-01-05
When i try to start it says
 
GRUB loading.
error: no such disk
grub rescue>
 
 
 
I also just found out that if i leave my Windows 7 Install Disk in and not do anything it will eventually start my Windows 7 OS.

---

### Post by audiomick on 2010-01-05
Hallo.
That sounds like Grub is in the MBR of the first drive, which I don't think is affected by a re-format. This is getting a bit over my head though.

You could try changing the boot order in BIOS. As far as I know, windows always overwrites the MBR, but if the boot order is looking at the other drive first and finding a broken grub, it will try and boot that first.

---

### Post by dariush_03 on 2010-01-05
What about this [thread]("http://ubuntuforums.org/showthread.php?t=1014708")?

---

### Post by Psyphin-X on 2010-01-05
thanks for the ideas, i already tried the bootrec /fixmbr and bootrec /fixboot
 
but i will try the BIOS settings and i will let you know, thanks again.

---

### Post by Psyphin-X on 2010-01-05
YAY!! Thank You Audiomick. that worked perfectly, never would have thought of that. i tried everything. Thank You again.

---

### Post by Leppie on 2010-01-05
so you can now boot both linux and 7 again?

---

