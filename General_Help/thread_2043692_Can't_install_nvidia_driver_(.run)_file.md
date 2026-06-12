---
title: "Can't install nvidia driver (.run) file"
date: 2012-08-17
forum: General Help
---

### Post by Linuxpal on 2012-08-17
Hello! I'm new to ubuntu and i don't know what to do anymore. This is what I have done:

```
cd <path to folder where .run file is>
```All good path changed. Then: 

```
sudo sh filename.run
```Much stuff is happening in terminal "vertifying.................... and so on" before I'm left with the text:

> ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com").Help?

---

### Post by syndicate0017 on 2012-08-17
You can't run it logged in to the X server. Run it from recovery. Or I think you can press CTRL + alt + F1 to get to TTY and then 

```
 sudo stop lightdm 
```

Then running the .sh and after completing the installation

```
 sudo startx 
```

---

### Post by Scott Harrison on 2012-08-17
This is not the best way to install the nvidia display driver.

At a terminal, run the following:

```
sudo apt-get install nvidia-current
```

---

### Post by Ravi5kumar on 2012-08-17
Or install using 'Additional Drivers'.

---

### Post by Linuxpal on 2012-08-17
> **Scott Harrison said:**
> This is not the best way to install the nvidia display driver.

At a terminal, run the following:

```
sudo apt-get install nvidia-current
```

How will it know I exactly need the 64-bit GT 620M driver?

---

### Post by syndicate0017 on 2012-08-17
> **Linuxpal said:**
> How will it know I exactly need the 64-bit GT 620M driver?

nvidia-current (I believe) is the recommended driver that shows up when you search for proprietaries. I had issues with this though. I kept getting a sleeping monitor on boot so I had to install mine through the .run

The way he said *should* work though. I have no idea why it wouldn't for me.

---

### Post by Linuxpal on 2012-08-17
> **syndicate0017 said:**
> You can't run it logged in to the X server. Run it from recovery. Or I think you can press CTRL + alt + F1 to get to TTY and then 

```
 sudo stop lightdm 
```Then running the .sh and after completing the installation

```
 sudo startx 
```
I am able to get in to TTY, but my username and password (one of them) is wrong. I am using same username and password as I use to log onto Ubuntu normally, so I'm quite confused why I'm getting invalid pw/username here. Also, how do you quit TTY?

---

### Post by Codify on 2012-08-17
Does it give you any error message when you try your credentials? To get out you could try exit or sudo reboot.

---

### Post by Linuxpal on 2012-08-17
> **Codify said:**
> Does it give you any error message when you try your credentials? To get out you could try exit or sudo reboot.
My bad. It was case-sensitive ^^ Logged in now.

I've now installed Nvidia X Server Settins program using sudo apt-get install nvidia-current, but when I click the program I get this error message:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server

EDIT: Managed ron run this file + did a restart to restart x server. Then a window show on startup that it cannot detect my graphics card etc and ask me to run in low-graphic mode, or restore some default configurations -.- I moved from Windows to get FREEDOM, what is this xD? I feel locked in!

---

### Post by Linuxpal on 2012-08-17
Seems like I've f*ed up ubuntu now. I think I need to format and reinstall Ubuntu and just give a s* about the nvidia driver sadly. Now, everything laggs. When moving an internet-window around at desktop the movement is very laggy, also seems like theres extreme delay. If I move a window I get extreme delay. If i drag a window, and move mouse like crazy in 10 sec, movement will still be going on for seconds  even after i have dropped the window (delay). This didn't happen before all of this, and I doubt this is some compiz effect or whatever.

---

### Post by syndicate0017 on 2012-08-17
> **Linuxpal said:**
> Seems like I've f*ed up ubuntu now. I think I need to format and reinstall Ubuntu and just give a s* about the nvidia driver sadly. Now, everything laggs. When moving an internet-window around at desktop the movement is very laggy, also seems like theres extreme delay. If I move a window I get extreme delay. If i drag a window, and move mouse like crazy in 10 sec, movement will still be going on for seconds  even after i have dropped the window (delay). This didn't happen before all of this, and I doubt this is some compiz effect or whatever.

Sounds like you might have gotten stuck with vesa. If you can still access recovery, I'd recommend installing your .run file through there. I think you'll need to make your file system r/w (at least I did)

```
 mount -o remount,rw / 
```

Then install the driver. Once you reboot, you should be using the updated NVIDIA driver.

---

### Post by kedar5 on 2012-08-17
Its simple.

Stop the display manager service.

$ sudo service gdm stop

(whichever you are using)

or switch to tty1 (alt-ctrl-F1) and type

$ sudo ./NVIDIA-filename.run

---

### Post by efflandt on 2012-08-17
Your problem now my be that you have bits and pieces of different drivers.  It is best to use the Ubuntu packages which are coordinated with kernel and other updates.  If you install drivers with a script downloaded from nvidia, Ubuntu will be unaware of that and you may need to run that script again after any kernel updates.  With Ubuntu video driver packages you would not have to do that.

Not sure how to handle it if you have the new mixed Intel integrated graphics and nvidia, but if you just have nvidia, the nvidia drivers are typically already installed when you do a regular installation (you may have to use **nomodeset** boot parameter to boot the live/install CD or iso, but I did not need that once installed).

So if you do a fresh install, afterwards, see what **sudo lspci -v** shows for modules for your video device, and what version **dpkg-query -l nvidia*** shows for nvidia-current version.

If for some reason you need newer nvidia version than that, you can add the x-swat repository:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

Then use **Update Manger** to **Check** and install updates

---

### Post by Linuxpal on 2012-08-17
> **syndicate0017 said:**
> Sounds like you might have gotten stuck with vesa. If you can still access recovery, I'd recommend installing your .run file through there. I think you'll need to make your file system r/w (at least I did)

```
 mount -o remount,rw / 
```Then install the driver. Once you reboot, you should be using the updated NVIDIA driver.

I did this now, but I get the same thing at startup: a box saying "run in low graphics mode" etc. Thanks for all help so far.

> **efflandt said:**
> Your problem now my be that you have bits and pieces of different drivers.  It is best to use the Ubuntu packages which are coordinated with kernel and other updates.  If you install drivers with a script downloaded from nvidia, Ubuntu will be unaware of that and you may need to run that script again after any kernel updates.  With Ubuntu video driver packages you would not have to do that.

Not sure how to handle it if you have the new mixed Intel integrated graphics and nvidia, but if you just have nvidia, the nvidia drivers are typically already installed when you do a regular installation (you may have to use **nomodeset** boot parameter to boot the live/install CD or iso, but I did not need that once installed).

So if you do a fresh install, afterwards, see what **sudo lspci -v** shows for modules for your video device, and what version **dpkg-query -l nvidia*** shows for nvidia-current version.

If for some reason you need newer nvidia version than that, you can add the x-swat repository:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```Then use **Update Manger** to **Check** and install updates

I got the laptop Asus Zenbook UX32VD which do have  Intel 4000 graphics and Nvidia GT 620M Graphics all together as you mention. Do you think this may cause trouble?

---

