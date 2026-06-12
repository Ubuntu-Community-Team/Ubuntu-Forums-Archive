---
title: "sudo /etc/init.d/gdm stop (It hangs on me, i think)"
date: 2010-05-18
forum: General Help
---

### Post by Werner7 on 2010-05-18
Hey,

I'm having trouble with stopping/shutting down the x server.

the command I used is at the title says;

sudo /etc/init.d/gdm stop


Is this correct? It freezes on me, or just gives a blinking prompt line. An horizontal one and cant do anything. When i press the power button is shuts down nicely though.

I want to install the latest NVidia driver, therefor im doing this.


Thank you!

(having a good time as a almost newbie to ubuntu here)

---

### Post by 3rdalbum on 2010-05-19
I'd recommend sticking with the repository version of the Nvidia driver. It's the one you can install from the Hardware Drivers program.

Now if you really want to install the latest Nvidia driver, then the command you should use in Ubuntus 9.10 and above is:

```
sudo service gdm stop
```

We don't use that ancient /etc/init.d stuff anymore :)

Also note that you'll probably need to blacklist the default Nouveau driver; you can do this by editing /etc/modprobe.d/blacklist.conf and adding the line:

```
blacklist nouveau
```

Then reboot and you'll be able to install the Nvidia driver.

---

### Post by jbrown96 on 2010-05-19
Nvidia drivers are a pain to install manually. The hardware drivers utility has the most current version, so there's no need to go through with it. 

If you really want to do it manually, then expect extreme hardship. Kernel updates will frequently break your graphics. You probably are not killing gdm from a virtual terminal first. Switch to one with Ctrl+Alt+F2, login, then run ```
sudo service gdm stop
```

using ```
sudo service gdm stop
``` is the new way to kill the x-server. ```
sudo /etc/init.d/gdm stop
``` is depreciated but is not causing your problem.

---

### Post by Werner7 on 2010-05-19
Thanks everyone. So you all will recommend i just stay with the proprietary driver provided by the hardware driver utility? "current" one?

---

### Post by jbrown96 on 2010-05-19
> **Werner7 said:**
> Thanks everyone. So you all will recommend i just stay with the proprietary driver provided by the hardware driver utility? "current" one?

Definitely. I'm not sure how much those drivers will be updated over time, but at least for the next 4-5 months they will be the best/easiest.

---

### Post by Werner7 on 2010-05-19
Alright okay. Anyone with an Nvidia driver or perhaps other GPUs experience that moving windows ect, isn't smooth? looks jaggered, specially with the wobbly windows? Is there settings that will make everything smooth? I did set the Nvidia settings to best quality but doesn't make much of a difference i think.

---

### Post by jbrown96 on 2010-05-19
I have a Nividia GPU and have never seen that problem. My guess is that the Nvidia driver is not loaded properly. 

Could you launch nvidia-settings and post the version, along with ```
lspci | grep VGA
``` and ```
lsmod | grep nvidia
```

---

### Post by ryan858 on 2010-05-19
Actually:
```

sudo stop gdm

```works too. And a bit easier to type.

---

### Post by Werner7 on 2010-05-19
> **jbrown96 said:**
> I have a Nividia GPU and have never seen that problem. My guess is that the Nvidia driver is not loaded properly. 

Could you launch nvidia-settings and post the version, along with ```
lspci | grep VGA
``` and ```
lsmod | grep nvidia
```

Yes sir, this is the line as follows for grep VGA;
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)

For the next command;

nvidia              10799466  41 

------------
Now the driver version is 195.36.15
Not sure if you want the other versions as well but here are they;
Server Version Number: 11.0
Server Vendor Version: 1.7.6 (10706000)
NV-CONTROL Version: 1.22.

The graphics isn't bad. But its a clear difference between Windows vista/7 and Ubuntu when moving windows. 

This is the rest of my config. 

HP Laptop,
Centrino 2 P8400 2.26GHz
4GB Ram
9600m GT 512MB.

Thanks for all the help.

---

### Post by jbrown96 on 2010-05-19
> **Werner7 said:**
> Yes sir, this is the line as follows for grep VGA;
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)

For the next command;

nvidia              10799466  41 

------------
Now the driver version is 195.36.15
Not sure if you want the other versions as well but here are they;
Server Version Number: 11.0
Server Vendor Version: 1.7.6 (10706000)
NV-CONTROL Version: 1.22.

The graphics isn't bad. But its a clear difference between Windows vista/7 and Ubuntu when moving windows. 

This is the rest of my config. 

HP Laptop,
Centrino 2 P8400 2.26GHz
4GB Ram
9600m GT 512MB.

Thanks for all the help.

It will never be quite as smooth as Windows, but it shouldn't be that noticeable. You can try disabling Compiz to see if the problem goes away. If so, then you can leave it disable, although probably don't want to. You can install the compiz configuration tool (it's like compiz-config-... or ccsm) and there's lots of performance/rendering settings. I use KDE, so I'm not familiar with the Compiz options, maybe someone else is. 
I don't think there is anything wrong with your driver install; it's more likely that Compiz is causing poor rendering.

---

### Post by Werner7 on 2010-05-22
Yea thanks in anyways for that. How is KDE? I still want to try it, although I'm a bit of an keeping it origanal fan. But is it good? Why do you pick it over Gnome?

---

### Post by jbrown96 on 2010-05-23
I like the applications better. To understand this, you need to understand how linux apps work.

Linux depends heavily on shared libraries. A library is a set of functions/objects that applications use. There are functions to make network connections, draw windows, draw the "save file" dialogs, etc. Some are very basic and some do almost everything for the programmer. For graphical applications on Linux, there are two main libraries (which contain sub-libraries as well): called GTK+ and QT. Gnome uses GTK+ and KDE uses QT. When you load Gnome or KDE at login a lot of the GTK+ or QT libraries are loaded into RAM. This is great because when you launch new application that match your DE (Gnome=GTK+ and KDE=QT) they load faster since some of the code is already in RAM. You can certainly run GTK+ apps in KDE and vice versa, but you typically have to load those libraries at launch time, which causes them to load slower and then have additional libraries in RAM. This leads to the general rule: run GTK+ apps in Gnome and QT apps in KDE. It's not hard and fast, but it helps performance. 

KDE tends to have lots of optimizations, although you have to put time into learning them. PowerDevil, which manages power settings, is a very great app in KDE that allows very fine tuning for laptops. I also really like Plasma and think that it is an the future, although I don't want to say that it's super advanced. 
KDE tends to be far more developmental, meaning that it adds features quickly but tends to lack stability. Gnome tends to be more conservative, although they are re-basing for the 3.0 release in six months. For 10.04 (or really KDE SC 4.4), I think that KDE has reached a good maturity level, so users won't have any problems with it. The only problem that I still have with it is knetworkmanager, but I replace it with network-manager-gnome. 
A Desktop Envrionment is a very personal choice, and it's worth exploring both. I wouldn't recommend installing gnome-desktop in Kubuntu or kde-desktop in Ubuntu because the menus get all messed up and doesn't lead to a good user experience. Give each a shot; you will probably figure out which you like pretty quickly. A word of warning: since Ubuntu is Gnome-based, there's not a lot of help to be found in the forums for KDE-specific questions. The OpenSUSE forums tend to be a better place for KDE problems.

---

### Post by Werner7 on 2010-05-23
Right, you just caused me to want to try out KDE, and I'm going to do that. So many people use it, or enough to tell me to give it a try. I am almost over my internet limit for the week :( so i'll ask my University tutor to download it for me. :P 

Is Kubuntu the same as Ubuntu just with another interface? Or does it operate different with other things instead of just the interface?

---

### Post by jbrown96 on 2010-05-23
> **Werner7 said:**
> Right, you just caused me to want to try out KDE, and I'm going to do that. So many people use it, or enough to tell me to give it a try. I am almost over my internet limit for the week :( so i'll ask my University tutor to download it for me. :P 

Is Kubuntu the same as Ubuntu just with another interface? Or does it operate different with other things instead of just the interface?

It's just the interface, but it's more polished. I definitely recommend trying Kubuntu separately to make your decisions. 
Don't know anything about your university, but at mine we had Internet2, which is a very fast connection to other universities. At your university, make sure to use a .edu mirror and it should download extremely fast.

---

### Post by Werner7 on 2010-05-23
Yea i will try Kubuntu alone. Maybe dual boot it with my Ubuntu machine. 
My university don't have a .edu address :P I'm in new zealand. But its still fast. 
[http://www.speedtest.net/result/752131778.png](http://www.speedtest.net/result/752131778.png) that is using internet at my univeristy from my laptop via Wireless N to another server in cyber space. :P 
Our univeristy has their is like their own ISP. not sure if all univeristies are like that though. If i don't use wireless the upload is the same as download. So I'm not sure why.

---

