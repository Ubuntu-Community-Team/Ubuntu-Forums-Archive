---
title: "Dualboot Ubuntu after Suse"
date: 2010-05-26
forum: General Help
---

### Post by any.linux12 on 2010-05-26
Hi!

If I install ubuntu 9.04 after opensuse 11.1 does ubuntu respect the installation and I get a dualboot system? I already tried the oposite and it didn't work.

Thanks

---

### Post by garvinrick4 on 2010-05-26
> **any.linux12 said:**
> Hi!

If I install ubuntu 9.04 after opensuse 11.1 does ubuntu respect the installation and I get a dualboot system? I already tried the oposite and it didn't work.

Thanks
If you are going to boot into different linux OS's you are going to have to learn how to
use a LIVE CD and replace your grub of choice after install. If you make sure you always
put grub in sda and not sda1 or sda2, ect. ect. ect. the last installations grub or boot manager will be installed then go straight to a LIVE Cd and mount your partition with grub installed lets say your ubunu linux is in sda5 and you gave it a label of maverick. I like to label all my partitions for convenience of mounting when more than one install.

Make a directory
```
sudo mkdir /media/maverick

```Mount partition with grub.
```
sudo mount /dev/sda5 /media/maverick

```install grub to sda (over writes any other boot manager)
```
sudo grub-install --recheck -root-directory=/media/maverick /dev/sda
```unmount partition (not a typo)
```
sudo umount /media/maverick

```When it says installed ok. Shutdown remove CD and restart will now have grub menu
with selections of OS's.

---

### Post by any.linux12 on 2010-05-26
> **garvinrick4 said:**
> If you are going to boot into different linux OS's you are going to have to learn how to
use a LIVE CD and replace your grub of choice after install. If you make sure you always
put grub in sda and not sda1 or sda2, ect. ect. ect. the last installations grub or boot manager will be installed then go straight to a LIVE Cd and mount your partition with grub installed lets say your ubunu linux is in sda5 and you gave it a label of maverick. I like to label all my partitions for convenience of mounting when more than one install.

Make a directory
```
sudo mkdir /media/maverick

```Mount partition with grub.
```
sudo mount /dev/sda5 /media/maverick

```install grub to sda (over writes any other boot manager)
```
sudo grub-install --recheck -root-directory=/media/maverick /dev/sda
```unmount partition (not a typo)
```
sudo umount /media/maverick

```When it says installed ok. Shutdown remove CD and restart will now have grub menu
with selections of OS's.

I already did that once when I installed a windows system after an Ubuntu and I wanted to get it back to work. I though that it should work with no problem but the workaround should be okay.

---

### Post by garvinrick4 on 2010-05-26
If you are going to have Windows in a dual boot it just seems it is a lot easier on user and
grub install just to install Windows first and then make a extended partition and put Ubuntu
in a logical partition inside of the extended. You only use 2 primary partitions and everything just works. Linux first and Windows second is just a pain in the rear.

---

