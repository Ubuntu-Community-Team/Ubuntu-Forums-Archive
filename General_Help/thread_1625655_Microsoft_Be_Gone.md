---
title: "Microsoft Be Gone"
date: 2010-11-19
forum: General Help
---

### Post by Tallorder64 on 2010-11-19
Is it possible to format my hard drive (thereby cleaning it) and then put the Linux disk in so that my computer will be Linux only?

---

### Post by Decatf on 2010-11-19
The Ubuntu installer has the option to wipe the entire disk and install Ubuntu on it.

---

### Post by Quackers on 2010-11-19
Yes, just boot from the Live cd and choose "use entire disc" which will over-write everything windowsy! Be sure that all your hardware works first though, by selecting "try ubuntu" from the live cd. Also make sure that you won't need Windows again!

---

### Post by Zill on 2010-11-19
> **Tallorder64 said:**
> Is it possible to format my hard drive (thereby cleaning it) and then put the Linux disk in so that my computer will be Linux only?
I did just that years ago and never looked back :-)

---

### Post by Quackers on 2010-11-19
Exterminate! :-)

---

### Post by Rubi1200 on 2010-11-19
It is possible, but let me offer some advice.

1. backup any important data first

2. make sure you either have or can get a Windows installation/repair disk

3. consider whether you really want to do this and why

There are users who regret having gone down the path you want to, for whatever reason; gaming, work, the feel of something familiar, a program that only works in Windows etc.

As suggested above, first try Ubuntu as a LiveCD.

Then, consider first dual-booting for at least 6 months before deciding to go 100% Linux.
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Best of luck whatever you decide :)

---

### Post by NoNameWill on 2010-11-19
I did it this year on two computers in my home with 10.04LTS.

---

### Post by Serpher on 2010-11-19
You **DON'T** have to reinstall your entire system unless you used a wubi install, in that case do what everybody's saying. If you want to do this, just do the following steps:

1)Find out what partition number your Windows is on. This can usually be seen on your grub in brackets "Windows Vista (on /dev/sda2)", or by going into gparted.

```
sudo -i
fdisk /dev/sda (may be /dev/hda)
```

This will now put you in the fdisk program, enter 'd' for the first command, then it will ask you for a partition number. Type in the number Windows is on then enter the command 'w'. At this point EVERYTHING in your windows partition will be gone. To resize your Linux partition enter:

```
resize2fs /dev/sda(partition number) (Size of your hardrive)
```

If you don't know how big your hardrive is:

```
df -h
```

---

