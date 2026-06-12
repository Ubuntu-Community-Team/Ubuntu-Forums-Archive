---
title: "Calling All Guru's - Please Help"
date: 2009-12-29
forum: General Help
---

### Post by dxtac1 on 2009-12-29
[COLOR=black][FONT=Verdana]About a week ago I started having issues with Karmic freezing. I've read in this forum this may be due to a plethora of things but I'm believing it may have been either Rhythmbox and or the Torrent agent being left open then the system not being able to recover from standby or the graphics card. Anyway that's the least of my problems right now. Yesterday I fired up the pc and the updates began to install. About half way through the install the screen went black and froze. I had been doing hard shut downs in the past week or so as no keyboard combinations would work after the machine freezes. After start up I now get "dxtac@dxtac-homepc:~$". [/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]I was working with a fellow forum "Guru" and tend to agree that it *_may_* be due to my Nvidia GeForce 6100 graphics card and a kernel update not playing nicely together. We tried to go online to "wget http://tinyurl.com/y9dtms4" to update the drivers with no success. I did download the drivers to a thumb drive and through trial and error I believe we successfully downloaded the drivers to the machine however, I am back to square one as when I boot it asks for my username and password and brings me back to "dxtac@dxtac-homepc:~$"[/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]I very recently switched all of my pc's over to Ubuntu in the hopes that I was leaving these goofy issues behind with MS. My netbook and notebook updated without issue, I am afraid to update my other pc for fear of this happening to that machine as well. [/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]Any and all help would be GREATLY appreciated. If I could just "Restore" back to a week ago that would be great or if anyone has any suggestions I am open. Also, if it appears the graphic card is the issue, is their a card that is recommended that works seamlessly with Ubuntu??[/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]Thanks in advance,[/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]Derek[/COLOR][/FONT]

---

### Post by Mahngiel on 2009-12-29
To clarify: After you log in at boot, you get kicked to the terminal (xterm) and are without GUI?

---

### Post by Mahngiel on 2009-12-29
> **phidia said:**
> What happens when you type ```
 startx
``` and press the enter key at that prompt? You may find some helpful info by typing dmesg <enter> and checking xorg logfiles in /var/log too.

try this and see what's up

---

### Post by dxtac1 on 2009-12-29
I tried "startx" and it gave me a whole string of things but the more interesting items are as follows:
 
I can't scroll up to read this entire line but this is the jist: 
but this NVIDIA driver component has version 190.53. Pleas make sure that the kernel module and all NVIDIA driver components have the same version.
NVIDIA failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.
***Aborting***
Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens foud
 
Please consult the X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help.
 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
 
ddxSigGiveUp: Closing log giving up
 
xinit: No such file or directory (errno 2): unable to connect to x server
xinit: No such process (errno 3): Server error
[EMAIL="dxtac@dxtac-homepc:~$"]dxtac@dxtac-homepc:~$[/EMAIL]
 
It sounds like NVIDIA and Ubuntu don't like each other very much. Would it be easier to go and buy a non-NVIDIA card and be done with it? I have NO problem with that. What's a good compatible brand???
 
Thx,
 
Derek

---

### Post by ibuclaw on 2009-12-29
It actually sounds like you have multiple versions of NViDIA installed - and the conflict is preventing the module/driver from loading.

Uninstall whatever custom version you setup:
```
sudo nvidia-uninstall
```
And purge all nvidia drivers in dpkg too.
```
sudo aptitude purge $(dpkg -l | awk '$2~/nvidia/{print $2}')
```
If you are having to write this down to try the below instead may be easier to remember.
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```

And lastly, .old the xorg.conf file.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then reboot
```
sudo reboot
```
And X should load with default failsafe settings.
You'll probably need to install the detection packages for nvidia
```
sudo apt-get install nvidia-common
```
After that - go to the Hardware Drivers app (**System -> Administration -> Hardware Drivers**).
Then install/activate the NViDIA 185 drivers again.

Regards
Iain

---

### Post by dxtac1 on 2009-12-29
[FONT=Calibri][SIZE=3]All went well until here:[/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Calibri]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]It tells me:[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]No such file or directory[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]I reboot (it sent me back to dxtac@dxtac-homepc:~$ with no GUI)and typed:[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]sudo apt-get install nvidia-common[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]And it tells me:[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]NVIDIA common is already the newest version[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]0 upgraded 0 newly installed 0 to remove and 0 not upgraded[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]Back to:[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Calibri]dxtac@dxtac-homepc:~$[/FONT][/SIZE][/COLOR]

---

### Post by kingtiger01 on 2009-12-29
need to re-install youre Video-card drivers/recompile them. 

if using the ones from the repository(Apt), just use ```
sudo apt-get install --reinstall nvidia-glx-185
```

if you installed from the nvidia website, re-download them.

if you used this method, i suggest the new 195.30 beta.

x86(32bit)```
http://www.nvidia.com/object/linux_display_ia32_195.30.html
```

x64(64bit)```
http://www.nvidia.com/object/linux_display_amd64_195.30.html
```

then change to the directory and ```
sudo sh *.run
```

---

### Post by dxtac1 on 2009-12-29
When I enter code:
[http://www.nvidia.com/object/linux_display_ia32_195.30.html](http://www.nvidia.com/object/linux_display_ia32_195.30.html)
 
It tells me:
-bash: [http://www.nvidia.com/object/linux_display_ia32_195.30.html](http://www.nvidia.com/object/linux_display_ia32_195.30.html): no such file or directory
 
when I enter code:
sudo apt-get install --reinstall nvidia-glx-185
 
It tells me:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

---

### Post by ibuclaw on 2009-12-29
Woah - you are going at a million miles a second here - calm down. :)

Firstly - do as the dpkg command tells you.
```
sudo sudo dpkg --configure -a
```

Secondly - if it tells you that nvidia-common is already installed. Then you didn't remove nvidia properly.
Try running the first two I gave you again.

Regards
Iain

---

### Post by rnerwein on 2009-12-29
all that stuff makes me wonder - i'm runing ubuntu 9.10 64bit on an acer apire x3200 amd quad and this box is fullfilled with nvidia stuff. even whit a02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2) and 03:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1) . the graphic and any thing else runs perfect out of the box. and now look at the following lines and i think you understand why i'm wondering -->
lsmod ain't show me any nvidia stuff. even lspci tells me: Driver Status: nvidiafb is not active. 
i can find the nvidia driver - ./2.6.31-16-generic/kernel/drivers/video/nvidia/nvidiafb.ko :-??? 
be sure i don't want try to install the original nvidia driver !

---

