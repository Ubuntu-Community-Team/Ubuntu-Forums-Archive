---
title: "XP/Ubuntu/Kubuntu. If I delete Kubuntu, what's happen to my boot cycle?"
date: 2010-03-31
forum: General Help
---

### Post by Roasted on 2010-03-31
XP Pro SP3
Ubuntu 9.10
Kubuntu 9.10

Tri-booting. They were installed in the order I listed above.

I ran into a few bugs with Kubuntu, so I no longer want to use it. I want to use GParted on a LiveCD to format Kubuntu and expand my Ubuntu home partition to sit on top of Kubuntu's space right now.

If I nuke Kubuntu, will Grub still exist with my Ubuntu/XP entries to boot?

---

### Post by burton247 on 2010-03-31
That depends whether you installed grub when install kubuntu. As long as you know what is installed where (or find out using gparted) you can find out where grub is.

Load up grub interface

```
sudo grub
```

then find it

```
find /boot/grub/stage1
```

This should return where your grub partition is. If it with ubuntu thats good. If its with kubuntu then youll lose it. Its really easy to restore from a liveCD though

---

### Post by Roasted on 2010-03-31
Am I not allowed to run sudo grub in my Ubuntu partition? it comes back with command not found.

---

### Post by burton247 on 2010-03-31
could try sudo /sbin/grub

But im guessing grubs not installed, do you have a menu.lst file on this partition?

---

### Post by oldfred on 2010-03-31
If you have a new install of 9.10 you have grub2. Boot into Ubuntu and reinstall grub from there before deleting.

reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

---

