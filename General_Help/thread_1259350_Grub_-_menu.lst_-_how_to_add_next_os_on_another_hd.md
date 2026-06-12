---
title: "Grub - menu.lst - how to add next os on another hdd"
date: 2009-09-06
forum: General Help
---

### Post by ExiMoR on 2009-09-06
Hello all! :)
I've just a lil problem:
In our family, we have two removable hdds (Me and my fother)..
Both are 160GB-ish, but one is SATA (I think) and one... idk, but it's a little bit older type.. :D
My hdd (newer) has two os : Ubuntu Jaunty and <caught>horrible</caught> Wirus Vista (dualboot) (on hd0,0)...
When in pc are both hdds, pc use first my hdd and show mine grub menu..
Okay.. So I've access to my fother's hdd from Vista and Ubuntu (logically :D)...
But when my fother needs to use his <caught>horrible and unuseable</caught> Windows XP, I must turn pc off, remove my drive and turn pc on... I can't then, of course, access my hdd (logically - it's removed from pc :D)...
So I wanna "add to my grub menu.lst fother's os", so I then can choose to boot windows xp instead of my vista or ubuntu.
Some infos (sorry, some stuffs are in czech):

```
eximor@ExiMoR:~$ sudo fdisk -l

Disk /dev/sda: 160,0 GB, 160 041 885 696 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 19 457
Jednotky = cylindry po 16065 * 512 = 8 225 280 bajtech
Identifikátor disku:&#8239;0x99bd99bd

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sda1   *           1        6710    53889024    7  HPFS/NTFS
/dev/sda2            6710        7101     3145796    7  HPFS/NTFS
/dev/sda3            7102       19457    99249570    5  Rozší&#345;ený
/dev/sda5            7102       19130    96622911   83  Linux
/dev/sda6           19131       19457     2626596   82  Linux swap/Solaris

Disk /dev/sdb: 160,0 GB, 160 041 885 696 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 19 457
Jednotky = cylindry po 16065 * 512 = 8 225 280 bajtech
Identifikátor disku:&#8239;0xc5f60e49

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sdb1   *           1        6091    48925926    7  HPFS/NTFS
/dev/sdb2            6092       19457   107362395    7  HPFS/NTFS

```gksudo gedit /boot/grub/menu.lst
```

title        Ubuntu 9.04
uuid        **********
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=********** ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04 (recovery mode)
uuid        **********
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=********** ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        **********
kernel        /boot/memtest86+.bin
quiet

title        Other operating systems:
root

title        Windows Vista Ultimate
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```I've also tried to add this
```
title        Widnows X9 Professional
root        (hd1,0)
savedefault
makeactive
chainloader    +1
```(Windows wrote something like a problem with loading from disc)

and:

```
title        Widnows X9 Professional
map (hd1) (hd0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader    +1
```(grub wrote something like Loading ..... and (I think) freezes (or have tried to boot, but It taked so long and nothing happen))...

So... Can anybody help me what I can do? :)
BTW: Sorry for my horrible english, I'm writtin' like a retarded donkey (czech one :D), but I'll understand you well (hope so :D).

I'll appreciate any feedback from your side ;)

---

### Post by Brandon Williams on 2009-09-06
I don't run Windows, so I'm not sure that this will work, but ...

I think that you need to remap both drives, not just the second one. But when you declare the root, you still need to refer to it as (hd1,0). So, try this:
```
title        Widnows X9 Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1
```

---

### Post by Bucky Ball on 2009-09-06
```
title        Widnows X9 Professional
[B]map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)[/B]
savedefault
makeactive
chainloader +1
```Except like this:

```
title        Widnows X9 Professional
[B]root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)[/B]
savedefault
makeactive
chainloader +1
```:)

'root (hd1,0) should come first and 'noverify' should not be required.

---

### Post by alejaaandro on 2009-09-06
not as experienced as to propose a grub solution, but as a workaround you could press F11 or F12 (depending on your computer) when it's starting (before it even gets to grub) and you 'll be able to choose which disk to boot from..

if that's too much trouble for your father, you can configure your bios to boot by default from the disk with XP and you can do the F11/F12 trick when you want to boot to grub.. (if you want more info on that, ask)

---

### Post by ExiMoR on 2009-09-07
Oh your god! You guyz rockz! :guitar:
Thanks for replies :)
@Bucky Ball:
```
[B]root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)[/B]
```worked, thanks! :)
Now my parents must use my beatiful grub menu with Enstein on background :D
@[alejaaandro]("http://ubuntuforums.org/member.php?u=395548"): This is exactly, I don't wanna use, but thanks for idea :)

---

