---
title: "result of separate installs on different hdd."
date: 2012-07-25
forum: General Help
---

### Post by techvish81 on 2012-07-25
yesterday i installed mint 13 on an extra hdd,  while keeping my main hdd with ubuntu  12.04 unconnected. now i want to know,  what will happen if i connect both the hdd and boot?
will it show both OSs to choose ? any chance of disturbing/breaking my main hdd OS ubuntu,  which i've configured to my way,  spending hours?

---

### Post by dino99 on 2012-07-25
each time a device is plugged/unplugged, its uuid change, meaning the previous uuid registered into grub will change too, resulting in boot failure.

to know uuid:  sudo blkid

to update uuid into grub : sudo gedit /etc/fstab

then : sudo update-grub

---

### Post by techvish81 on 2012-07-25
it means,  now if i connect the main hdd it will boot to the second hdd which is already connected.

now,  i think i will have to open nautilus with sudo and edit the fstab of main hdd installation.

am i right ?

---

### Post by Cheesemill on 2012-07-25
> **dino99 said:**
> each time a device is plugged/unplugged, its uuid change, 

Completely wrong.

The entire point of UUID's is that they don't change.


In response to the OP, you should just plug both drives back in and then boot whichever OS is in charge of GRUB on the first hard drive and issue:
```
sudo update-grub
```
This will detect the other OS and add it to your GRUB menu.

---

### Post by oldfred on 2012-07-25
I think Dino was thinking of an image copy from one drive to another which then creates duplicate UUIDs which then have to be changed.

As Cheesemill says just run sudo update-grub.

You should also be able to directly boot each install from BIOS or one time boot key (f12 on my system) as each should have its own grub2 boot loader in the MBR of its drive. That is always best case anyway as if one system does not boot, you can switch to other drive and  it should boot. If you run the sudo update-grub in both then both are updated.

---

### Post by techvish81 on 2012-07-25
> **oldfred said:**
> I think Dino was thinking of an image copy from one drive to another which then creates duplicate UUIDs which then have to be changed.

As Cheesemill says just run sudo update-grub.

You should also be able to directly boot each install from BIOS or one time boot key (f12 on my system) as each should have its own grub2 boot loader in the MBR of its drive. That is always best case anyway as if one system does not boot, you can switch to other drive and  it should boot. If you run the sudo update-grub in both then both are updated.

thank you very much for all the replies:-)


i think i would go with the above post and keep both grub and press f10 (in my system it is) to switch OSs by switching hdd boot order.

thank you oldfred for an expert advice.:-)

---

