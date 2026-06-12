---
title: "A few questions."
date: 2009-12-01
forum: General Help
---

### Post by Ganjafreak on 2009-12-01
Okay guys, I have dual booted my computer with ubuntu 9.04 jaunty and kubuntu 9.10. Now see here is a few problems I've noticed.

First off all I had themes I'm going to try and switch over.

Another thing is I went to hardware drivers and there is no drivers on this system wtf???

I want my graphics card to work so I can make my screen resolution like 1600x1200 but yeah I'm on like 800x600 and it's to big for me I like to have a really big window so I can run multiple things at once.

And I want to add a panel at the top and put stuff on but these panels are hard to work I added a panel and tried to put stuff on there but it don't show like I see no icons on it you would think if you click "add to panel" it would show the icon.

But yeah I'm about to google for amw toolbar manager, Cause I got's to have my toolbar for both system's

Is wine also avalible for kubuntu??

I heard that both of these operating system's are very similar except for the Desktop Enviroments that one uses Gnome*(Ubuntu) and that Kubuntu is KDE.

---

### Post by Ganjafreak on 2009-12-01
K, I have installed my graphics card nvidia the one that was suggested and when I restarted I have major damn problems there is colors pink purple blue etc flashing like there is a system error like it's all blinking right now and stuff does anyone know what this is../??

I think my thing my be corrupted it's like it is **** is crashed and it's all blinking help anybody

---

### Post by jbrown96 on 2009-12-02
Kubuntu is the exact same as Ubuntu underneath, so all the same programs are available, including wine. 

To add a panel, right click on the desktop and add a panel. There should be a small icon in one of the corners (mine was in the top left). Right click on it and choose panel settings. Then, drag the arrow (looks like |<--) to the right to expand it. You can click the screen edge and drag it to another side, and add icon by adding widgets. 


To fix your graphics problem:
When you boot, you should get a Grub listing of available kernels. If not, then hold shift or escape when the computer first boots. Choose the second entry, which should be a recovery version of the kernel with the largest version number. Once that boots, then choose "root shell" and run the following ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``````
nano /etc/X11/xorg.conf
``` This will open a text editor. You need to find a section like this > Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
 You need to  change "nvidia" to "vesa" be sure to keep the quotes and spacing. Save, exit, and ```
reboot
``` This should get you back to low graphics mode. Try to enable the driver again. It would also be helpful to know the driver version and your graphics card. You can get your graphics card info from ```
lspci | grep VGA
```

---

### Post by Ganjafreak on 2009-12-02
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
ganjafreak@ganjafreak-desktop:~$

---

### Post by jbrown96 on 2009-12-02
Boot into recovery mode as mentioned in my last post, then do the following. 

1) install some build tools ```
sudo apt-get install build-essential
```
2) download the driver ```
wget http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run
```
3) install the driver ```
sudo sh ./NVID
``` then press tab to auto-complete the filename. 

If it fails to build the kernel module, then you need to install the kernel headers manually.


1) find your kernel version ```
uname -r
```
2) install the kernel headers for your kernel ```
sudo apt-get install linux-headers-
``` press tab twice to get a list of available packages. install the generic one that matches your version.

Then re-run #3.

when finished
```
sudo reboot
```

---

### Post by Ganjafreak on 2009-12-02
Alright, well I reinstalled the OS.

Hopefully I will run the update manager and the hardware drivers will *poof* magically work. What I don't get is other's have installed the exact same version with the exact same computer I'm sure of and I bet they didn't have this problem..


I thought I had a corrupt disc. I was about to send it back and have them send me another xD.

---

### Post by Ganjafreak on 2009-12-02
Now, See I had this problem last night. I clicked "Hardware Drivers" and let it load. Then it said no prority drivers are avalible on this computer. I think I have to restart but yeah. I don't get it I have drivers on my pc. Why does OS system's these days have to be so complicated. I wish we would of just got stuck with windows NT and 2k for the rest of our lifes. Hell now days 2k runs faster and responds faster than new os's does. xD

---

### Post by SuperSonic4 on 2009-12-02
> **Ganjafreak said:**
> Now, See I had this problem last night. I clicked "Hardware Drivers" and let it load. Then it said no prority drivers are avalible on this computer. I think I have to restart but yeah. I don't get it I have drivers on my pc. Why does OS system's these days have to be so complicated. I wish we would of just got stuck with windows NT and 2k for the rest of our lifes. Hell now days 2k runs faster and responds faster than new os's does. xD

Of course it does. An OS designed for computers with less than 100mb of RAM and a CPU measured in MHz will run faster...

I'd follow the manual install instructions, I installed nvidia with no problem

---

### Post by Ganjafreak on 2009-12-02
I've done the manual installation, I just put in the disk and click "Next" read and follow the directions. That is how I install.

---

