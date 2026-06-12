---
title: "xorg.conf , nvidia (dual-monitor) and Ubuntu 11.10"
date: 2011-11-28
forum: General Help
---

### Post by linux87n on 2011-11-28
Hi all!!

I just updated my version of Kubuntu to the 11.10 and i've got a big problem with my dual-screen settings.

After the upgrade (everything was right, no warnings or errors), i rebooted the machine and it didn't load the graphical interface. I solved this problem easily, deleting the xorg.conf file.

So, i deleted completely nvidia drivers, updated and reinstalled including the xserver-xorg-video-all. I can open my desktop but, if i try to access the nvidia settings, it says that xorg.conf is not located in /etc/X11 (obvious error), and if I run the nvidia-xconfig it creates it. But then i need to reboot to load the new configuration and......the system gets stuck again. To access graphical interface, the only way is to delete the xorg.conf.

My question is: how to set the dual monitoring???? Why do the nvidia drivers (although updated and xorg.conf is deprecated) creates that file that causes the boot problem?

Please help me, i need the dual monitoring to work.

PS: i can't use "nouveau drivers" because, even if they properly work, they are really slow in my computer.

Thanks!!!

---

### Post by dabl on 2011-11-28
> **linux87n said:**
> 

i rebooted the machine and it didn't load Linux. 

...

 then i need to reboot to load the new configuration and......the system gets stuck again. To access linux, the only way is to delete the xorg.conf.


I don't understand.  "Linux" is the operating system, not the graphical desktop/screen.  Are you saying you can't boot the computer at all, or are you saying that booting takes you only to the command-line prompt?

---

### Post by linux87n on 2011-11-28
Thanks for the reply,
with "Linux" i wrongly meant the graphical interface.
In every case I can access the command-line prompt, but i can start the graphical desktop only without the xorg.conf file. 

To enable the dual-desktop, the nvidia drivers need the xorg.conf file. So i donno how to solve this problem... :(

---

### Post by dabl on 2011-11-28
Can you boot "recovery" mode?  If so, there is a "Fix X" option on the recovery menu.  I would think that would restore either a VESA or the radeon driver.  Once you have either of those running by default, when you boot, then you can use the System > Additional Drivers menu (i.e. jockey-kde) to install the Nvidia proprietary driver.  I believe it will automatically run nvidia-xconfig to set up your /etc/X11/xorg.conf file.

---

### Post by linux87n on 2011-11-28
Thank you,
i tried to do so: 
1) because i don't have the xfix option in my recovery menu (i don't know why, i've only "resume, fsck, remount, root") i searched on internet behavior of this command and i found the xorg.conf file that it generates. I used it and the graphical interface loaded!
2) I deleted and updated my repository to install the last stable release of the nvidia drivers (as explained here [http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/](http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/)).
3) I create the xorg.conf file using the nvidia-xconfig.
4) After rebooting i got the same error but i was able to explore it. It says:
FATAL: error inserting nvidia-current: no such device.
failed to load the NVIDIA KERNEL MODULE
No screen found.

To come back to this forum, i had to remove again the xorg.conf and restart :(

---

### Post by dabl on 2011-11-28
Boot recovery mode.  At the menu, choose "drop to root prompt".  Run the "nvidia-xconfig" utility (you will not need "sudo" if you have the # prompt).

Now run

```
service kdm start
```

and see if you get a KDM greeter.

---

### Post by alterego2 on 2011-11-29
I have the same problem, nvidia-xconfig generates xorg.conf which doesn't allow kde to start. ThinkPad T520, nVidia Quadro NVS4200.

---

### Post by linux87n on 2011-11-29
> **dabl said:**
> Boot recovery mode.  At the menu, choose "drop to root prompt".  Run the "nvidia-xconfig" utility (you will not need "sudo" if you have the # prompt).

Now run

```
service kdm start
```

and see if you get a KDM greeter.

Unfortunately in recovery mode  i'm in "read-only" mode (my mistake?) but I tried your suggestion from the prompt without accessing KDE and i got the same troubles...

I've been playing with this for hours with no luck.
My kernel is 3.0.0 since the last system upgrade.
What d u think if a try to downgrade to the last kernel 2.x?

---

### Post by alterego2 on 2011-11-30
I found solution for my case:
1) remove all nvidia drivers from system: nvidia-* and nouevau drivers as well (e.g. xserver-xorg-video-nouevau) with apt-get remove
2) download new nvidia 290.10 drivers from nvidia [ftp]("ftp://download.nvidia.com/XFree86/Linux-x86_64/290.10/NVIDIA-Linux-x86_64-290.10.run")
3) shutdown laptop
4) set up BIOS: **Graphics Device** to **Discrete Graphics**. See recipe [here](http://www.thinkwiki.org/wiki/DisplayPort), under topic **Problems**
5)start laptop
6) Ctrl-Alt-F1, login as root
7) stop kdm: service kdm stop
8) install nvidia drivers: sh NVIDIA-Linux-x86_64-290.10.run
9) start kdm: service kdm start
10) login in kde
11) apt-get install nvidia-settings
12) setup 2nd monitor with nvidia-settings

---

### Post by linux87n on 2011-12-01
> **alterego2 said:**
> I found solution for my case:
1) remove all nvidia drivers from system: nvidia-* and nouevau drivers as well (e.g. xserver-xorg-video-nouevau) with apt-get remove
2) download new nvidia 290.10 drivers from nvidia [ftp]("ftp://download.nvidia.com/XFree86/Linux-x86_64/290.10/NVIDIA-Linux-x86_64-290.10.run")
3) shutdown laptop
4) set up BIOS: **Graphics Device** to **Discrete Graphics**. See recipe [here](http://www.thinkwiki.org/wiki/DisplayPort), under topic **Problems**
5)start laptop
6) Ctrl-Alt-F1, login as root
7) stop kdm: service kdm stop
8) install nvidia drivers: sh NVIDIA-Linux-x86_64-290.10.run
9) start kdm: service kdm start
10) login in kde
11) apt-get install nvidia-settings
12) setup 2nd monitor with nvidia-settings

Thanks to your suggestions, i got my dual screen back!!! 

But in my case it wasn't enough. I ha to download the file NVIDIA-Linux-x86-96.43.20-pkg1.run because my graphic card is not recognized by the version 290. It caused the conflict everywhere, even in the xserver-xorg files. Resuming, the steps I did are:

- remove everything about nvidia (sudo apt-get remove --purge nvidia-*)
- downgrade the drivers:   xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-radeon 
- install nvidia drivers: sh NVIDIA-Linux-etc...

The problem is that the uploader is always asking to upload the file i downgraded, and if i update them then i got stuck again with the same problem.

I hope this can help somebody!

my graphical card is GeForce FX 5200

Does anybody know how to disable the updating of specific drivers?

---

