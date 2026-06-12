---
title: "No GDM no X, nothing"
date: 2009-12-07
forum: General Help
---

### Post by Eragon0605 on 2009-12-07
When I attempt to boot Ubuntu 9.10 Karmic, I get the boot-up screen with the white ubuntu logo, then i get a command prompt saying:
```
Ubuntu 9.10 dck-destop tty1
dck-desktop login:
```I tried entering
```
sudo /etc/init.d/gdm start
```and
```
sudo update -rc.d gdm defaults 13 01
```after searching Ubuntu Forums and entered the Ctr+Alt+F7, but neither work. The problem started when I was playing SPORE under Wine. After quitting SPORE, my computer stopped responding; it wouldn't do anything. Not even pressing the power button worked. I had to press and hold the power button to get it to shut off. After restarting, this problem presented itself. My boot options are:
```
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
```I tried them all (except Window$ 7 and Memtest) and they all had the same problem.

---

### Post by MooPi on 2009-12-07
Let the computer sit and cool, before attempting further. The game may have over heated a component and caused shutdown.

---

### Post by Eragon0605 on 2009-12-07
No, I thought of that and checked it in Window$, everything is at normal temps. In any case, I have been trying to fix the problem for 3 days now...

Edit: Oh, and a potentially important bit of info is that this was the first time I ran SPORE under Linux 2.6.31-16 generic.

---

### Post by lloyd_b on 2009-12-07
Login and type "startx".  This should ideally start up X, but if there's something wrong with X it'll hopefully give you an error message telling you what the problem is.

Lloyd B.

---

### Post by ElSlunko on 2009-12-07
startx or initx should bring you to x

---

### Post by Eragon0605 on 2009-12-08
Alright, I type 'start', my screen goes blank for a second, then I get this:
```
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implimented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec  7 22:26:41 2009
(==) Using default built-in configuration (30 lines)
(EE) open /dev/fb0: No such file or directory
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) config/hal: couldn't initialize context: unknown error (null)

waiting for X server to shut down error setting MTRR (base = 0xd000000, size = 0x10000000, type = 1) Invalid argument (22)
 ddxSigGiveUp: closing log
```
Sorry if there are any typos, couldn't exactly cut 'n paste...

---

### Post by lloyd_b on 2009-12-08
Do you have a Nvidia graphics card?  If so, [look at this]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/492121") (sorry, it's not a solution, just a bug report).

Lloyd B.

---

### Post by gradinaruvasile on 2009-12-08
Rename xorg.conf:

sudo mv /etc/X11/xorg.conf $HOME

then reboot

---

### Post by FearfulJesuit on 2009-12-08
So I have an nVidia graphics card and I had this same exact problem running some other program. The program crashed and wouldn't open. So I rebooted and found myself with nothing showing up. 

So what I did was I went ahead and logged in. Then you want to reinstall your nVidia driver and startup module. 

First, uninstall whatever nvidia driver you have. I believe the options are 96, 173, 185 and some others. 
```

sudo aptitude remove nvidia-glx-version
```Then

```
sudo reboot
```Then 

```
sudo apt-get install nvidia-glx-version
```This should reinstall all the necessary modules and allow you to see your desktop and other things.

If this doesn't help, you may want to try installing some of the open source drivers like vesa or xserver-xorg-nv.

---

### Post by gradinaruvasile on 2009-12-08
The nv driver is already installed. Its part of the Xserver along with all opensource drivers. If the xorg.conf is removed, the server will generate a new configuration with the opensource driver (it used to work eith the dpkg-reconfigure command but as of Karmic it doesnt work) - it doesnt matter if the restricted driver is installed or not, it will not be activated. 

Then the nvidia-glx package should be reinstalled.

---

### Post by FearfulJesuit on 2009-12-08
> **gradinaruvasile said:**
> The nv driver is already installed. Its part of the Xserver along with all opensource drivers. If the xorg.conf is removed, the server will generate a new configuration with the opensource driver (it used to work eith the dpkg-reconfigure command but as of Karmic it doesnt work) - it doesnt matter if the restricted driver is installed or not, it will not be activated. 

Then the nvidia-glx package should be reinstalled.

So I want to learn a little bit more about this...
Vasile, is it possible for him to change the xorg.conf file to pick up the vesa or xorg-nv driver?

---

### Post by gradinaruvasile on 2009-12-08
More simple than that: as i said, just delete it. It seems the default settings are kept somewhere alse in the newer version of X because i did remove this file on several occasions and it wasnt regenerated. So the default settings are somewhere else.
And for nvidia cards, the defaults mean the nv driver.

However it will be regenerated by nvidia-xconfig when the driver is reinstalled. I would say run a "sudo nvidia-xconfig" in a terminal just to be sure.

---

### Post by lloyd_b on 2009-12-08
> **gradinaruvasile said:**
> More simple than that: as i said, just delete it. It seems the default settings are kept somewhere alse in the newer version of X because i did remove this file on several occasions and it wasnt regenerated. So the default settings are somewhere else.
And for nvidia cards, the defaults mean the nv driver.

However it will be regenerated by nvidia-xconfig when the driver is reinstalled. I would say run a "sudo nvidia-xconfig" in a terminal just to be sure.

You are assuming that there *is* an "xorg.conf" file.  The default configuration is compiled into Xorg now, so there may not be one.```
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implimented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec  7 22:26:41 2009
**(==) Using default built-in configuration (30 lines)**
(EE) open /dev/fb0: No such file or directory
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) config/hal: couldn't initialize context: unknown error (null)
```The bolded line above indicates that it is using its default configuration, rather than xorg.conf.

Lloyd B.

---

### Post by Eragon0605 on 2009-12-08
Thanks for all the suggestions. I reinstalled nvidia-glx-185 and ran nvidia-xconfig. I then rebooted and I got a nice black screen again. I ran xstart, and I get a similar error message, this time saying to reinstall my NVIDIA drivers. I just reinstalled them! It wouldn't be awfully terrible if I had to reinstall Ubuntu, but I would rather not.

---

