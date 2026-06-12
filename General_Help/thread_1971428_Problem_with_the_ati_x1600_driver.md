---
title: "Problem with the ati x1600 driver"
date: 2012-05-02
forum: General Help
---

### Post by eferkan on 2012-05-02
Hello everybody. I am a new user of linux, ubuntu, terminal and even to this forum. I am really having fun while trying to learn things about linux. I am using Ubuntu 12.04lts right now and i am not having too much trouble, just one, about the graphic card ati x1600.
I did lots of stuff about the packages and the "sudo apt-get update" kinda things and more but could not solve my problem for about 3whole days. I learned that after the ubuntu 8.04 i am not able to install the proper fglrx driver for my gpu, so i installed ubuntu 8.04 but after i did that i realized it is only text mode and i am not that skilled to handle the kernel for now.
So now i need some information and suggestion about what should i do.
Is there any simple way for me to create a desktop style thing for 8.04, it is so called gnome i think but i am not sure. And is it enough for me to use 8.04 with a graphical user interface?
Is there any way for me to use 12.04 with a proper fglrx driver?
And my expectations from my computer is the Mozilla, 1game called Heroes of Newerth, some office programs, and watching movies and listening to music. Not that much i guess :)
I hope i could express myself correct and any help will be deeply appreciated.
Thanks in advance, have a nice day.

edit: i am also having trouble watching movies from mozilla like "youtube" videos etc, but i think it is from the same problem above?

---

### Post by The Rnegade on 2012-05-02
> **eferkan said:**
> Hello everybody. I am a new user of linux, ubuntu, terminal and even to this forum. I am really having fun while trying to learn things about linux. I am using Ubuntu 12.04lts right now and i am not having too much trouble, just one, about the graphic card ati x1600.
I did lots of stuff about the packages and the "sudo apt-get update" kinda things and more but could not solve my problem for about 3whole days. I learned that after the ubuntu 8.04 i am not able to install the proper fglrx driver for my gpu, so i installed ubuntu 8.04 but after i did that i realized it is only text mode and i am not that skilled to handle the kernel for now.
So now i need some information and suggestion about what should i do.
Is there any simple way for me to create a desktop style thing for 8.04, it is so called gnome i think but i am not sure. And is it enough for me to use 8.04 with a graphical user interface?
Is there any way for me to use 12.04 with a proper fglrx driver?
And my expectations from my computer is the Mozilla, 1game called Heroes of Newerth, some office programs, and watching movies and listening to music. Not that much i guess :)
I hope i could express myself correct and any help will be deeply appreciated.
Thanks in advance, have a nice day.

edit: i am also having trouble watching movies from mozilla like "youtube" videos etc, but i think it is from the same problem above?

follow this guide  to install fglrx properly 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by |{urse on 2012-05-02
I have had loads of "fun" in the past with getting my x1650 pro 256mb to play nice with linux.

This card will play adobe flash and videos much better in general if you disable compositing (several ways to do this). Are you experiencing flickering and flashing while playing videos/video games?

---

### Post by QIII on 2012-05-02
This appears to be a legacy card, which means that any ATI driver after 9.3 will fail.  Don't install driver 12.4.

I'm on my cell right now and can't give you a link, but if you google the terms

ati x1600 legacy

You should find an ATI page explaining what to do.  

After installing the driver and BEFORE rebooting, be sure to do

```
sudo aticonfig --initial
```

in the terminal to generate an initial xorg.conf.  Otherwise, you will likely be staring at a blank screen and cursing.

---

### Post by eferkan on 2012-05-02
@Rnegade it is not the problem installing the fglrx driver, it does not support my gpu for 12.04.

@|{urse i did installed the proprietary driver but it did no good for the game i try to play

@QIII as far as i know, the older vers is can not work on 12.04

But anyway thanks all of you guys

---

### Post by |{urse on 2012-05-02
Try disabling compositing before you give up on that card ;)

---

### Post by eferkan on 2012-05-02
> **|{urse said:**
> Try disabling compositing before you give up on that card ;)

Sorry but i am not that skilled, how can i do that?
And also do you think it is a solution to play Heroes of Newerth?
thnx in advance

---

### Post by Mark Phelps on 2012-05-03
> **eferkan said:**
> ... Is there any way for me to use 12.04 with a proper fglrx driver?...
Despite what others may have told you, the answer is NO.

AMD dropped support for fglrx drivers for your video card back with Ubuntu 8.10.  There are no fglrx drivers that will work with your card and any Ubuntu version newer than 8.10.  If you FORCE the installation of fglrx drivers, you will trash your display and have to go through a LOT of work to get a working display back.

---

### Post by QIII on 2012-05-03
Thank you Mark.

I will now grin sheepishly, since I should have just stopped without my knee jerk advice to run aticonfig, knowing it wouldn't work.  Stupid from a guy who spends half his time helping with ATI driver issues on the forum.

For the OP:  It's not that it won't work just on Ubuntu.  The 9.3 driver won't work on *any* distro with X Server 1.6 and beyond.

---

### Post by NotSoTangible on 2012-05-21
eferkan: the optimal driver you can get for your video card in Ubuntu 12.04 is the open source "radeon" driver that ships with the operating system, no additional installation required.
I would suggest you do not install Ubuntu 8.04 as this version isn't supported anymore on the desktop.
I've just tried on a X1100-equipped laptop: Heroes of Newerth will work with the free drivers, although you might want to hunt down a file called "libstdc++.so.6" located in the game's libs-x86 or libs-x86_64 folder (depending on whether you are running the 32 bit or 64 bit version of Ubuntu) and remove it, see [http://lists.freedesktop.org/archives/dri-devel/2011-July/012728.html]("http://lists.freedesktop.org/archives/dri-devel/2011-July/012728.html")
Also, as suggested by |{urse,  switch to "Ubuntu 2D" from the login screen (click on the cog wheel thingie above the login password field) for a snappier desktop.

---

### Post by insanelyapple on 2012-07-04
So, theres no chance for Unity with 3D in 12.04? I have same gpu - X1600 PCI-E 71c3.

---

