---
title: "grub rescue&gt; error"
date: 2011-03-10
forum: General Help
---

### Post by abros2k11 on 2011-03-10
Hi I am a newb;
recently I tried to dual boot the win7 with ubuntu 10.10, the installation worked fine. i also got the boot option using easybcd software. but wen i selected ubuntu from the boot option I am getting grub rescue error. although I know I have installed grub on different location.
Then I tried these commands in terminal:
sudo fdisk -l;
sudo mount /dev/sd8/mnt

but at this point im getting following error: (dont remember exact word)
mount: cannot find /dev/sd8/mnt

please help

---

### Post by abros2k11 on 2011-03-10
Hi I am a newb;
recently I tried to dual boot the win7 with ubuntu 10.10, the installation worked fine. i also got the boot option using easybcd software. but wen i selected ubuntu from the boot option I am getting grub rescue error. although I know I have installed grub on different location.
Then I tried these commands in terminal:
sudo fdisk -l;
sudo mount /dev/sd8/mnt

but at this point im getting following error: (dont remember exact word)
mount: cannot find /dev/sd8/mnt

please help

---

### Post by abros2k11 on 2011-03-10
Hi I am a newb;
recently I tried to dual boot the win7 with ubuntu 10.10, the installation worked fine. i also got the boot option using easybcd software. but wen i selected ubuntu from the boot option I am getting grub rescue error. although I know I have installed grub on different location.
Then I tried these commands in terminal:
sudo fdisk -l;
sudo mount /dev/sd8/mnt

but at this point im getting following error: (dont remember exact word)
mount: cannot find /dev/sd8/mnt

please help

---

### Post by bapoumba on 2011-03-10
Threads merged.

---

### Post by Rubi1200 on 2011-03-12
Hi and welcome to the forums abros2k11 :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

