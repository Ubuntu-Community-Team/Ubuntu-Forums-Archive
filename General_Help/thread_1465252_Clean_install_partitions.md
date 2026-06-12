---
title: "Clean install /partitions"
date: 2010-04-29
forum: General Help
---

### Post by Hydrokys on 2010-04-29
I am going to do a clean install of windows 7 and Ubuntu. I have 2 hdd's. a 500 and a 320gb. Windows 7 on the 500 and Ubuntu on the 320. I want to be able to access and share my pictures, music, videos, and documents from linux. I dont need to access files in Ubuntu from windows. On my windows 7 drive i usually have a seperate partition for the user files. I would like to know how i should partition Ubuntu  with 320gb and if i need to do anything special to be able to access the files mentioned from linux?

---

### Post by dino99 on 2010-04-29
to format your hdd, the best tool is [http://partedmagic.com/](http://partedmagic.com/)

drop it on a cd or usb stick, then boot with it and start formatting:

- a main partition to install ubuntu: about 10-12 go named / and you have to choose it as the bootable partition

- a swap partition: about twice your ram and named swap

- a user partition for your data, named /home

/home and / are formated as ext3 or ext4

when you format , take note of their path ( ie /dev/sda, /dev/sdb, ...) you will be asked on which partition you want to install ubuntu. The bootloader have to be installed on /dev/sda.
The first time you boot on ubuntu, into console, run:
- sudo grub-mkconfig
- update-grub

this will find windows. ubuntu is able to write/read windows files, if you give it the rights with mountmanager

---

