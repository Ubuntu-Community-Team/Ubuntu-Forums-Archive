---
title: "how to remove windows install i dont need it now."
date: 2012-05-29
forum: General Help
---

### Post by ytkuser12 on 2012-05-29
hey all how do i remove the windows partition and delete windows i like ubuntu better. and i have a new computer coming this week its a alianware so that will be my windows machine,and this will be my ubuntu machine. i have gparted installed from software center i see the windows partition. but it has a flag by it saying boot?. can i just delete this and then merge ubuntu into it?. or is there more i need to do.

---

### Post by wilee-nilee on 2012-05-29
> **ytkuser12 said:**
> hey all how do i remove the windows partition and delete windows i like ubuntu better. and i have a new computer coming this week its a alianware so that will be my windows machine,and this will be my ubuntu machine. i have gparted installed from software center i see the windows partition. but it has a flag by it saying boot?. can i just delete this and then merge ubuntu into it?. or is there more i need to do.

As long as your install was not from windows a wubi you can just delete it.

The wubi is a folder in windows, so if windows is gone so is the ubuntu.

The wubi can be transfered to a partition if needed.
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Many people install this way so just trying to make sure we and you know where you are at. :)

---

### Post by ytkuser12 on 2012-05-29
hi :) i did the fresh install off my usb stick so no wubi here. so if i delete it how would i get ubuntu to clame the space?

---

### Post by wilee-nilee on 2012-05-29
> **ytkuser12 said:**
> hi :) i did the fresh install off my usb stick so no wubi here. so if i delete it how would i get ubuntu to clame the space?

Use the live cd and gparted to resize the partitions.

You may have a extended type partition around the main ubuntu partition, if you do it has to be resized first.

A live cd should not have any partitions mounted by default, just make sure none are.

You can post a screenshot of gparted if you like for more concise help. :)

---

### Post by ytkuser12 on 2012-05-29
ok cool will boot into it thanks. still getting use to the fonts in this lol. trying to figure out what font google and firefox use on windows i like that one. might have to boot into windows and take a look.

---

### Post by deadflowr on 2012-05-29
You can use gparted in your instance from your normal installed ubuntu, as you are going to reformat the unmounted windows partition. I would recommend this way as running from a livecd will leave you vunerable to both your linux and windows partitions unmounted and you can accidentally quash the wrong one.

Here though is the guide I used along time ago, on how to add the extra space to fstab:

[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by ytkuser12 on 2012-05-29
thats confusing lol

---

### Post by Cheesemill on 2012-05-29
> **ytkuser12 said:**
> ok cool will boot into it thanks. still getting use to the fonts in this lol. trying to figure out what font google and firefox use on windows i like that one. might have to boot into windows and take a look.
To install the Windows fonts:
```
sudo apt-get install msttcorefonts
```

---

### Post by sky5564 on 2012-05-29
I would just back up all your files you want to keep then pop in the live cd and start over from scratch, But this time just do a full install.

After you are done you can pop in your usb drive or disc or what have you then you will be good to go.

Its good to make backups anyway in case a drive fails or something.

---

### Post by wilee-nilee on 2012-05-29
> **ytkuser12 said:**
> thats confusing lol

Yeah the peanut gallery feels the need to comment based on their own limitations and projected ones on other users.

The forum is like that, so just keep that in mind on posts. ;)

---

### Post by ytkuser12 on 2012-05-29
i figured it out will be doing it here shortly :). had one more question how do i adjust screen brightness?.

---

### Post by ytkuser12 on 2012-05-29
deleted it but had to put it back as i could not get the ubuntu install to extend to the new unallocated space. any ideas?

---

### Post by wilee-nilee on 2012-05-29
> **ytkuser12 said:**
> deleted it but had to put it back as i could not get the ubuntu install to extend to the new unallocated space. any ideas?

From a live cd post a screenshot of gparted.

---

### Post by ytkuser12 on 2012-05-29
here you go i hope this helps.

---

### Post by wilee-nilee on 2012-05-29
So as of now there is no free space.

The Ubuntu is in a extended partition as I mentioned sda2, this has to be resized before the sda5 can be. 

The swap needs to be unmounted as well, this will unmount the extended, and then it can be resized.

You may loose your ubuntu boot when you move the front of it to the left so be prepared for this, an easy fix so just a heads up.

You can fix this ahead of time by by tweaking the fstab, open it with this command.
```
sudo gedit /etc/fstab
```

Then remove the UUID and number and replace it with.

/dev/sda5

The UUID would look something like this.

UUID=540fba4f-32b3-460c-a3f4-7f9598fc9b25

You will have a boot then as long as the partition is sda5

---

### Post by ytkuser12 on 2012-05-29
ok so after i do all this will i need to re install the boot loader ?

---

### Post by wilee-nilee on 2012-05-30
> **ytkuser12 said:**
> ok so after i do all this will i need to re install the boot loader ?

If you change the fstab you should boot in alright, it may be, that you still will even if you don't change the fstab as well. Although on a couple occasions myself with moving the front of a Ubuntu partition I have had to reload grub to the mbr.

Couple of ways to get around this supergrub is one, it should boot you straight into a Ubuntu system that does not boot.

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

From the installed desktop you can from the terminal reload the mbr with these commands.

```
sudo fdisk -lu
```First command identifies the partitions and the HD, you just want to confirm the HD here, whether it is sda, or sdb etc. The next command puts grub in the mbr, the X is just the missing HD confirmation letter.
```
sudo grub-install /dev/sdX
```Then
```
sudo update-grub
```

---

### Post by ytkuser12 on 2012-05-30
lol i goofed it up had to do fresh install lol you live and learn.

---

