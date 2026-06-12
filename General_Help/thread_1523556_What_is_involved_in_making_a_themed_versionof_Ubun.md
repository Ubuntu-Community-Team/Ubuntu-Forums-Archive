---
title: "What is involved in making a themed versionof Ubuntu?"
date: 2010-07-03
forum: General Help
---

### Post by Nick_Jinn on 2010-07-03
Lets say somebody wanted to make a themed version of Ubuntu for Activists and came with tools and programs just for that purpose...programs for video streaming and web hosting from a non server desktop (I guess its a server, but it would be from a graphical GUI that you can still surf the web with, kind of like what the Opera web browser now has), tools for making fliers beyond just GIMP, video editing for making documentaries, open office tools for making zines or whatever tools are needed, perhaps links to Infoshop and Indymedia built into the desktop and browsers as default, ect ,ect.

So if somebody wanted to do this, would they have to be a programmer, or is there a simple way of doing it?

---

### Post by SmokeyThePanda on 2010-07-03
I am not certain of all of the packages you would need to install, but you could install a base system of ubuntu and add them..It would be as you say "themed", but it would be yourself that themes it. You would have an ubuntu skeleton and then add what you want to it. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Above is a link to the mini.iso. You would use it to install an ubuntu skeleton. Once you load your system with the CD, you will find yourself at a command prompt. You would then run the command:

*cli*

This stands for Command Line Install. It will install the skeleton for you. It will take a while because it has to download all of the files. After it is done, you will restart and be brought back to the command line. 

From this point, you can install whatever packages you feel you need. You would need synaptic, a window manager, xorg and gdm at the very minimum. For a very lightweight install you could use the following: 

[I]sudo apt-get install xfce4 xorg gdm synaptic

[/I]You may replace xfce4 with whatever window manager you like. *gnome-core* is good if you like gnome. Then, you could install each of your programs from the command line or run:

[I]xstart

[/I]Xstart would then take you to your desktop, which will look really bland if you chose xfce4. Once you got to your desktop, you could open synaptic with Right Click --> Applications --> System --> Synaptic Package Manager. Then just install the programs you want from there. It's rather easy and takes up alot less space than doing a normal ubuntu/xubuntu/kubuntu/edubuntu install. 

I went a little bit too much into detail..But meh. This is the closest thing I can think of to "Theming" your own ubuntu.

---

### Post by /b/rotard on 2010-07-03
> **SmokeyThePanda said:**
> I am not certain of all of the packages you would need to install, but you could install a base system of ubuntu and add them..It would be as you say "themed", but it would be yourself that themes it. You would have an ubuntu skeleton and then add what you want to it. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Above is a link to the mini.iso. You would use it to install an ubuntu skeleton. Once you load your system with the CD, you will find yourself at a command prompt. You would then run the command:

*cli*

This stands for Command Line Install. It will install the skeleton for you. It will take a while because it has to download all of the files. After it is done, you will restart and be brought back to the command line. 

From this point, you can install whatever packages you feel you need. You would need synaptic, a window manager, xorg and gdm at the very minimum. For a very lightweight install you could use the following: 

[I]sudo apt-get install xfce4 xorg gdm synaptic

[/I]You may replace xfce4 with whatever window manager you like. *gnome-core* is good if you like gnome. Then, you could install each of your programs from the command line or run:

[I]xstart

[/I]Xstart would then take you to your desktop, which will look really bland if you chose xfce4. Once you got to your desktop, you could open synaptic with Right Click --> Applications --> System --> Synaptic Package Manager. Then just install the programs you want from there. It's rather easy and takes up alot less space than doing a normal ubuntu/xubuntu/kubuntu/edubuntu install. 

I went a little bit too much into detail..But meh. This is the closest thing I can think of to "Theming" your own ubuntu.

isnt it startx?
but anyway, you can also play with several WM's or DE's by getting x, and then using "xinit /usr/bin/startxfce4" or whatever enviorment you want. to change what comes up in startx, you have to edit /home/username/.xinitrc and put "start WM/DE" then "end" on the next line.

---

### Post by SmokeyThePanda on 2010-07-03
Hmm. You're right, I believe. Too many commands running through my head. xD

---

### Post by cbowman57 on 2010-07-03
Or you could get a version that you like, add or subtract what you like, customize the look and create the distro with Remastersys.

---

### Post by SmokeyThePanda on 2010-07-03
The problem with "Getting a system he likes" is it will install 3957823957892357 other programs he doesn't need and installing them like that will make it so you can't delete them without deleting programs/packages that you need. He's asking about creating a themed version. Installing a prebuilt ubuntu is not a theme. If I had installed xubuntu instead of building mine up, it wouldn't feel like it was mine. Therefore, it wouldn't be themed for my needs. For instance, I do not use epiphany browser, but it comes with the ubuntu desktop. If you attempt to remove the epiphany browser, it removes most of the ubuntu desktop as well. Therefore, to combat this, you either install gnome-core which doesn't include all of the programs or you build it up. :p 

Just my thoughts. ^^

---

### Post by Nick_Jinn on 2010-07-03
This is awesome and fascinating. I was afraid that this wouldnt be possible at my level of understanding, but from reading all this it sounds like I might actually be able to pull this off. 

I would like info on both ways of doing it.....In a dream I had I was doing something with XFCE....which is odd because I have never even seen what that desktop looks like till this day. The fact that its light weight would give me room to put all the programs I need on a CD. However, I dont really know everything I would need as a bare minimum since I am not a power user.


Maybe I should try starting with something that already exists and just build onto it for my first attempt, and when I get better at this maybe build it from scratch next....I at least want all the codecs and drivers.

...in fact, I may even want to use Mint as a starting point, simply because it has extra drivers......unless I could add Medibuntu, then I might just stay with regular Ubuntu. I may want to create an XFCE and a E16 version.


But this would be for a good cause (assuming you agree with the cause). It would be a distro that is ready to go 'out of the box' without any tweaking geared for political activists who want to do certain things in a hurry. It would have media links built in, its own IRC page if we are lucky, and perhaps come with the torrent for the distro itself already installed and executes automatically at startup. 

I may have to do a DVD to start until I learn to shave off what is unnecessary, after I learn exactly what is unnecessary. 

It should have some PDF documents sitting on the desktop ready to be read when you open it.



I dont really understand how to do any of that yet, but it does sound like I can start with a distro that exists and maybe add programs. That alone would be really cool if I could do it myself.

---

### Post by SmokeyThePanda on 2010-07-04
Alright, so you are looking at the shaving method. :p As I stated up there, it will be rather difficult to remove some programs/packages this way, but for a first attempt, it would most likely be easier than building up. :p

If you are wanting Xfce, you want Xubuntu. ;)

---

### Post by /b/rotard on 2010-07-04
If you want it to be really lightweight, done use a desktop environment, just use a window manager like fluxbox.

---

### Post by Spr0k3t on 2010-07-04
If you have never built from skeleton before, it's fascinating to say the least.  Throw the iso into a VM with 4GB virtual hard drive and go to town.  Enjoy learning about new functionality and features you never knew about.

---

### Post by SmokeyThePanda on 2010-07-04
I agree, building from scratch is pretty amazing. :p Though, I have a bit smaller hard drive. xD

---

### Post by Spr0k3t on 2010-07-04
flash drives are cheap.  Found a 4GB flashdrive for $8 the other day from a reputable source.  I have heard of cheaper as well.

---

### Post by d3v1150m471c on 2010-07-04
whatever you do just please don't make another one of **[these]("http://www.revlinuxos.com/")**... btw if you want to catch a good laugh just write the developer and give him some civil criticism. public relations are not exactly their bag...kinda makes you appreciate the moderators here.

ROFL... [http://www.revlinuxos.com/about.html](http://www.revlinuxos.com/about.html)

"james (woodsmoke)"

---

### Post by Nick_Jinn on 2010-07-04
> **SmokeyThePanda said:**
> Alright, so you are looking at the shaving method. :p As I stated up there, it will be rather difficult to remove some programs/packages this way, but for a first attempt, it would most likely be easier than building up. :p

If you are wanting Xfce, you want Xubuntu. ;)


I dont think I will start with the shaving method...I think I will go with the keep everything and only add what I need because its the easiest way of doing things method....of course that probably means it will be a DVD installation.

Is there a way to make it a 2 CD installation?  I want it to be as simple as possible with a primarily plug and play action for NON geeks who have never used linux before. I want everything taken care of with ZERO customization involved, and I want to include restricted codecs and Medibuntu, because I dont want any stumbling blocks for activists who want to accomplish something.

Its ok if it comes on 1 DVD, but more people could burn it themselves if it was easier to put on a USB flash drive with purely plug and play action, or if the second CD could set up all the customizations WITHOUT having to add the programs one by one with Synaptic after adding the CD as a source. I would have 1 base CD that is probably Gnome, or XFCE or maybe E16, and I would have the second change everything about the desktop from the background to the installed programs to certain files and torrents being installed automatically. It would get media feeds from various sources fed directly to the desktop in both video and text format, home pages would be added to the browser, and I might use Opera instead of firefox because of the web hosting capabilities, and it would give you access to IRC chat as well as provide the needed tools.



If thats too hard I might just go with making a DVD, and if I do so I might start with Mint since it already has the restricted drivers and codecs, or if XFCE already has enough room for me to add the needed programs on a single CD I might just go with that.


I wont be shaving so much as adding. It will be a feature and program rich distro with no customization needed geared for non geeks who have never used it before and need what they need in a hurry.



There is a definite purpose for what I am trying to do though. Its not just Ubuntu with restricted drives and codecs. The point is to include tools specific to the needs of activists who want to accomplish certain tasks on the fly.

---

### Post by Nick_Jinn on 2010-07-04
> **/b/rotard said:**
> If you want it to be really lightweight, done use a desktop environment, just use a window manager like fluxbox.


I dont really need it to be light weight at all. It might be slightly more convenient if it could be put on a CD. Some people have CD burners but not DVD burners. 2 CDs wouldnt be terrible, but the point is that it can be put on a flash drive or disk.....the only downside of DVDs is that some people dont have DVD burners, but with a flash drive is should be ok.


So, it is possible with 2 CDs?

This isnt intended to be some "New" improved version of Ubuntu. This is for a small group with a specific purpose, and the idea is for everyone to have access to the same tools for working on specific projects. It would give you access to various websites and generic user accounts, have media links from websites like Indymedia and infoshop, and everything about it would be themed for the activist and include tools for making fliers and documentaries.

I guess you could say that I want to 'spoon feed' the users, but not as a replacement for learning how to use the OS, only because I want people to be able to use it in a hurry, like if they arrive in a foreign provide for a major protest, I want people who use it to be socially connected and already have the tools ready to go without having to waste time on customization, though it should allow additional customization if needed.

---

### Post by SmokeyThePanda on 2010-08-07
This post is a bit dated, but I found something that may help the original poster, that is if he still looks at this thread...

[https://build.reconstructor.org/](https://build.reconstructor.org/)

You create and account and you can create your own custom distribution using Debian 5.0 or Ubuntu 9.10/10.04. You add the programs you want on the .iso and you add modules you want loaded. You can make them as big or small as you want and you can make it a live cd or not, depending on what you want. I recently created a basic Ubuntu 10.04 live cd with only the stuff I need for a backup live cd. I haven't tested it yet, but I am quite sure it works. 

You are given $5 in your account each month to use on the site. Certain things cost money from your account to do, like starting a new project and downloading. At the very least, you should give it a try and see if it's anything close to what you're looking for. :)

---

### Post by Nick_Jinn on 2010-08-08
I probably dont want to host it anywhere since I dont have a lot of money. I just want to create something for my small group, but I want it to have its own logo and name. I definitely need the ability to 'rebrand'. 

I dont think Remasterys has that ability...does it?

Can I use Reconstructor with Mint as well as Ubuntu?

---

### Post by Nick_Jinn on 2010-08-08
I dont understand how to use it.

It says I need to choose a project. I want to start my own project, so why do I need to get one from the website? Cant I just take my own ISO and use the tool to edit it?

Im confused about how this works.


Can I use Remasterys to change the login/spash screen/name/logo?

Id be willing to backstep and use Debian/Morphix/Knoppix if the tools for Ubuntu/Mint dont lend themselves well.

---

### Post by Nick_Jinn on 2010-08-08
All I need is the following.....

Rebrand to my own project name
Change the splash screen and replace with my own logo and name
Download the ISO


From there I can do the rest with Remasterys which seemed a little more comprehensive to me.

Id be willing to pay somebody to help me out with this. Im feeling a little confused.

---

