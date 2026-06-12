---
title: "Nvidia Screen resolution 640x480"
date: 2009-09-20
forum: General Help
---

### Post by steffenklug on 2009-09-20
Hi, 
Here is the problem.
I boot up and I get the 640x480 resolution.
It was working displaying at 1024x768 at one point, but no more
-
I have the latest Ubuntu 9.04 version with all updates installed.
-
I checked several web sites, but can not find a true hit
most recommendations do not work for me (like Ctrl Alt +..)
-
The system is a dual boot with Windows and the Graphics card works fine there, so I do not think it is hardware
- 
Display shows:
A red box "Unknown"
The available Resolution is 640x480 and 320x240
"Detect Monitors" does not do anything
-
xorg.conf 
shows:
  "Device"
       Identifier "Configured Video Device"
EndSection
Monitor
  Identifier "Configured Monitor"
Screen
Identifier "Default Screen"
-
In hardware drives I see 
"NVIDIA accelerated graphics drive (version 96) recommended

I activated it and deactivated it without a difference
-
I need some guidance
Thank you
Steffen

---

### Post by NoaHall on 2009-09-20
gksudo nvidia-settings 

From the terminal.

---

### Post by ibuclaw on 2009-09-20
And you rebooted your workstation after you installed the NViDIA Hardware Drivers?

---

### Post by steffenklug on 2009-09-20
I did not get that far.

I did:
And again, move the installer to the /usr/src folder and make a link to the file.
Code:

sudo install NVIDIA-Linux-190.32.pkg.run /usr/src
sudo ln -fs /usr/src/NVIDIA-Linux-190.32.pkg.run /usr/src/nvidia-driver

and nothing really happened, (I moved to the usr/src folder-no difference)
at the moment I am waiting after I did the 

sudo /etc/init.d/gdm stop

It has been there for 6 minutes
I have a black screen 
* Stopping firewall
                     * reloading system log daemon

--
I will power off now

---

### Post by steffenklug on 2009-09-20
Well - Thank you
I guess I did not power off
I have a resolution of 1280x1024 now
when I go to display it still states unknown
-
no driver in NVidia anymore
--
Well that works for me
Thanks and good day

---

### Post by steffenklug on 2009-09-20
To finalize
I used link
[http://ubuntuforums.org/showthread.php?t=1125400&highlight=screen+resolution+640](http://ubuntuforums.org/showthread.php?t=1125400&highlight=screen+resolution+640)

for help

---

### Post by ibuclaw on 2009-09-20
> **steffenklug said:**
> To finalize
I used link
[http://ubuntuforums.org/showthread.php?t=1125400&highlight=screen+resolution+640](http://ubuntuforums.org/showthread.php?t=1125400&highlight=screen+resolution+640)

for help

Thanks, glad the guide helped you.

---

