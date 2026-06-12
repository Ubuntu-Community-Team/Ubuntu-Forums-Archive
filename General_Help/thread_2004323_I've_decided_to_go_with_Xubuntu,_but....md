---
title: "I've decided to go with Xubuntu, but..."
date: 2012-06-15
forum: General Help
---

### Post by Cyberpawz on 2012-06-15
I have decided to bite the bullet and use Xubuntu... that being said after watching it install, I've noticed a lot of extra things being installed I will never use. 

I am going to trick out the desktop, but I'm going to be using the laptop as a word processor, and possibly to play my music on. 

Is there a way to streamline Xubuntu any more? And before someone says Lubuntu, please don't.

---

### Post by flemur13013 on 2012-06-15
Maybe Arch?  It installs easily, has lots of packages to add via 'pacman' and has very good documentation.   In one afternoon I was able to make it act like my ubuntu 12 setup (internet, sound, video, fonts, etc) except for volume management w/thunar (or whatever).

---

### Post by kanikilu on 2012-06-15
Well, if you know what you don't need, why not just remove/purge those packages?

Another way is to build the system up manually using the minimal CD (or even the server installation). Then just install the XFCE desktop environment (sudo apt-get install xfce4) - not the xubuntu-desktop meta-package, since that will pull in more, and then only add what you know you want/need.

---

### Post by Cyberpawz on 2012-06-15
> **kanikilu said:**
> Well, if you know what you don't need, why not just remove/purge those packages?

Another way is to build the system up manually using the minimal CD (or even the server installation). Then just install the XFCE desktop environment (sudo apt-get install xfce4) - not the xubuntu-desktop meta-package, since that will pull in more, and then only add what you know you want/need.

I did the minimal install CD, and its still pulling in more than I need. How do I find what packages have been installed, and how do I purge them?

---

### Post by cortman on 2012-06-15
> **Cyberpawz said:**
> I did the minimal install CD, and its still pulling in more than I need. How do I find what packages have been installed, and how do I purge them?

If you did the minimal CD and installed "xubuntu-desktop" it's no different than simply installing Xubuntu.
You need to do the minimal CD and install

```
xorg
xfce4
```

and some sort of login manager (GDM, LightDM, LXDM) unless you want to log in the command line and run startx every time.
I heartily recommend the Minimal CD- it's what I use for all my Ubuntu installations.

---

### Post by Cyberpawz on 2012-06-15
> **cortman said:**
> If you did the minimal CD and installed "xubuntu-desktop" it's no different than simply installing Xubuntu.
You need to do the minimal CD and install

```
xorg
xfce4
```

and some sort of login manager (GDM, LightDM, LXDM) unless you want to log in the command line and run startx every time.
I heartily recommend the Minimal CD- it's what I use for all my Ubuntu installations.

I do too, but when I say minimal, I mean no games, no multimedia stuff except a music player, no apps except a word processor, no extra stuff... 

A terminal, a word processor, bare-bare bones Xubuntu, and that's it... I guess I want something more simple than the average bear calls simple.

---

### Post by Rodney9 on 2012-06-15
A easy to follow guide on installing a minimal Ubuntu -

[http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

then install Abiword for word processing 
and Audacious, or what ever is your favourite music player.

Rodney

---

### Post by kanikilu on 2012-06-15
> **Cyberpawz said:**
> How do I find what packages have been installed, and how do I purge them?

It will be a long list, but an easy way to get it is: ```
dpkg --get-selections > ~/packages.txt
``` This will save a list of installed packages to a text file in your your home directory.

I can't tell you which ones you'd need or not need, but if you search through the list and find something you don't want, just remove it: ```
sudo apt-get remove packagename
``` If you want to remove any system conf files that the package created as well, just use "purge" instead of "remove".

Once you've removed some packages, it should tell you if there are any others that are not needed anymore (for instance if they are dependencies of something you removed). To clean those up as well, run ```
sudo apt-get autoremove
```

---

### Post by Cyberpawz on 2012-06-15
> **Rodney9 said:**
> A easy to follow guide on installing a minimal Ubuntu -

[http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

then install Abiword for word processing 
and Audacious, or what ever is your favourite music player.

Rodney

I usually go to command line install, so the only thing installed originally is the core ubuntu... I hate to say it but perhaps Ubuntu isn't for me?

---

### Post by Rodney9 on 2012-06-15
> **Cyberpawz said:**
> I usually go to command line install, so the only thing installed originally is the core ubuntu... I hate to say it but perhaps Ubuntu isn't for me?

At the end of that tutorial all you have is the command line, you decide what you want from there.

---

### Post by cek on 2012-06-15
For all this work, you could have installed Arch, or even Gentoo.

---

### Post by kanikilu on 2012-06-15
> **Cyberpawz said:**
> I usually go to command line install, so the only thing installed originally is the core ubuntu... I hate to say it but perhaps Ubuntu isn't for me? flemur13013 suggested Arch, and I'd second that.

Although, looking at the package information for xfce4 in Ubuntu ([http://packages.ubuntu.com/precise/xfce4](http://packages.ubuntu.com/precise/xfce4)), I don't see anything extraneous like games.

Can you confirm how you installed it? If you used the minimal CD, I think by default it uses *tasksel* to let you choose packages to install. But those are meta-packages. If you chose "Xubuntu Desktop" from that list, as has already been pointed out by cortman, that would definitely pull in more packages than "vanilla" xfce:

[http://packages.ubuntu.com/precise/xubuntu-desktop](http://packages.ubuntu.com/precise/xubuntu-desktop)

---

### Post by kanikilu on 2012-06-15
By the way, if you like the Debian way of doing things, I've used CrunchBang before on my netbook, and it's pretty darn lightweight. It uses Openbox by default, but there's no reason you couldn't install xfce4 from the repos...

---

### Post by cortman on 2012-06-15
If your skills are up to it and you're willing to take your time, Arch would be great for you.
I doubt you installed only xfce4 if you got a ton of other programs in the process. AFAIK it doesn't come with anything besides the DE- even gnome-shell comes with really nothing more than gnome-terminal, nautilus, and gedit.

---

### Post by BBQdave on 2012-06-15
> **cek said:**
> For all this work, you could have installed Arch, or even Gentoo.

+1

And too, Xubuntu and Fedora Xfce spin are blends of Xfce and Gnome. The smoothness and friendly-ness of these distros is the extra packages.

If you are looking for a specific build (few applications), Arch and Gentoo is your scene.

If you like the smoothness of Xubuntu, don't sweat the little extras :)

Of the two, Fedora Xfce seems a little tighter than Xubuntu. Though it might be my perception, as I am running F16 (64-bit) Xfce :D

---

### Post by Cyberpawz on 2012-06-15
> **cortman said:**
> If your skills are up to it and you're willing to take your time, Arch would be great for you.
I doubt you installed only xfce4 if you got a ton of other programs in the process. AFAIK it doesn't come with anything besides the DE- even gnome-shell comes with really nothing more than gnome-terminal, nautilus, and gedit.

To me a ton of things are things like extra packages such as python, useless things that boot up when you start up, etc...

I'll look at Arch. I'm looking for something in where the bare apps are installed, but a full feature of system preferences are not left behind.

Networking, GUI setups, and as I said, terminal to install things, and an editing program...

I'm not looking for anything fancy except for being able to custom my own desktop, icons, and effects the way I want to... make the login screen my own creation, same with desktops, etc...

I was originally looking at XFCE-Crystal, but the support died a while back...

I'm looking for something with a no-nonsense setup, where settings are in the control panels, applications are where they are meant to be, and any extra terminal commands are left in the terminal, and not spread through the entire menu list.

I'm looking where if I want python installed or a web server installed I will install it myself...

Does this make any sense? 

I want a desktop environment that will allow me full customization, but install nothing including a web browser without my input...

Is this even possible, or am I asking for "too much"?

---

### Post by cortman on 2012-06-17
> **Cyberpawz said:**
> To me a ton of things are things like extra packages such as python

This tells me that perhaps your skills aren't quite Arch-ready- just about every DE and WM in existence relies on Python. Python is an essential part of any GUI system.

If you're looking for something that is GUI minimum and aren't completely stuck on XFCE, you could try [Bodhi Linux]("http://bodhilinux.com/")- installed programs include one web browser, one terminal, and one text editor, one file manager, and that's it. It's based on Ubuntu and uses the Ubuntu repos so you're good to go there. I use Bodhi on my netbook and am very pleased with it.

---

### Post by Cyberpawz on 2012-06-18
> **cortman said:**
> This tells me that perhaps your skills aren't quite Arch-ready- just about every DE and WM in existence relies on Python. Python is an essential part of any GUI system.

If you're looking for something that is GUI minimum and aren't completely stuck on XFCE, you could try [Bodhi Linux]("http://bodhilinux.com/")- installed programs include one web browser, one terminal, and one text editor, one file manager, and that's it. It's based on Ubuntu and uses the Ubuntu repos so you're good to go there. I use Bodhi on my netbook and am very pleased with it.


That is pretty much what I am looking for. As for not being ready for Arch cause of the python comment, I'd have to dissagree. 

I'm not a developer, so most new people who install Ubuntu and other Linux distros never go past the GUI. So I was slightly amazed the GUI uses python. 

Thanks for the advise though.

---

### Post by cortman on 2012-06-18
> **Cyberpawz said:**
> That is pretty much what I am looking for. As for not being ready for Arch cause of the python comment, I'd have to dissagree. 

I'm not a developer, so most new people who install Ubuntu and other Linux distros never go past the GUI. So I was slightly amazed the GUI uses python. 

Thanks for the advise though.

I may have read more into it than is true; I sure didn't know everything when I did my first Arch installation (and I'm still very much a Linux novice)- good luck with whatever you choose!

---

### Post by c2tarun on 2012-06-18
Try to take a bigger bullet ;) try bodhi linux once.
Please do share your feedback.

---

### Post by Cyberpawz on 2012-06-18
> **c2tarun said:**
> Try to take a bigger bullet ;) try bodhi linux once.
Please do share your feedback.


Actually I'm trying Bodhi Linux, and I'll tell you right now, I'm nearly in love with it's simplicity, and yet functionality. 

It doesn't seem to have a lot of what I call "Fat" in it, which are extra programs, and it boots up less than 30 seconds on my laptop... now mind you it is more than 10 years old too...

I do like the splash screen, I actually wish I could make that into a desktop. Make it so the desktop can change, but have the flowing leaves running in front of it. 

I haven't played with it much, but with all the effects it has out of the box, and as "neat" as the desktop is, I think I have found what I was looking for. 

The only thing I wish, and this is just me, but I see that every time a major rev change comes up, you need to re-install from scratch? 

This isn't a bad thing, just something I noticed, and can be an annoyance for other people, thankfully my home folder is on another partition, but those who didn't do that, are going to be in pain backing things up before installing a new rev...

I wish though that the GRUB would just never show up on first boot. I honestly don't think there is a reason for it, but that's just me.

Overall, a good build, I'll report back if I can about how well it does other things soon.

I would love to see Ubuntu to have this one of their options if you are doing a net install/Minimum CD...

---

### Post by c2tarun on 2012-06-18
> **Cyberpawz said:**
> Actually I'm trying Bodhi Linux, and I'll tell you right now, I'm nearly in love with it's simplicity, and yet functionality. 

It doesn't seem to have a lot of what I call "Fat" in it, which are extra programs, and it boots up less than 30 seconds on my laptop... now mind you it is more than 10 years old too...

I do like the splash screen, I actually wish I could make that into a desktop. Make it so the desktop can change, but have the flowing leaves running in front of it. 

I haven't played with it much, but with all the effects it has out of the box, and as "neat" as the desktop is, I think I have found what I was looking for. 

The only thing I wish, and this is just me, but I see that every time a major rev change comes up, you need to re-install from scratch? 

This isn't a bad thing, just something I noticed, and can be an annoyance for other people, thankfully my home folder is on another partition, but those who didn't do that, are going to be in pain backing things up before installing a new rev...

I wish though that the GRUB would just never show up on first boot. I honestly don't think there is a reason for it, but that's just me.

Overall, a good build, I'll report back if I can about how well it does other things soon.

I would love to see Ubuntu to have this one of their options if you are doing a net install/Minimum CD...




hmm... we started quite similar. Initially I was also in love with bodhi linux, but I dont know why, on heavy use, bodhi's performance degrades. Heavy use like, I used eclipse, android-emulator, music, browsers, skype and IRC at once and within 15 mins I can feel the lag. So I switched form bodhi linux to Ubuntu, it starts slow then bodhi linux, but it is equally fast, and more stable.

---

### Post by cortman on 2012-06-18
> **Cyberpawz said:**
> Actually I'm trying Bodhi Linux, and I'll tell you right now, I'm nearly in love with it's simplicity, and yet functionality. 

Welcome to Bodhi. :) It's a terrific distro.
Not sure what you mean about major rev change; AFAIK that only happens when a new LTS is introduced, which won't happen for another three years.
And it's best to reinstall then anyway.

---

### Post by vasa1 on 2012-06-18
> **cortman said:**
> Welcome to Bodhi. :) It's a terrific distro.
Not sure what you mean about major rev change; AFAIK that only happens when a new LTS is introduced, which won't happen for another three years.
And it's best to reinstall then anyway.
IIRC, the LTS based on 12.04 is yet to come. So it will be soon. Right now I think it's in alpha.

Edit: details: [http://jeffhoogland.blogspot.in/2012/06/bodhi-linux-200-faq.html](http://jeffhoogland.blogspot.in/2012/06/bodhi-linux-200-faq.html)

---

### Post by Cyberpawz on 2012-06-18
> **c2tarun said:**
> hmm... we started quite similar. Initially I was also in love with bodhi linux, but I dont know why, on heavy use, bodhi's performance degrades. Heavy use like, I used eclipse, android-emulator, music, browsers, skype and IRC at once and within 15 mins I can feel the lag. So I switched form bodhi linux to Ubuntu, it starts slow then bodhi linux, but it is equally fast, and more stable.

I'm only using it for word processing, email, and perhaps a music player... beyond that...it's going to be very limited use.

Again, this laptop is 10 years old, made in 2002, it's not going to be doing the stuff you do. 

I will say that this runs significantly faster than Ubuntu with Unity...at least for what I need. 

You may be right in the long run but for now, I see the system running smoothly. I'm very happy with what I see. when I installed Ubuntu with Unity the system felt like it was running Windows XP... I wasn't thrilled. One of the reasons I wanted to go with Xubuntu was because it was one of the few choices I seem to be stuck with. 

I'm glad I persisted because right now this OS seems to run just the way I wanted when I thought I was installing Ubuntu for the first time.

---

### Post by Cyberpawz on 2012-06-19
After dealing with some thing we all take for granted, updating, or changing things over to something a bit more user friendly, I have decided to stick with Bhodi. 

A little bit of streamlining, and off I go. Thanks for the helps peeps. This OS is great for an old system like mine, for as little as I need done with it and all.

---

### Post by cortman on 2012-06-19
> **Cyberpawz said:**
> After dealing with some thing we all take for granted, updating, or changing things over to something a bit more user friendly, I have decided to stick with Bhodi. 

A little bit of streamlining, and off I go. Thanks for the helps peeps. This OS is great for an old system like mine, for as little as I need done with it and all.

Great! Good to see you're willing to tweak and make a few things work rather than throw up your hands and moan about the future of the Linux desktop, like some people. :/

Good luck!

---

