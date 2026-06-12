---
title: "Noob questions?, idk"
date: 2010-06-13
forum: General Help
---

### Post by sw0o0sh on 2010-06-13
I was primarily using a Windows XP for quite a few years now, and recently a friend of mine recommended Linux for the hosting a gameserver and what not bla bla, so I figured I'd learn how to partition my drive and install Linux to get an idea (so here I am, it's running). 

Anyway, long story short, and please do let me know if I am lacking specificness, I did a side-by-side installation from a CD iso of Ubuntu. However, when I turn on the computer, the grub boot options are duplicated for the Ubuntu? 


```

 [SIZE=3][COLOR=#000000][FONT=Arial]linux image: /boot/vmlinuz-2.6.32-22-generic
initrd image: /boot/initrd.img-2.6.32-22-generic
linux image: /boot/vmlinuz-2.6.32-21-generic
initrd image: /boot/initrd.img-2.6.32-21-generic
memtest86+ image: /boot/memtest86+.bin
Windows XP Media Center Edition on /dev/sda1
[/FONT][/COLOR][/SIZE]
```[SIZE=3][COLOR=#000000][FONT=Arial]

Also,

when I run the command [/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Arial]df -h

It says:

[/FONT][/COLOR][/SIZE]```
[SIZE=3][COLOR=#000000][FONT=Arial]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              26G  2.8G   22G  12% /
none                  244M  332K  244M   1% /dev
none                  248M  296K  248M   1% /dev/shm
none                  248M   88K  248M   1% /var/run
none                  248M     0  248M   0% /var/lock
none                  248M     0  248M   0% /lib/init/rw
/dev/sda1              48G   19G   29G  40% /media/FEBCDBC8BCDB7A1B
[/FONT][/COLOR][/SIZE]
```[SIZE=3][COLOR=#000000][FONT=Arial]

Did something go wrong?
[/FONT][/COLOR][/SIZE]

---

### Post by bruno9779 on 2010-06-13
Everything looks fine.

you have more than one entry in grub, because you have more than one kernel installed. Probably the one from the install and the other one from updating.

You can get rid of the older one, but it is a good idea to keep it as fallback, if something goes wrong.

also, i don't see what df -h has to do with this

---

### Post by sw0o0sh on 2010-06-13
> **bruno9779 said:**
> Everything looks fine.

you have more than one entry in grub, because you have more than one kernel installed. Probably the one from the install and the other one from updating.

You can get rid of the older one, but it is a good idea to keep it as fallback, if something goes wrong.

also, i don't see what df -h has to do with this

Alright thanks man, I thought all the "nones" were odd but then again idk anything about this stuff as of yet.

---

