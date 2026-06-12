---
title: "Help, one of my partitions has disappeared!"
date: 2010-11-09
forum: General Help
---

### Post by dr_dexter on 2010-11-09
Hi all,

I have a serious problem here with my laptop. I currently have Windows 7 and Ubuntu 10.10 in my computer, and I was booting normally with grub until last night. I tried to install Adobe Photoshop into Windows and after that I went on to reboot my system. When it restarted, grub showed a message like this:

error: no such partition
grub rescue>

I've followed some advice regarding this issue and I got this running the bash script (boot_info_script0555.sh) mentioned in some related posts. Here is my RESULTS.txt output.

After a quick view, I think the biggest problem is that one of my Linux partitions has disappeared, and I don't know how to recover it. Please help me to find out a solution for this.

Thanks in advance!

---

### Post by webtechquery on 2010-11-09
Hi there..

I think I also had the same problem while installing Ubuntu 10.10, but due to installation failure, this error occurred while rebooting.
What I did was, I simply installed Ubuntu's previous version (10.04) in another partition, and after installation, all went fine as before.

Sorry I dint get the proper solution yet, but this was what I did and it resolved.

Thanks.

---

### Post by dr_dexter on 2010-11-09
Thanks for your help webtechquery, but I'm not sure if doing so I'd be able to recover my files. Could you guys show me how to at least recover them? I have some important university work there and I must save it! How can I get into Linux file system (folder /home)?

---

### Post by JC Cheloven on 2010-11-09
Hi, from that script, it seems that there isn't a linux OS installed in any partition. 

But just to be sure,  first of all boot from live cd/pendrive and find out what partitions are shown. 
You can use gparted for that, or those commands from terminal whose output you can post back here if needed
```
sudo blkid
```  ```
sudo fdisk -l
```

Let's suppose (the most probable imo) that you actually have the ubuntu partition, and that is only the grub bootloader what is screwed. If so, and still from live, please follow the instructions here to reinstall grub in your disk (method 1 "simplest" should suffice)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

EDIT: 
In a second read, if you have reached the "script stage", you may also have tried what I said, as you may have run the script from live. 
If it's the case, then you need "advanced" recovery tools to make accesible your lost partition (was it /dev/sda7 at installation? had you a separated /dev/sda6 for home?). In this link  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) you'll find a variety of tools. Please note the advice about triyng to not write to the disk but cloning it and recovering from that, to avoid data overwritting. 
Hope this helps.

---

### Post by dr_dexter on 2010-11-09
Yes, I tried to run fdisk before running the script with the same results. It's unbelievable, the Linux partition has suddenly disappeared. Can anybody confirm if my data in /home is still recoverable? How can I do it?

Thanks in advance

---

### Post by Grenage on 2010-11-09
> **dr_dexter said:**
> Yes, I tried to run fdisk before running the script with the same results. It's unbelievable, the Linux partition has suddenly disappeared. Can anybody confirm if my data in /home is still recoverable? How can I do it?

Thanks in advance

Ok, first things first, since your data is important:

Change nothing on your computer.
Download and burn an Ubuntu ISO (if you don't have one to hand - another live distro is also fine).
Boot from the CD (as a Live CD, don't install it).
Copy your data off (can you see it?)

---

