---
title: "How to set custom resolution for secondary monitor?"
date: 2010-04-30
forum: General Help
---

### Post by pom69wod on 2010-04-30
Hi guys I just switch from windows to use ubuntu 10.04. I am still learning how to set things in ubuntu. 
One of the problem is that I can't set my secondary (external) display to my favorite one. I have 22'' screen (max 1680x1050) but I love to set it to 1280x800.
I follow instruction from this website [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) and my display detail is like this

Screen 0: minimum 320 x 200, current 2464 x 900, maximum 8192 x 8192
VGA1 connected 1440x900+1024+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0 +
   1600x1200      60.0  
   1400x1050      60.0  
   1280x1024      75.0  
   1440x900       75.0     59.9* 
   1280x960       60.0  
   1360x765       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+96 (normal left inverted right x axis y axis) 246mm x 185mm
   1024x768       50.0 +   85.0*    75.0     70.1     60.0     40.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     60.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

I would like to set my VGA1 to 1280x800 so I use this command.

xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync

Somehow, I get the new mode in LVDS1 but not in  VGA1. How could I add this new mode in VGA1?

---

### Post by Gear.0 on 2010-05-27
I know it's been 3 weeks since you posted this, but maybe this bump will get more people to look at it because I am having a similar problem.

If you have found a solution could you please post it?

Although I am only using a single display, I want 1400x1050 on LVDS1 but when I add it it shows up in TV1, and I cannot select it.

---

### Post by ashnur on 2010-06-07
Up!

---

### Post by NTL2009 on 2010-06-12
I'm a noob, but it seems I was able to do this easily from the menu System / Preferences / Monitors. For me, it showed my external monitor connected to the laptop, and allowed me to select available resolutions from the drop down menu. Check "Show monitors in panel" for quick access.

I read somewhere else that these panel settings may over-ride the X / Config settings, but don't take my word for it.

---

### Post by mionescu on 2010-06-12
It depends on the video card you have. If it is an Intel card, you should be able to set up the resolution from "System->Preferences->Monitors". If you have Nvidia or ATI you need to use the Nvidia or Ati program to set up the resolution.

---

### Post by gharika on 2010-09-22
> **mionescu said:**
> It depends on the video card you have. If it is an Intel card, you should be able to set up the resolution from "System->Preferences->Monitors". If you have Nvidia or ATI you need to use the Nvidia or Ati program to set up the resolution.

Thanks mionescu, but where do we get these softwares from. I am trying to set a resolution of 1366x768 which is definitely non standard.

Helpppppph.

---

### Post by mionescu on 2010-09-22
You should be able to install them using the Ubuntu Software Center (or synaptic). For Nvidia, the program is called "nvidia-settings". For ATI (AMD) the name of the program is "fglrx-amdcccle". You should be able to find them in "System->Administration" after installation.

---

