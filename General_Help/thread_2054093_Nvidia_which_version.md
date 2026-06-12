---
title: "Nvidia which version?"
date: 2012-09-06
forum: General Help
---

### Post by Timeless on 2012-09-06
Hi, I am using synaptic to clean up my comp, In the installed tab, I see lots of different versions of nvidia; 173, 95, 185 which looks like some kinda transitional package for 195. Nvidia current is 195.36.24, my question is if 195 is my current version, can I get rid of the other/older versions?

Thnxs

---

### Post by aPaonessa on 2012-09-06
I believe so. Worst case is your driver is removed and you install it again via tty.

---

### Post by bogan on 2012-09-07
Hi!, **Timeless**,

Edit: This first bit is wrong; I just rebooted to my 10.04 installation and you are quite right, the later versions of nvidia-current do not show in 10.04 Synaptic. I am using 295.59 Downloaded from nvidia.com, and it does not show up.

[COLOR=DarkOrange]Are you sure that Synaptic shows nvidia "195", It should be 295.40 & 295.49 nvidia-current.

Version '195.36.24' dates back to April 2010 and , AFAIK, would not work with 12.04 kernals: 173 is only needed for legacy cards, such as nForce & pre 5xxx series.[/COLOR] [COLOR=DarkOrange]

What version of Ubuntu are you using? Still 10.04 ??[/COLOR] 
Edit: Ignore the yellow bit!

What is important is the Synaptic entries that have a Green tag against them, those are actually installed, the others are just listed as available.

To find out what you are using run [ & Post if you need more info]: ```
lspci -nnk | grep -iA3 vga
cat /sys/module/nvidia/version # only works for nvidia.com drivers
sudo apt-cache policy nvidia-current
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan.**

---

### Post by Timeless on 2012-09-07
Tks, for the help, yes, its 195, I have not updated the drivers in 2 years. I'm still using 10.04 Lucid, not ready to upgrade, yet. I'm going to check, but I think they are all green, that was the reason for my question, I did not think they could all be installed at once, but they are all green. So which ones can I remove? see attachment. 

tks, to both of your for the help, I'll try the terminal and see which version I have.

---

### Post by bogan on 2012-09-07
Hi!, **Timeless**,

Edit: Second thought: Is your set-up fully updated? @uname -ar will show the current installed version. Mine is:> Linux alan-desktop 2.6.32-42-generic #96-Ubuntu SMP Wed Aug 15 18:57:09 UTC 2012 i686 GNU/Linux

Was the screenshot of Synaptic taken with it set in the bottom-left as 'Status'?

As in 10.04, I am not using 'nvidia-current' or 'Jockey', even the 'nvidia-common' is not shown as installed, certainly not that long list of nvidia drivers. 

I am no expert in this but in general, AFAIK, multiple drivers for the same video card produce conflicts, and it is good practice to remove, or at least deactivate, the existing installed driver, before installing or activating another.

Using nvidia's own installer automatically does that.

It is of interest what is shown in Additional Hardware/Drivers  as available, installed or activated, but I cannot find it in 10.04.

Woah, Found it!! System>Administration>Hardware Drivers; but it only shows: "No proprietary drivers are in use in this system." as I am not using nvidia-current installed with Jockey. It may or may not list them in yours.

Looking forward to hearing which drivers are actually being used.

Chao!, **bogan**.

---

### Post by Epodx64 on 2012-09-07
I'd highly recommend adding the x-swat/x-updates PPA and grabbing the 304 driver when I had a Geforce 6150se 173-295 didn't work what so ever.

---

### Post by haresear on 2012-09-07
> **Timeless said:**
> Hi, I am using synaptic to clean up my comp, In the installed tab, I see lots of different versions of nvidia; 173, 95, 185 which looks like some kinda transitional package for 195. Nvidia current is 195.36.24, my question is if 195 is my current version, can I get rid of the other/older versions?

Thnxs

Just to clarify for other readers who may happen across this thread, drivers 173 and 96 are not transitional, but rather legacy drivers for older nVidia cards. For example 5000 series cards need to use the 173 drivers, because newer driver versions don't support those cards. The nVidia website describes the cards supported by the legacy drivers.

---

