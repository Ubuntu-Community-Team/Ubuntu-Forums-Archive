---
title: "Can not mount dmg image"
date: 2012-09-22
forum: General Help
---

### Post by sarikan on 2012-09-22
Greetings, 
After trying everything that I can think of for hours, I've finally given up. I just can't seem to mount a dmg image under ubuntu 12.04. I've updated all packages, I have the latest kernel available through ubuntu's update system. This is an 64 bit installation. 

I have a dmg image. I've converted it to img via dmg2img. I do modprobe hfsplus then try to mount it and I always and always get the following:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail says:

hfs: unable to find HFS+ superblock

This is really driving me mad. Nothing else worked, I've tried

sudo mount -t hfsplus javafx.img.iso jfxgui
sudo mount -t hfsplus -o loop  javafx.img.iso jfxgui
sudo mount -t hfsplus -o loop  javafx.dmg jfxgui
sudo mount -o loop  javafx.dmg jfxgui (gives me: you need to specify filesystem type etc)
...

you name it. 

What am I missing here?

---

