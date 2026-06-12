---
title: "Ubuntu 9.10 Wont Start =/"
date: 2010-05-20
forum: General Help
---

### Post by Yesirom on 2010-05-20
Hey. I have a problem.

Everything was perfectly fine until today when I started my pc and choose to boot into Ubuntu 9.10.

It would go past the logo and now I only get a black screen and can't do nothing.

I think it's a problem with Xorg but I'm not experienced with this stuff so I ask of you for help. I'm really confused xD

I also tried to put in a Karmic and Lynx Live CD but it fails at the desktop loading part , just says "no input signal" on monitor.

---

### Post by Yesirom on 2010-05-22
Anybody?

---

### Post by albinootje on 2010-05-22
> **Yesirom said:**
> 
It would go past the logo and now I only get a black screen and can't do nothing.

Please try the "recovery mode" from the grub boot menu. I think that in 9.10 you have to hold the "right shift" key to make the grub visible.

Perhaps your / partition (or the partition where /tmp lives) is full, this is a possible reason that X can't start.

---

### Post by Yesirom on 2010-05-22
I tried many things till now but none of them work...

Can you tell me exactly what to do?

---

### Post by Yesirom on 2010-05-24
> I figured it out. Guess the problem was caused by a upgrade which affected the manual installed ATI drivers I had.

First to get the login screen I used a radeonhd driver which I installed via command line in the Recovery mode.

```
sudo apt-get install xserver-xorg-video-radeonhd
```

Here are the two xorg.conf files which my friend gave me. Use the radeon hd one preferably for now (it should work).

*SEE ATTACHMENT BELLOW POST*

I used this xorg.conf file from another card just to get me started.

Backup your original xorg.conf and delete it in /etc/X11 and replace it with this.

Mine xorg.conf was on another partition for safe keepings (just run Ubuntu from a Live CD and replace the file). If you cant get the Live CD to work and have dual boot then try this. 

1. Have the file ready on your partition 

2. Boot to Recovery mode and get to terminal or boot Ubuntu normally and try (CTRL+ALT+F2) to get the console

3. Type sudo fdisk -l to see the name of you partition (sda something, sda5 in my case)

```
sudo mkdir /media/Backup

sudo mount -t ntfs /dev/sda5 /media/Backup

sudo cp /media/Backup/radeonhd/xorg.conf /etc/X11/xorg.conf
```

I hope you understand it, it just makes a folder "Backup" in your media folder and appends your partition to it , if you do the "ls" command you can see your folders and files.

Also "sudo reboot" is very useful for rebooting. Before rebooting try to disable compiz.

```
metacity --replace
```

```
sudo /etc/init.d/gdm restart
```

because it gave me a white screen when I logged in but if you cant disable it just use "FAILSAFE GNOME" option in the login screen and then disable compiz when you get inside (dont forget to go back and choose GNOME instead of FAILSAFE again".

Reboot. You should get a decent working system (dont worry about the resolution , we have just started). 

Next I uninstalled all ATI drivers (fglrx)

```
cd usr/share/ati
```
```
sudo sh ./fglrx-uninstall.sh
```
```
sudo rm -R /etc/ati
```

then I uninstalled everything FGLRX from synaptic (type fglrx in search and remove the packages you find).

Next I downloaded the official driver from [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) for my video card.

Typed in terminal 

```
sudo sh ./ati-driver-installer-10-4-x86.x86_64.run
``` 

I used automatic , then after the install i ran

```
/usr/bin/aticonfig --initial
```

Rebooted and everything works perfect now. I guess they updated something in the driver (28.4 was the last update) to make it compatible.

Well sure you guru ubuntu users think why didn't you just install it from Hardware Devices.

Well I tried but It didn't work for me, I always got the "unable to initialize PCS database" so this works like a charm.

If you have this kind of issues then all above might not work on you but just keep on trying. 

The most important thing is to fix the Xorg.conf in your /etc/X11 folder to boot properly in your system.

Also what can help for precaution measures is when you get to grub press "E" to modify the boot parameters, type "nomodeset" at the end of the kernel line.

```
kernel /boot/vmlinuz26 {...} nomodeset
```

That line.

This trick is only for ATI Radeon cards because the drivers dont support KMS (dont ask me what that is because I'm no expert for this).

**extra:**

If you want to make the nomodeset permanently so you dont have to type it again and again after every reboot in the console type:

```
sudo nano /etc/default/grub
```

and add the nomodeset

```
GRUB_CMDLINE_LINUX="quiet splash nomodeset"
```

then press CTRL+ALT+X and press Y to confirm and ENTER. You are done.

Now you only have to type in 

```
sudo update-grub 
```

to update grub.

I hope this will help someone. I spent 2 hours writing this :D

---

