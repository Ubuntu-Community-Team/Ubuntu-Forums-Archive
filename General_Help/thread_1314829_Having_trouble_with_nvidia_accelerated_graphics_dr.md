---
title: "Having trouble with nvidia accelerated graphics drivers"
date: 2009-11-04
forum: General Help
---

### Post by aviedw on 2009-11-04
I looked up my graphics card on the nivida website and this is the driver that it prompted me to download 

NVIDIA-Linux-x86-190.42-pkg1.run

I downloaded it and installed it by pressing ctrl alt and f1 and logged in. Then i went ahead and put in

sudo killall gdm and then i did

sh NVIDIA-Linux-x86-190.42-pkg1.run i went through the install process but it told me that there was another driver that i had used in the past that i was going to uninstall. It also prompted me that it was having troubling uninstalling the driver and updating some kind of file. 

So when i restarted the computer the graphics was worse than before. So i went ahead and download Envy. This got my graphics working on a very basic level but i cant even run screen savers let alone games. When i slide windows it leaves an imprint almost as if its still in the place where i last dragged it from. 

I am hoping that there is a solution to this problem. And i think it might start with me uninstalling all the nivide drivers. The ones from Envy and the accelerated drivers that i download from Nvidia. One of my problems with that though is that i dont know how to uninstall accelerated nvidia drivers. If anybody can help me with this problem please feel free to leave your advice. Thanks in advance

---

### Post by mechro on 2009-11-04
Before you installed these drivers did you check what Ubuntu was recommending? When you first install Ubuntu it usually offers restricted drivers if available.

Check **System > Admin... > Hardware Drivers**

---

### Post by wojox on 2009-11-04
[HowTo: NViDIA 185.18 Drivers in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1125400")

Follow along with these instructions. Except you'll be using NVIDIA-Linux-x86-190.42-pkg1.run

---

### Post by aviedw on 2009-11-09
I did just that i download the newest drivers and installed them. 
Truthfully i dont think they work for my graphics card because the performance is terrible. Im working with these drivers right now 185.18.36 , When i download envy its the drivers that was suggested so i tried that and now the computer works a lot better but i dont think i have full 3d support or open GL support, some of the more graphics rendering screen-savers still dont work correctly or it looks like its stuttering or it just shuts down. 

The last time my computer work correctly was when i had Ubuntu 8.10 and i had installed the 180.22 nvidia graphics drivers. I was able to use the the desktop advancements. Now would hate to have to downgrade to get better performance.

---

### Post by aviedw on 2009-11-13
Hey, i had another questions that was related to my orginial questions so i decided to just post in the same thread. 

Check this out 


aviedw@aviedw-desktop:~$ dpkg -l | grep nvidiaii  

nvidia-173-
modaliases                      173.14.20-0ubuntu5                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-185-kernel-source                   185.18.36-0ubuntu9                         NVIDIA binary kernel module source
ii  nvidia-185-libvdpau                        185.18.36-0ubuntu9                         Video Decode and Presentation API for Unix
ii  nvidia-185-modaliases                      185.18.36-0ubuntu9                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                       96.43.13-0ubuntu6                          Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                              0.2.15.1                                   Find obsolete NVIDIA drivers
rc  nvidia-glx-173                             173.14.20-0ubuntu5                         NVIDIA binary Xorg driver
ii  nvidia-glx-185                             185.18.36-0ubuntu9                         NVIDIA binary Xorg driver
rc  nvidia-glx-71                              71.86.08-0ubuntu1                          NVIDIA binary Xorg driver
ii  nvidia-settings                            180.25-0ubuntu1                            Tool of configuring the NVIDIA graphics drive

i currently have the 185 driver installed, but what i was wondering is if i had all of these on my system could this possible be the reason why my computer is acting up. Any advice is truly welcome. Thanks

---

