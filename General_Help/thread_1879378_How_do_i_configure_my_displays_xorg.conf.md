---
title: "How do i configure my displays xorg.conf"
date: 2011-11-11
forum: General Help
---

### Post by Neill_R on 2011-11-11
[FONT=-moz-fixed]hello 

Could/Would you please show me a xorg.conf file that I could use as a  starting template for my system. 

Computer PACKARD BELL I MEDIA 1328/1 
OS UBUNTU 10.04 and Windows XP PRO SP3 (where it works in extended desk  top) 
Monitors 
                 DELL 17 (on S3)                              (active  screen 0) 
                 HP S2231a on (SIS motherboard)   ( inactive ) 

$ lspci | grep VGA 

00:09.0 VGA compatible controller:S3 Inc. 86c968 [Vision 968 VRAM] rev 0 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS]  661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter 
$ lspci -s 00:09.0 -n 
00:09.0 0300: 5333:88f0 
$ lspci -s 01:00.0 -n 
01:00.0 0300: 1039:6330 
$ 


in default case where there is no xorg.conf file I get 

(--) s3(0): Cannot determine IBM RAMDAC type, aborting 
(EE) s3(0): Ramdac probe failed 

... 

(EE) Screen(s) found, but none have a usable configuration. 

defaults to low resolution  mode only  800x600 

I used the GPARTED Live CD to get the screen into higher resolution mode  and have tried to edit the file but I am unsure of what I am doing hence  the need for a template. and I would like to see the other screen turned  on.  


Many thanks 







[/FONT]

---

### Post by Neill_R on 2011-11-13
The problem has now moved on.
I can get two screens if i use the vesa driver instead of the S3 driver but the display  is some what corrupt  and mouse and keyboard 


How does one get this to work and what is it supposed to do?

sudo dpkg-reconfigure xserver-xorg

I have an job to get done please bid if you are an expert in this

[http://www.peopleperhour.com/freelance_jobs_work_projects/ubuntu-configuration-dual-screens/102465](http://www.peopleperhour.com/freelance_jobs_work_projects/ubuntu-configuration-dual-screens/102465)

---

### Post by Neill_R on 2011-11-13
[B]The problem was partially solved it has moved on to where I have two screens but the system freeze refer to this thread

[http://ubuntuforums.org/showthread.php?t=1881197 ]("http://ubuntuforums.org/showthread.php?t=1881197")

this is closed


sudo dpkg-reconfigure xserver-xorg?????[/B]             
                                                                How does one get this to work and what is it supposed to do?

sudo dpkg-reconfigure xserver-xorg

I have an job to get done please bid if you are an expert in this

[http://www.peopleperhour.com/freelan...screens/102465]("http://www.peopleperhour.com/freelance_jobs_work_projects/ubuntu-configuration-dual-screens/102465")

---

### Post by raja.genupula on 2011-11-13
i hope these things can help you

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

[http://www.youtube.com/watch?v=2QsP8GDTpno](http://www.youtube.com/watch?v=2QsP8GDTpno)

[http://www.mepis.org/docs/en/index.php?title=Dpkg-reconfigure_xserver-xorg](http://www.mepis.org/docs/en/index.php?title=Dpkg-reconfigure_xserver-xorg)

---

### Post by dino99 on 2011-11-13
maybe: man dpkg

---

### Post by jocko on 2011-11-13
It does nothing of importance anymore. It used to run a set of scripts to detect and configure your graphics card, keyboard, mouse, etc. and set up an /etc/X11/xorg.conf file that stored all the relevant settings for those devices.
Since a few years back xorg.conf is not needed anymore by any of the open source graphics drivers and everything is detected and configured automatically when x.org starts, so dpkg-reconfigure doesn't do any of those things anymore (but if you make a xorg.conf file, the settings in it will be used).
If you still by some reason need a xorg.conf you have to set it up some other way.

One way to make a xorg.conf:
1. Switch to a virtual terminal: Press Ctrl+Alt+F1 (or F2-F6).
2. Stop Xorg by stopping lightdm (or gdm if you use an older Ubuntu version than 10.10):
```
sudo service lightdm stop
```Or:
```
sudo service gdm stop
```3. Let Xorg detect everything and set up a Xorg.conf for you:
```
sudo Xorg -configure
```4. The new Xorg.conf file will be saved in your home directory as "xorg.conf.new", so you'll need to copy it to /etc/X11:
```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
```5. Keep your fingers crossed and hope it was set up correctly:
```
sudo service lightdm start
```Or:
```
sudo service gdm start
```If you need to go back to the way it was before this, just delete the Xorg.conf file:
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by MoreOrLess on 2011-11-13
No xorg.conf is going to fix this issue:
```
(--) s3(0): Cannot determine IBM RAMDAC type, aborting
(EE) s3(0): Ramdac probe failed
```
Your best bet for the Diamond card is the vesa driver, but I don't know if it does multi-monitor.

---

### Post by Neill_R on 2011-11-13
Jocko  

Although I have 11.04 system as it was most likely upgrades from 10.04 I had to use gdm  it complained that there was no lightdm service. F OR I  (other readers)

On my dual screen system now I have the resultant xorg.conf in place.  But as Moreorless says it does not and can not fix the 

(--) s3(0): Cannot determine IBM RAMDAC type, aborting
(EE) s3(0): Ramdac probe failed
But I do have the SIS graphics working and in 1024 x 768 mode. I also have the S3 card showing the startup UBUNTU screen on the DELL monitor 

I tried changing the S3 driver to vesa . A two screen display ensues but the mouse and keyboard freeze (even alt ctrl f1) and the display on both monitor has corruption. if i can figure out hoe to attach the xorg.conf file I will

---

### Post by Neill_R on 2011-11-13
I have attached the xorg.conf file created. I will also attact the Xorg.log file 3 parts 

sumary s3      --- EE  a single screen on SIS HP S2231a
             vesa  --- two screens but freezes keyboard and mouse and is partially corrupt

Anyone got any idea what I can do

---

### Post by Neill_R on 2011-11-14
Monday  14

Hello

In Windows XP I can run dual screen 1024x768 16 medium colour. Here with the vesa and not the s3 driver then the screen is corrupt I think I need Modeline line adding to xorg.conf I hope that once the screen resolution is sorted out the mouse and keyboard will stop freezing.

Am I right? what can you suggest

refer to the xorg.conf file attached card0-monitor0 is a DELL E171FPb card1-monitor1 is a HP S2231a

Thank you for any assistance you can provide to me.

Neill

---

### Post by lisati on 2011-11-18
Threads merged. Creating multiple threads for the same issue can dilute the comminuty's efforts. Please remember that we're all volunteers here with a wide range of hardware and experience.

---

