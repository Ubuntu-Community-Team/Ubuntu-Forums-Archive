---
title: "finding /dev/hxx ?"
date: 2009-12-16
forum: General Help
---

### Post by garyed on 2009-12-16
Is there any way to find out how your drives & partitions are referenced in different versions of Ubuntu by booting from a live CD? I know how to use fdisk -l but that only tells how the kernel on the disk I'm booting from names them. I have 3 different versions of Ubuntu. One labels my drives hda, hdb & sda, another labels them sda,sdb,sdc in totally different order. I ask this because I finally made a grub2 boot disk & found how to get into all my drives but knowing the way each kernel references them is a necessity to be able to boot to each one in an emergency. I was wondering if there was some kind of grub command if it can't be done from a live CD. I'm just trying to plan for an emergency because I'm going to be testing some more distros.

---

### Post by earthpigg on 2009-12-16
hi,

take a look at the output of this command on each linux/unix/ubuntu install:

```
cat /etc/fstab
```

---

### Post by garyed on 2009-12-16
> **earthpigg said:**
> hi,

take a look at the output of this command on each linux/unix/ubuntu install:

```
cat /etc/fstab
```

Excellent,

That's just what I was missing.
Now it should be pretty easy to boot into any version on any partition in an emergency with a grub boot disk. If I don't remember how they're numbered I can use the live CD to view the fstab files.

---

### Post by earthpigg on 2009-12-16
> **garyed said:**
> Excellent,

That's just what I was missing.
Now it should be pretty easy to boot into any version on any partition in an emergency with a grub boot disk. If I don't remember how they're numbered I can use the live CD to view the fstab files.

have a blast experimenting with fstab, but make sure you back them up before you change anything! so you can revert if/when your experimentation breaks things. and don't play with fstab if you will ***need*** to use those computers to get actual ***mission critical*** work done within the next several hours -- just in case.

once you navigate to /etc/ on each given partition...

```
sudo cp ./fstab ./fstab-backup
```

will create a new file called fstab-backup right next to the fstab file. so, if you want to undo your changes you can use the live cd to get back to /etc/ on that partition and use this to remove your modified fstab and restore the backup:

```
sudo rm ./fstab
sudo cp ./fstab-backup ./fstab
```

if you want to keep your modified fstab that broke the system, so you can look at it later and learn from your mistakes then run this to rename the broken fstab instead of 'rm' to remove it:

```
sudo mv ./fstab ./fstab-that-i-broke
sudo cp ./fstab-backup ./fstab
```
('mv' is to 'move' something... essentially the same as renaming it, in this case. 'moving' the contents of the file from ./fstab to a new file called ./fstab-that-i-broke)

that's three commands with 'sudo' that i gave you. as always, make sure you understand what the commands do prior to executing them to ensure i am not a bad guy giving you directions that will fry your system.... or, even if i am not a bad guy, it is possible i made a typo. so always double check what random-internet-person tells you to do!

manuals for rm, cp, and mv:
```
man rm
man cp
man mv
```

and while we are at it, the manual for fstab:
```
man fstab
```

there is also a great 'how to fstab' guide somewhere on these forums if you want to check that out.

---

