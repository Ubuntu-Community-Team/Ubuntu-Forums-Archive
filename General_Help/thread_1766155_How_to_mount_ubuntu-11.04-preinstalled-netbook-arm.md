---
title: "How to mount ubuntu-11.04-preinstalled-netbook-armel.img"
date: 2011-05-24
forum: General Help
---

### Post by vanloswang on 2011-05-24
How to mount ubuntu-11.04-preinstalled-netbook-armel.img .I am working on porting ubuntu netbook edition to my MID which is running Android with samsung s5pv210 .I tried xubuntu 9.10 and it works well without touchscreen .Now I choose ubuntu-11.04-preinstalled-netbook-armel for the one I will work on .But I can't mount it with the command following:

sudo mount -o loop ubuntu-11.04-preinstalled-netbook-armel.img /mnt .

Also I add -t ext4 or -t ext3 and turn out to be an error .I tried cpio but it's not this format .
I just don't want to follow the way that use the command dd to write the image into SD card .What I need is the pre-installed rootfs .So I should mount this image and extract the filesystem .
Any idea will be appreciated .

---

