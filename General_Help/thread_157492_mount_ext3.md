---
title: "mount ext3"
date: 2006-04-09
forum: General Help
---

### Post by neoroses on 2006-04-09
hey guys i have a hdd that is in  ext3..it isnt auto mounted, so could you just tell me how to mount it please =)

---

### Post by taurus on 2006-04-09
Open up a terminal with Applications -> Accessories -> Terminal.  Then, type
```

sudo mkdir /mnt/second  <-- create a mount point
sudo mount -t ext3 /dev/hdb1 /mnt/second  <-- assuming that your HD is /dev/hdb1!!!
df -h  <-- you should see it on the list now

```

---

### Post by PriceChild on 2006-04-09
how do you make it automount?

---

### Post by nanotube on 2006-04-09
[QUOTE=PriceChild]how do you make it automount?[/QUOTE]

put the proper line into the file /etc/fstab, that will make it mount at boot.
see "man fstab" for proper format, or find another thread that discusses it at length. :)

---

### Post by PriceChild on 2006-04-09
lol i know about fstab sorry.

I tried it myself, copying the line used for my current ubuntu, changing the location of it (hda1 etc.) changing the place it should mount to and trying that.

Didn't work though, kept breaking gnome and i had to go to terminal and take out the extra line again.

Could you gimme the standard line i should add, and i'll try again. Pricey

---

### Post by aysiu on 2006-04-09
Assuming it's /dev/hdb1 (check *sudo fdisk -l* to be sure), you'd do this: ```
sudo umount /dev/hdb1
sudo mkdir /second_drive
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` add in this line ```
/dev/hdb1 /second_drive ext3 defaults 0 0
``` Save. ```
sudo mount -a
sudo chown -R pricechild:pricechild /second_drive
sudo chmod -R 755 /second_drive
```

---

### Post by PriceChild on 2006-04-09
your method would make it mount into a folder called "second_drive" inside my home folder?

---

### Post by aysiu on 2006-04-09
[QUOTE=PriceChild]your method would make it mount into a folder called "second_drive" inside my home folder?[/QUOTE] No, it wouldn't be inside your /home folder. It'd be it's own folder. So you'd have

/bin
/boot
/etc
/home
/lib
/second_drive
/usr
...

---

### Post by PriceChild on 2006-04-09
Ah ok thanks very much :)

---

