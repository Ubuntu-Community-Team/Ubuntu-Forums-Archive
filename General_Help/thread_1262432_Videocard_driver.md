---
title: "Videocard driver"
date: 2009-09-09
forum: General Help
---

### Post by seandude on 2009-09-09
So, I accidentally got rid of my video card driver, and have now re-downloaded it, but I don't know what to do with it now.  

[FONT=Arial]The instructions for installing the driver are thus:
 Once you have downloaded the driver,   change to the  directory containing the driver package and install the driver by  running, as root, sh  ./NVIDIA-Linux-x86-185.18.36-pkg1.run[/FONT]

What I want to know is this; where do I move the driver to?  when I type in the command ([FONT=Courier New]sudo sh ./NVIDIA-Linux[/FONT] ... etc)  I get back "[FONT=Courier New]sh: Can't open ./NVIDIA-Linux[/FONT] ...etc".  What's happening here?

Also, is there anything else I'm doing wrong here?

---

### Post by seandude on 2009-09-09
I read the readme on Nvidia's website, it made no sence.  I really do need help.

[http://www.nvidia.com/object/linux_display_amd64_185.18.36.html](http://www.nvidia.com/object/linux_display_amd64_185.18.36.html)

---

### Post by lildigiman on 2009-09-09
You'd be better off installing the Driver from  System > Administration > Hardware Drivers

---

### Post by Perfect Storm on 2009-09-10
> **lildigiman said:**
> You'd be better off installing the Driver from  System > Administration > Hardware Drivers

+1

The only reason you should install the drivers from nvidia homepage is if your card isn't supported in the driver ubuntu ships with.
Normally you don't need to hunt down drivers/apps/libs in Ubuntu. If there's a driver available for your card you'll find it at System > Administration > Hardware Drivers.
Another thing is; If you install th Nvidia driver manually - you need to re-install them after each kernel patches/updates.

Apps you can find it Add/remove in the applications tab or by using Synaptic Package Manager.

---

### Post by seandude on 2009-09-10
Thank you both of you.  That worked wonderfully.  I was dreading a long bout of compiling and configuring.  

Just out of curiosity, what would I have to do to manually install it?

---

### Post by Perfect Storm on 2009-09-10
> **seandude said:**
> Thank you both of you.  That worked wonderfully.  I was dreading a long bout of compiling and configuring.  

Just out of curiosity, what would I have to do to manually install it?

Something like;

Download the driver to your Desktop.
Then;

```
sudo apt-get install build-essential
sudo apt-get remove --purge nvidia-settings nvidia-common nvidia-glx-180
```

<alt>+<ctrl><F1>
Then you're running in CLI mode
Then;
```
cd ~/Desktop
sudo /etc/init.d/gdm stop
chmod +x <name of the driver>
sudo sh <name of the driver>
nano /etc/X11/xorg.conf
```

set the driver to nvidia in the conf file.

<ctrl>+<o> = save
<ctrl>+<x> = exit

```
sudo /etc/init.d/gdm start
```

If you're using eg. kubuntu which uses KDE instead of gnome, the gdm is changed to kdm

---

### Post by seandude on 2009-09-10
A couple of questions;

Why would I get rid of the nvidia settings?
What is nvidia common?
what does glx-180 do as opposed to glx-96?
What does <alt><ctrl><f1> do? put me in CLI mode?
what is CLI mode?
What do the commands stop, sh, and nano do?
What do those configurations mean?

Sorry that that's a lot of questions.

---

### Post by Perfect Storm on 2009-09-10
> **seandude said:**
> A couple of questions;

Why would I get rid of the nvidia settings?

Too purge/remove all the previous settings and then install it again.
> What is nvidia common?
It's the backbone of the nvidia driver on Ubuntu.

> what does glx-180 do as opposed to glx-96?
It's a newer driver that works excellent with 8xxx series.

> What does <alt><ctrl><f1> do? put me in CLI mode?
[http://www.scribd.com/doc/18804848/Linux-Has-7-Different-Run-Levels](http://www.scribd.com/doc/18804848/Linux-Has-7-Different-Run-Levels)

> what is CLI mode?
Comandline interface

> What do the commands stop, sh, and nano do?
the command stop, means it stop eg. the current application if it's running in the background. sh is; [http://en.wikipedia.org/wiki/Bourne_shell](http://en.wikipedia.org/wiki/Bourne_shell) and nano is a CLI text editor.

> What do those configurations mean?
Means to set something up or changing it.

> 
Sorry that that's a lot of questions.

No problem. you can **man** (manual) each of the command in the terminal. Eg. **man nano**

---

