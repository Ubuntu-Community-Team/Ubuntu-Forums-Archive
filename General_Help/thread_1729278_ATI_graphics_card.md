---
title: "ATI graphics card"
date: 2011-04-14
forum: General Help
---

### Post by Julian Luna on 2011-04-14
Well lately i've been doing some updates and finally this game that comes with Ubuntu "Quadrapassel" displays fine with the desktop effects at the maximum but still a bit too laggy (Graphically)... I mean, is it normal that when I open the "Additional Drivers" Only one option is available and it's about graphic card? Anyways I wish you can help me to run awesomely 4D mmo's with my desktop effects at max

Also, how to know how much megabytes does my graphic card has? I might be not using the proper graphic card's driver maybe

---

### Post by Mark Phelps on 2011-04-14
Telling us it's ATI is not telling us much.

Open a terminal and enter "lspci" and look for the line with VGA in it.  That will give you information about your card.

And yes, you are generally offered only one choice of restricted video drivers.

---

### Post by Julian Luna on 2011-04-14
Hello! It is ATI Technologies Inc Radeon HD 3200 Graphics ^^

---

### Post by Mark Phelps on 2011-04-15
OK, then you should use the Additional Drivers option to install those drivers.

If you want the latest version, the process is more complicated because you will have to:
1) remove the current ATI drivers and replace them with the open-source drivers
2) Download the latest AMD drivers for your card
3) Install the latest AMD drivers

---

### Post by cottfcfan on 2011-04-15
A good guide to installing ATI Drivers is found here:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

### Post by Julian Luna on 2011-04-16
Okey I'm trying to follow it but I'm stuck on the following step: 

***Generate a new /etc/X11/xorg.conf file***

 *Unfortunately, there is no sure way to generate the ATI version of  the Xorg.conf file.  It is entirely dependent on your configuration.   The following subsections will attempt to address possible (and tested)  variations for their respective configurations. *
 ***[[edit]("http://wiki.cchtml.com/index.php?title=Ubuntu_Maverick_Installation_Guide&action=edit&section=11")]  Generic Config ***

 *This will work for most people: *
 *$ sudo aticonfig --initial -f*

[FONT=Verdana]Because whenever I tipe the last command there's an error that says "aticonfig" is not a valid parameter, or... you know..

Also the specifications of my graphic card (Which is not dedicated), are right here
[http://www.notebookcheck.net/ATI-Radeon-HD-3200.9591.0.html](http://www.notebookcheck.net/ATI-Radeon-HD-3200.9591.0.html)

Are 512 MB something good in order to run properly the gnome's desktop max effects and also this 4D games kind of WoW?
[/FONT]

---

### Post by K_45 on 2011-04-16
I'd just use the built in drivers in Additional Drivers. That GPU should run WoW on Medium/Low, and Gnome shouldn't be a problem. The problem for games is that it has no dedicated memory, only shared, and only 4 texture unites and 4 ROP's, and generally low specs all around. A dedicated card, such as the 6870 for example, has 56 texture units and 32 ROP's.  For desktop work, no problem, for games, lower specs like WoW will run on reduced quality settings.

---

### Post by Julian Luna on 2011-04-17
Ok thanks, what's a ROP?

---

### Post by K_45 on 2011-04-17
ROP's are raster pipelines that for processing part of the stuff you see onscreen. The more the better.

---

### Post by Julian Luna on 2011-04-17
Oh thanks, well, can anybody suggest me which libs to download if I already installed the generic driver at "Additional Drivers" and Quadrapassel still looks bad, blinky (Having in mind I don't even have compiz installed)? I'm on ubuntu 10.10 x64 bits

---

### Post by Julian Luna on 2011-04-18
bump

---

### Post by cottfcfan on 2011-04-19
Ok. these are the steps i followed:
But before you start you may have partially installed fglrx, so run the following:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
Then:

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
```
Only use the next one if your using 64bit!!
```
sudo apt-get install ia32-libs
```
```
cd ~/; mkdir catalyst11.3; cd catalyst11.3/
```
```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run
```
```
chmod +x ati-driver-installer-11-3-x86.x86_64.run
```
```
sudo apt-get remove --purge xserver-xorg-video-radeon
```
```
sh ati-driver-installer-11-3-x86.x86_64.run --buildpkg Ubuntu/maverick
```
```
sudo dpkg -i fglrx*.deb
```
```
sudo aticonfig --initial -f
```
Then reboot, you may have to reboot twice.
That should sort it.

---

### Post by Julian Luna on 2011-04-19
Ok! Im gonna try em out ^^

Ok! Tried it but it looks glitchy, actually it works better since quadrapassel was not showing at all (Blinking all the time) Well Quadrapassel is a good option to start cause it does require basic graphics... what is happening is that it only blinks when a new piece is appearing or a line is completed... it's better! Thanks a lot! But it requires something else.. I don't know what

---

### Post by Julian Luna on 2011-04-20
cottfcfan D:

---

### Post by cottfcfan on 2011-04-21
Hi Julian,
Tried Quadrapassel, and works fine for me.
I'm using the radeon HD2400 card which in theory is not as good as yours.
Make sure your drivers are installed correctly. Type "fglrxinfo" in a terminal, and make sure it looks something like this:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 3.3.10600 Compatibility Profile Context

```
Ive also atached my xorg.conf which may help.
If you change anything run:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```
afterwards and reboot.
Other than that I can't really help, ATI & Linux never have worked that well together, just waiting for the OSS Drivers to come up to speed.

---

### Post by mastablasta on 2011-04-21
> **Julian Luna said:**
> [FONT=Verdana]Are 512 MB something good in order to run properly the gnome's desktop max effects and also this 4D games kind of WoW?[/FONT]

 
just so you know - running desktop effects and virtualizing "graphic intensive" games can make a lag even with better dedicated card and drivers. Compiz (the thing that makes the effects) has a tendency to act out even with a dedicated card. So it's best to turn it off (turn off desktop effects) when running games especially if you run them via WINE which in itself can eat up memory as well as CPU.

---

### Post by Julian Luna on 2011-04-21
Hello friend! I have good news!
It might not be the graphic card cause... the first fact I might mention is: I opened right now Quadrapassel (Which is the ridiculous example we're managing). And it's actually running worst! But there's a new factor that has changed... I'm running atm a VirtualBox to which I assigned around _128mb_ of my 512mb of graphic memory (The max I could)... it might be probably issue of the Ram memory that I have (Just 2 gigas) Or issue of the graphic memory that I splitted. Because here's what the fglrxinfo showed me:
(If you can tell me how to make textboxes it'd be fine cause I can't figure it out on the toolbox)

[I]julian@julian-A780GM-A:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 1.4 (3.3.10600 Compatibility Profile Context)[/I]

So if we check it's not really far from what yours is... there's nothing that looks differently wierd

I don't exactly remember in which folder to find my xorg.xonf files... ohwait it was on the page you gave me, here it is I found it... (Processing) Ok there are many different issues between your file and mine... the first thing I might ask, of a bunch of facts that I might mention is:

**1.-** Did you rename your [xorg.conf] file to [xorg.conf.odt] yourself in order to be able to upload it? Or it was as .odt suffix by itself? Because on my folder [etc/X11] there's just a [xorg.conf] file which it isn't as [.odt], and I can open on text editor.

**2.-** Your file is clearly opened by OpenOffice Word Processor, so I tried the first syncronization in order to  be able to open your file on Text Editor, hence I removed the [.odt] suffix and tried to open it on Text Editor but there's a message I got:

[I]Could not open the file /home/julian/Downloads/xorg.conf.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again[/I]

Which is an issue that I don't get when I open my [xorg.conf] file. But in fact; if I open your [xorg.conf.odt] file on Word Processor (Since I can't manage to open it on Text Editor) and also open my [xorg.conf] file on Text Editor, they display almost the same thing, I will not copy what yours dislplay cause you already know and I won't copy what's on mine in order not to spam you... but I found some differences (Will mark em on red)

   **A) Yours:**
Section "Module"
EndSection

   **B) Mine:**
Section "Module"
[COLOR=Red]    Load  "glx"[/COLOR]
EndSection

  ** C) Yours:**
Section "Device"  
     Identifier  "aticonfig-Device[0]-0" 
     Driver      "fglrx"  
     [COLOR=Red]Option        "UseFastTLS" "1" [/COLOR]
     BusID       "PCI:2:0:0"  
 EndSection  
 
**   D) Mine:**
  Section "Device"  
     Identifier  "aticonfig-Device[0]-0" 
     Driver      "fglrx"
    [COLOR=Black]BusID       "PCI:2:0:0" [/COLOR] 
 EndSection  
 
That's all about the differences, having in mind that yours I can't open on Text Editor but only Word Processor even if I erase the [.odt] suffix. Before I edit/change anything... which essential modifications shall I do in order to have em on the same format/code/etc to open both on the same program?

**3.- **Another thing that's worying me is that at the same folder there's a file [xorg.conf.fglrx-0] do you also have this one file on your folder?

But there's another thing that I might mention; tibia, which is a game that requires way too much more graphical memory than quadrapassel; runs perfectly well. Then I don't know why the horrendous Quadrapassel does not run well... not that I like that game but it's something that wories me...

One last question is, normally how much graphical memory does the dedicated graphic cards have? Mine is not dedicated and I have read that it has 512mb but VirtualBox does not let me assign more than _128mb_ is there a chance that what I have read was wrong and I only have 128? Thanks people

mastablasta hello! I didn't see your response before sending mine, yeah :/ I think compiz sucks a lot for my needs... I have my desktop effects on medium probably i'm turning em completely OFF! D:

Sincerely, Julian Luna and sorry for my lame english

Edit: Should I be able to run games under a VirtualBox? Cause they keep crashing I think because of the graphics...

---

### Post by cottfcfan on 2011-04-22
Hi Julian,
Theres nothing wrong with your xorg.conf, and yes i copied and pasted mine into open office because it would not upload.
I also didn't realize you were running ubuntu in virtual box.
The fact it is only assigned 128/512 mb memory will cause it a big hit.
Why don't you try dual booting and installing it on your hard drive, chances are it will run a lot better, but never having used virtualbox I don't know.
Anyway I don't see you have any real issues there.

---

### Post by mastablasta on 2011-04-22
virtualisation takes (and needs) a lot of CPU and RAM. Porbably the cards GPU is not even utilized in it but instead all porcessing is likely done by CPU instead. Which increases the load.
 
8GB+
dual or Quad core CPU should increase virtualization experience. Otherwise unless necessary the OS is better run in normal environment. Even Wubi (which still uses some virtualization) will be slower than real install.

---

### Post by Julian Luna on 2011-04-22
No, I got missunderstood, my host is Ubuntu 10.10 and i'm running as Guest Windows XP :] I also already thought on installing Seven on another partition :(

---

### Post by Claus7 on 2011-04-22
Hello,

I have not followed you very closely from the beginning, yet:

1) the xorg.conf files are under /etc/X11
2) in case there is a xorg.conf file exactly like that:
/etc/X11/xorg.conf

then this is the file that your graphics card will use. In the recent versions of ubuntu it is not needed, yet this is not the case for all the graphics cards.

As a result if you do have a xorg.conf like that then one more thing you could do is to create a new one by typing:
sudo aticonfig --initial -f
that way, along with your hardware, one xorg.conf will be created automatically. It does not mean that it will work out of the box though.

before, just bakcup your existing xorg.conf file by typing:
sudo cp /etc/X11.xorg.conf /etc/X11/xorg.conf.backup

Since you are under /etc directory, you need to type these commands (and every single change you like) as root.

edit1: I think that from the specs you give, 2GB of ram, are more than enough.
edit2: If you are using virtual desktop and you have windows xp in it, and you want to play the game inside virtual desktop (guest) then you should have in mind that virtual desktop uses a "simulated" graphics card and not the one you are using normally. As a result, the tweaking you are trying to do won't affect much its visual capabilities. I do guess that other applications should work more than ok in it.

Regards!

---

### Post by Yellow Pasque on 2011-04-22
128MB of graphics RAM is the max allowed for one VM in Virtualbox. It is probably not directly mapping your video RAM either (and if your video card is using shared/system memory, then it doesn't matter). You should probably try to use 1GB for a Win7 VM, unless you need more than 1GB RAM for the rest of your system or are trying to run multiple VM's. Preferably, you would upgrade to 4GB of RAM and/or run Win7 on its own partition. Anyway...

I'm not sure why Quadrapassel is acting up. What other games do you have installed and how do they perform? Maybe there is an issue with python graphics on your system (QP uses python).

BTW, this forum uses [ CODE ][ /CODE ] to make text boxes.

---

### Post by Julian Luna on 2011-04-24
Thanks people you are really helpfull

---

