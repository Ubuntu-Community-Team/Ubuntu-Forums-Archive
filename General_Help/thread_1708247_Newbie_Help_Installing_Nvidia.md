---
title: "Newbie Help Installing Nvidia"
date: 2011-03-16
forum: General Help
---

### Post by Quarkrad on 2011-03-16
Sometime back my Nvidia card blew up and I had to order a new one -problem was I had to run in Failsave graphics.  I posted for help and got this reply that worked:


[COLOR="Blue"]If you have not change /etc/X11/xorg.conf and have not install any graphics drivers,

"Application" -> "Accessory" -> "Terminal"

$ gksu gedit /etc/default/grub

Change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa"

Save and quit text editor.

Execute
$ sudo update-grub
in order to activate the change[/COLOR]


This was great - I started in Failsave graphics each fresh boot.  New Nvidia card arrived today and installed but I cannot loaded the drivers.  *System/Admin/Additional Drivers* tells me I have the Recommended Driver installed but when I go *System/Admin/Nvidia Server Settings* I'm informed 

[COLOR="Blue"]You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/COLOR]


I open terminal as root and type nvidia-xconfig and I get:

[COLOR="Blue"]dad@dadubuntu:~$ sudo su
[sudo] password for dad: 
root@dadubuntu:/home/dad# nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'[/COLOR]

Now - I have changed Grub (actually Burg but the grub commands worked in Burg) and I think I may have to change grub/burg as well as accessing this xconfog file.  Any help appreciated.

---

### Post by seawolf167 on 2011-03-16
Removed double post

---

### Post by seawolf167 on 2011-03-16
Just change this line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa"
```

back to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

i.e.

```
sudo vi /etc/default/grub
```

then re-update grub

```
sudo update-grub
```

and you should be ok (restart the computer after to test it out and make sure it starts correctly). The computer won't automatically start in failsafe graphics mode and your new Nvidia drivers should work on boot.

---

### Post by Quarkrad on 2011-03-16
Sorry - all it needed was a reboot.  I keep getting caught out by this - windoz needed rebooting after changing anything - Ubuntu/Linux hardly ever needs rebooting but every now and again it does. I'm learning that anything to do with graphics it is best to reboot.  Sorry for posting too soon.

---

### Post by seawolf167 on 2011-03-16
Basically, anything that touches graphics drivers you should reboot, or at least logout/login, but you'll always have to reboot after updating or changing your kernel

---

