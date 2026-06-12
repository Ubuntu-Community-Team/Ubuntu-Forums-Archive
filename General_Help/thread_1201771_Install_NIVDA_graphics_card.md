---
title: "Install NIVDA graphics card"
date: 2009-07-01
forum: General Help
---

### Post by Karinab on 2009-07-01
I am very new to ubuntu, so I may need a bit of remedial help...

I just bought a computer from Ibuypower, and decided that I just wanted to run ubuntu, so I had them send it to me blank..

now I have ubuntu.

I've been having problems playing movies and music, I think I need to install my graphics card somehow, but the install CD doesnt have any files that run, they don't seem to know which program to use. are there any install drivers that i need to get?

please help!

---

### Post by bekind2thenoob on 2009-07-01
Please clarify:

do you have ubuntu installed currently or are you running it off the cd?

have you installed any drivers for your NVIDIA card??

it sounds like you just need to install codecs to play restricted formats what happens when you try to play media files?

---

### Post by colau on 2009-07-01
> **Karinab said:**
> I am very new to ubuntu, so I may need a bit of remedial help...

I just bought a computer from Ibuypower, and decided that I just wanted to run ubuntu, so I had them send it to me blank..

now I have ubuntu.

I've been having problems playing movies and music, I think I need to install my graphics card somehow, but the install CD doesnt have any files that run, they don't seem to know which program to use. are there any install drivers that i need to get?

please help!
System>Administration>Hardware Drives

---

### Post by abhi_69 on 2009-07-01
u can either use official build from nvidia website (1st read instructions before installation) or ubuntu build form repo.
if u install ur video card driver properly, then u may need some codecs to play various media formats. just enable Medibuntu repo. & type in terminal-
*************
$ sudo apt-get install ubuntu-restricted-extras
*************
this will install everything u need to play media.
to play DVD u may also need these-
***********
$ sudo apt-get install libdvdread4 libdvdcss2 lsdvd regionset 
***********
hope this will help.

---

### Post by ShadowWraith on 2009-07-01
First you can easily make sure that your graphics drivers aren't already installed. Do that by going in the menu to System->Preferences->Appearance, clicking on the Visual Effects tab, and clicking the "Normal" radio button. If visual effects are activated, that means your graphics drivers are installed. If not, keep reading.

I have found the official drivers for NVIDIA cards to be easier to install, but messier and buggier.

The official drivers are more difficult to install, but if you don't mind looking for packages and messing around in the console, they are IMHO a much better choice.

If you wish to install the official NVIDIA drivers, you must have a basic knowledge of the command line.

Drivers for nvidia cards can be downloaded at [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) . Just enter the model of your card and press search, and a page will be provided with a download link.

[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/index.html) is a readme with instructions on how to install the NVIDIA drivers on all *nix systems. Mostly what you have to be careful about is having all the required packages.

Make sure you have the software listed here [http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/chapter-02.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/chapter-02.html) It is all provided as packages in Ubuntu (make sure you get the -dev variants!)

Then, press ctrl-alt-f1 to enter the console and when there, log in (you can return to the GUI with ctrl-alt-f7). Find the NVIDIA driver file, and
chmod 755 <name-of-the-file>
that will make it executable.
Then, you must shut off the GUI:
sudo /etc/init.d/gdm stop

Now run the file with sudo:
sudo ./<name-of-file>

This will bring you to the NVIDIA installer. If everything is correct, it will compile a kernel interface and offer to run nvidia-xconfig. Say yes and your driver installation will be complete.

To test that everything is working, start the GUI with:
sudo /etc/init.d/gdm start

And when you are in GNOME, open a terminal and type:
glxgears

If you can see the animation, your graphics drivers work. Congratulations!

NOTE: When you make a kernel update, you will have to reinstall the drivers.

---

### Post by Karinab on 2009-07-01
Please excuse me, because I'm very new to much of this.

What is GUI?
Do i need to use the CD that I have at all, or will the drivers that you gave me the websites for suffice?
I'm pretty sure my graphics card is not installed because when I want to upgrade the visual effects it says my system doesn't support it.

And about having all the software necessary... I've just installed ubuntu and haven't added anything else (I will be getting the internet hooked up to that computer soon). does the default system come with everything I'll need?

Thanks again Shadow!

---

### Post by ShadowWraith on 2009-07-01
GUI means Graphical User Interface. In other words, the windows and buttons on your screen. Without it, the computer simply gives you a "command line" of all text, into which you must type commands. Become familiar with the command line before you try the advanced method of graphics driver installation.

You may have installed the graphics drivers when you installed Ubuntu. Ubuntu usually asks you "would you like to install restricted drivers?" or something of the like. Nevertheless, the best thing to do is to test if your computer already has 3d drivers.

That said, videos can be played without 3d card drivers, but since you mentioned that you have not set up the computer's internet connection, it is clear why you cannot play videos; you must first install the correct codecs or a video playing program that can decode them.

Two good options are the VLC player and Mplayer.
You can install either by going to System->Administration->Synaptic Package Manager in the menu. Synaptic is a program that helps you install other Ubuntu programs, called "packages".
Go to the search bar in Synaptic and type vlc , then click "Search". You will get a list of packages. Click the box next to the one that says "vlc" and click "Mark for installation". Then press the button on top that says "Apply". This will install vlc.

Now you can go to any video you have, right click on it, select "Open with vlc", and it should play.

In order to play commercial dvds, which are encrypted, you have to follow these instructions:
[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

This should solve all your playback problems.

The easy way to install NVIDIA drivers is to follow this tutorial:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

Unless you experience trouble with Ubuntu's NVIDIA drivers, there is no reason to put yourself through the pain of following the instructions I posted above; I only outlined them because that is the way I do it since I have had problems with driver instability in earlier versions of Ubuntu, so I'm a bit paranoid about it and like to have more control. As far as I know, the current Ubuntu NVIDIA drivers work fine.

Good luck!

---

