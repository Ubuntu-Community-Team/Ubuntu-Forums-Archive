---
title: "Prefix error shows up while booting with the USB stick!!!"
date: 2012-06-12
forum: General Help
---

### Post by ShankyTrip on 2012-06-12
hello all.
i have an iso image of ubuntu 12.04 x64 .i used a 2gb data traveller usb stick.and made bootable using unetbootin.
everything looked good and the windows asked me for a reboot.
although when i did so an error message flashed "preix not set " and then the screen with the options of trying,installing,checking occured.selecting anyone of them did not help at all.it stalled!!!
have tried it more than 20 times since last night but of no avail.
i have ASUS K53SM laptop.
help needed.Thanks

---

### Post by ShankyTrip on 2012-06-12
Any help would be appreciated ////
please and thanks

---

### Post by oklokl on 2012-06-12
In my case, do not use anything else.

sudo parted -l
#view

sudo dd if=/dev/zero of=/dev/sdXy bs=446 count=12453
# remove usb

cd ~/Downloads
dir

# file32.iso

sudo dd if=file32.iso of=/dev/sdXy bs=1M
# linux os.. make iso usb..


or..
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)
windows usb make Tip
ntfs-3g > usb format..
sudo mkfs.ntfs -f /dev/sdXy

Hash
md5sum ~/Download/*.iso > txt
cat txt

---

