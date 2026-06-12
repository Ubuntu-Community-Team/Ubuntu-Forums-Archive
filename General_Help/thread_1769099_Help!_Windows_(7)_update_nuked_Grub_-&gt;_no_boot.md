---
title: "Help! Windows (7) update nuked Grub -&gt; no boot"
date: 2011-05-27
forum: General Help
---

### Post by Naggobot on 2011-05-27
I have multi booting Ubuntu 10.04 / Windows 7 installation. 

After **Windows update** the grub menu is gone and computer is stuck in boot-reboot cycle with just a non blinking cursor. 

Boot info script is attached. I am currently using Live usb (32bit) and the Ubuntu installation is 64 bit.

How can I restore the boot grub / boot menu?

Can I follow these instructions safely

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by piratebill on 2011-05-27
I'd try reinstalling grub, which is what the article says to do.  Using the live cd can you at least see your files on the drive?

---

### Post by Naggobot on 2011-05-27
Yes I can 

Following the instructions as I write.

---

### Post by lmarmisa on 2011-05-27
You need to reinstall GRUB ([COLOR="Red"]use a 64 bits Ubuntu Live USB!!![/COLOR]) :

[https://help.ubuntu.com/community/Gr...ing%20GRUB%202](https://help.ubuntu.com/community/Gr...ing%20GRUB%202)

Open a terminal and type these two commands:

```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

Reboot the system normally and type this command:
```

sudo update-grub

```

---

### Post by piratebill on 2011-05-27
> **Naggobot said:**
> Yes I can 

Following the instructions as I write.

If you are really worried about "being safe" back up your files first.  Though I cant imagine anything going wrong with reinstalling grub

---

### Post by Naggobot on 2011-05-27
Dang, Hasty as I am I Missed the instructions by Imarmisa. I would have saved a few empty empty hear beats

I was unsure about the last bit in 

```
sudo grub-install --root-directory=/media/40508207-89dc-4cad-b4d4-4ed31893e41b /dev/sda
```and of course I inputted the wrong end and pointed the Grub installation to /dev/sda5 instead of /dev/sda. Luckily Grub installer was smart enough not to install the grub there. So if you try this at home, do not do that error. 

Hasty as I am I also used the 32 bit live USB so I suspect shall consider doing it once more since there was some unnecessary flickering in the boot up. I may have imagined that also so I need to sleep over it.  Especially since Ubuntu is now booting fine and I have difficulty finding info on the subject (except that Kernel sets the processor to 32 bit or 64 bit)

At this point I would like to offer gazillion thanks to every one participated in making of Grub. I also shall  not update windows 7 ever again if even remotely possible to avoid.

And no I did not bother to back up since I am just setting up a new computer (two days old) and I would not have known how to back up all of the work I have to installing and configuring anyhow.

---

### Post by aaronLund on 2012-12-02
el-subscribe-o.

Grazi!

---

