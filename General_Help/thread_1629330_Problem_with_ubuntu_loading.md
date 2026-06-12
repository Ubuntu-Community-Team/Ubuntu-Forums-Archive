---
title: "Problem with ubuntu loading"
date: 2010-11-23
forum: General Help
---

### Post by slinzex on 2010-11-23
When I start my laptop: Dell Vostro 1720, it starts loading grub, I select Ubuntu, and after that, appears one image of ubuntu logo 
and few points, like loading... 
I show it :
[IMG]http://t2.gstatic.com/images?q=tbn:ms--dDX1-97rkM:http://www.mylinuxblog.info/wp-content/uploads/2010/06/install1.png&t=1[/IMG]
Since I updated to ubuntu 10.04, I had this problem

1- How to change it ?

I tried a lot of things while googling... but didn't solve it yet.

2- When I install StartupManager, it appears only with two options: Startup Options and Advanced. And there I can't change the ubuntu loading image. 
If we check google images, we can see more than this... I suppose this is caused by ubuntu startupManager download link....

3-I tried copy by different ways the splash.png. With gnome-conf, setting the key in apps...splash.png. Didn't work. Also I tried 
to replace "/usr/share/images/xsplash/bg_2560x1600.jpg" to another pic I have, but no result.

---

### Post by Rubi1200 on 2010-11-24
Hi and welcome to the forums :)

We need some more information please:

1. how did you install Ubuntu; to the drive or via Wubi?

2. what other operating systems do you have installed?

3. what graphics card do you have?

Thanks.

---

### Post by nl4m on 2010-11-24
Try to boot into single user mode, and type in as root:
```
startx
```If that does not work I can help you find the error by going through the verbose mode. If it's the logo I can disable it for you.

---

### Post by slinzex on 2010-11-24
1. how did you install Ubuntu; to the drive or via Wubi?
I installed Ubuntu with live CD, that was ubuntu9... old version. Then I updated
2. what other operating systems do you have installed?
Also I have w7. But in my opinion it don't depend of that....
3. what graphics card do you have?
[GeForce 9600M GS]

---

### Post by slinzex on 2010-11-24
> **nl4m said:**
> Try to boot into single user mode, and type in as root:
```
startx
```If that does not work I can help you find the error by going through the verbose mode. If it's the logo I can disable it for you.

Why I need to do that? 
Actually I can boot. That not is my problem. The problem is only the splash screen. Not the login splash screen, but the boot .

---

### Post by slinzex on 2010-11-24
plz help

---

### Post by Quackers on 2010-11-24
Can you explain a little more please?
Is your problem just with the screen you pictured? What is the problem with it?

---

### Post by Quackers on 2010-11-24
Do you mean the screen resolution? The writing is too big?

---

### Post by garvinrick4 on 2010-11-24
Go to Synaptic package manager and type in plymouth
select which plymouth themes you want to install and install them: Then run this below:
                   ```
sudo update-alternatives --config default.plymouth   
```Now pick your choice by # and run
                    ```
sudo update-initramfs -u 
```Now you have new Ubuntu plymouth theme installed

---

### Post by slinzex on 2010-11-24
> **garvinrick4 said:**
> Go to Synaptic package manager and type in plymouth
select which plymouth themes you want to install and install them: Then run this below:
                   ```
sudo update-alternatives --config default.plymouth   
```Now pick your choice by # and run
                    ```
sudo update-initramfs -u 
```Now you have new Ubuntu plymouth theme installed


Before I see your answer, I did that but on other way. I installed with apt-get the plymouth GUI. Then I've chosen one of them, and activated plymouth. Then I restarted and just after grub, I can only see the blinking "_" and 6sec after ubuntu desktop. No more. So now, I arrived to the point where I have no image on boot.
But I want to install one.

---

### Post by garvinrick4 on 2010-11-24
#Go to Synaptic Package Manager and type in plymouth in upper right hand corner box.
#There are 5 or 6 different Themes, install theme.
#Now run code and choose which one you want.

---

### Post by faal on 2010-11-27
I have the same problem. I only see the blinking cursor, no logo at all.

Tried to:

1. Reinstall plymouth
2. Reinstall plymouth-theme-ubuntu-logo
3. Tried a different theme (plymouth-theme-ubuntustudio)

Everytime running 

sudo update-alternatives --config default.plymouth

and 

sudo update-initramfs -u

in-between.

Nothing has worked so far. Any ideas?

Running on a fresh install of Ubuntu 10.10 with an ATI mobility card using fglrx.

[   15.658022] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.823820] [fglrx] Maximum main memory to use for locked dma buffers: 5773 MBytes.
[   15.824195] [fglrx]   vendor: 1002 device: 68c0 count: 1
[   15.824921] [fglrx] ioport: bar 4, base 0x2000, size: 0x100
[   15.825944] [fglrx] Kernel PAT support is enabled
[   15.825963] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   19.628682] [fglrx] ATIF platform detected with notification ID: 0x81
[   19.871312] fglrx_pci 0000:02:00.0: irq 56 for MSI/MSI-X
[   19.872057] [fglrx] Firegl kernel thread PID: 1497
[   19.872326] [fglrx] IRQ 56 Enabled
[   20.137233] [fglrx] Gart USWC size:1280 M.
[   20.137236] [fglrx] Gart cacheable size:508 M.
[   20.137239] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   20.137241] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[   20.137243] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000

---

### Post by faal on 2010-11-27
I was able to mostly solve the problem using startup-manager, except for the fact that it won't go higher than 1280X1024 16bit. 

More annoying though is that on my external monitor the scaling is wrong, leaving a large black edge around the loading screen. Anyone know how to scale up the loading screen on an external monitor?

---

### Post by garvinrick4 on 2010-11-30
rick@rick-laptop:~$ sudo update-alternatives --config default.plymouth
[sudo] password for rick: 
There are 2 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       auto mode
* 1            /lib/plymouth/themes/solar/solar.plymouth               10        manual mode
  2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       manual mode

Press enter to keep the current choice
[*], or type selection number: 
#Notice I have 2 themes installed. I choose one then update with code I gave and new
one is inplace
#There are about 5 or 6 different themes you can install I use solar in this install see the * means that
is one installed now.

---

### Post by slinzex on 2011-01-06
But garvinrick4, this is for grub boot logo, picture...
I have that working, with plymouth.

The problem I still having is the logo/picture while ubuntu is loading. How to set that? Because at this moment, se sequence is:
1-Dell boot screen
2-Grub choose lin/win  (with my picture on background)
3- "_" for 10seconds
4-I can see my desktop. 

Between 3-4 I can only see black screen and "_" blinking. Nothing else until gnome desktop is appeared.

---

### Post by slinzex on 2011-01-11
nobody can help me or nobody reads this post?

---

### Post by Lykopis on 2011-01-13
If I understand you correctly you don't have a boot splash screen. 
This is what I did to get Plymouth working again.
1: Open synaptic package manger.
2: click the status button at the lower left.
3: select installed from the list above it.
4: type grub in the search box
5: right click and select "reinstall" for all installed grub packages.
6: you should get a dialogue box some time during the process, select the vendors settings from the pull-down menu & complete the install.
7: now type plymouth in the search box.
 8: right click and select "reinstall" for all installed plymouth packages.
Let the reinstall complete and apply it's changes.
Reboot a couple of times to see if the settings took. 
(don't freak out on the first reboot it can look really bad)

---

### Post by matt_symes on 2011-01-13
Misread Post

---

