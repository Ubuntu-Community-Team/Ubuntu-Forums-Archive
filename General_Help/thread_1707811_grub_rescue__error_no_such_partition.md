---
title: "grub rescue / error: no such partition"
date: 2011-03-15
forum: General Help
---

### Post by Zero33 on 2011-03-15
I guess I messed up my GRUB by deleting my ubuntu partition and reformatting it. I was using ubuntu netbook remix and Windows XP. I am on a HP mini 311. 

How can I boot up windows? I want to delete ubuntu and just boot it up to XP. I am a complete newbie when it comes to ubuntu. 

Please help.


Thanks.

---

### Post by Zero33 on 2011-03-15
I can't start my computer up at all..

all I get is...

error: no such partition
grub rescue>



Can anyone help?

---

### Post by drs305 on 2011-03-15
Do you have the Ubuntu "LiveCD" on a bootable thumb drive?

If so, boot Ubuntu and run the following commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Don't run any other lilo commands.

This should restore the main drive MBR to point to your Windows boot files.

---

### Post by Zero33 on 2011-03-15
Ok so I am running Ubuntu off an USB stick.

After running those commands, I get some errors. 

After running:
```
sudo apt-get install lilo
```

I get:
```
DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
cp: cannot start '/vmlinuz': No such file or directory
dpkg: error processing bcml-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Error were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

After running:
```
sudo lilo -M /dev/sda mbr
```

I get:
```
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of /dev/sda has been updated
```


Does all this look right? I should be able to restart my computer after doing this and it should boot up correctly? I did this and I still get to the same problem. The GRUB rescue screen.

Help please and thanks!

---

### Post by Rubi1200 on 2011-03-16
We need to get a better overview of the current state of the system.

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

### Post by kjs12 on 2011-04-04
Hi. I love Ubuntu but since I installed it I hated GRUB2 after getting fedup with it and deciding Linux was no longer worth the Grub, I had the same problem as zero33. 
So now I have a passionate hate that burns white hot for the Grub. Nothing would fix the MBR, not windows recovery, not Rescatux, combing thru forum after forum, I even tried blessing it with a sacrafice, y nada! nothing worked until I found this simple suggestion in this obscure thread. And now it's a productive computer again and not a BRICK.
This will probably be my first and last posting on this forum and I just want to say, THANK YOU! to drs305.

---

### Post by drs305 on 2011-04-04
> **kjs12 said:**
> This will probably be my first and last posting on this forum and I just want to say, THANK YOU!

kjs12,

You're always welcome to come and go as you please at the Ubuntu forums. If you ever find yourself cursing at Ubuntu, come on back and we'll do our best to turn things around. You've already taken the time to register, so the next time will be even easier.  

And besides, us *alphanumerics* have to stick together. :-)

---

