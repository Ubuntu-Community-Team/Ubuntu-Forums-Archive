---
title: "how to make ubuntu looking in to c: partition"
date: 2011-11-06
forum: General Help
---

### Post by xinqi_wang on 2011-11-06
hi, I am newbie to ubuntu. I recently tried to install unbutu on two windows machines.
but however, 
on the windows7 machine ( I have to return to school soon), ubuntu recognized the windows c: disk as a 80GB file system. so I can operate any folders in it. A small d: partition disappeared. 

whereas in the vista machine, ubuntu only looks the small partition d: as a 8.3 GB file system, the big c: partition is hidden from ubuntu. 

Is there anything  I can do to make ubuntu looking in to both the windows c: and d: partition? 
The windows 7 result is better to me.

Plus:
the desktop looking are also different. The result with win7, the desktop looking is more traditional with three pull-down menus" application , places, system"  on the top  and firefox icon. But the vista installation, it is the launcher on the left. I don't like the pop up luncher bar. Can I possibly change the desktop to the traditional looking?

Thanks  you very much

---

### Post by sanderd17 on 2011-11-06
First of all: please don't use big fonts. If we have bad eyes, we would enlarge the font for every site.

Now, you're talking about hard disks. Is this a wubi installation, or a normal dual boot? Can we see the output of
```

sudo parted -l

```
That will show all partitions on your computers. So we know what Ubuntu can possibly mount.

And for the look, the triple menu is an older version of Ubuntu. The new one is the one with the dock on the left. You can install all kinds of desktop environments in Ubuntu (e.g. KDE, LXDE, XFCE, Gnome-Shell, Gnome-fallback ...). They all have a different work flow and a different design. But going back to the triple-menu (the old Gnome) interface is difficult.

---

### Post by xinqi_wang on 2011-11-07
> **sanderd17 said:**
> First of all: please don't use big fonts. If we have bad eyes, we would enlarge the font for every site.

Now, you're talking about hard disks. Is this a wubi installation, or a normal dual boot? Can we see the output of
```

sudo parted -l

```
That will show all partitions on your computers. So we know what Ubuntu can possibly mount.

And for the look, the triple menu is an older version of Ubuntu. The new one is the one with the dock on the left. You can install all kinds of desktop environments in Ubuntu (e.g. KDE, LXDE, XFCE, Gnome-Shell, Gnome-fallback ...). They all have a different work flow and a different design. But going back to the triple-menu (the old Gnome) interface is difficult.
Thanks a lot! this is a wubi installation. I installed inside windows. I gave 30GB to ubuntu from windows c: disk.
when I do sudo parted -l 
it shows all the partitions.  the biggest is the windows c: with 232GB ntfs boot. 
What I can see in the ubuntu file system is only the 30GB allocated to linux when I was installing ubuntu.:
Can I possibly make the windows c: disk visible to ubuntu?  my windows d: and external hard drive are all visible to both windows and linux.
thank again

---

### Post by sanderd17 on 2011-11-08
[s]When you do the parted command, you will see that the windows disk gets a label. Something like /dev/sda1 (be sure it has a number at the end).

Now, can you do the following:
```

[s]sudo mkdir /media/c-drive
sudo mount /dev/sda1 /media/c-drive[/s]

```
Off-coarse, use the label you see on the parted command instead of sda1 I used.[/s]
[B]
I do trust Mark Phelps more than myself when it comes to partitioning and mounting. See below.[/B]

---

### Post by Mark Phelps on 2011-11-08
If you're using wubi, do NOT manually mount the "C" partition; instead, go into your file system under /host.  That is where the "C" partition is ALREADY mounted.

---

