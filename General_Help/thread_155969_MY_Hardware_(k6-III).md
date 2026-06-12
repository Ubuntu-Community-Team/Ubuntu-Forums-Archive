---
title: "MY Hardware (k6-III)"
date: 2006-04-06
forum: General Help
---

### Post by racoq on 2006-04-06
Hello Guys

I'm a new user of ubuntu.

Someone have managed to provide me with an desktop PC with these specifications

AMD K6 -III 450 MHZ
128 MB SDRAM MEmory
S3 Savage 32 MB
20GB Hard Disk
100MB PCI network adapter

What i ask, is if it is possible to run this machine on UBuntu (Breezy Badger 5.10), using the default graphical desktop (Gnome), more or less smoothly.

If it is not possible i was thinking on upgrading that PC's 128 MB SDRAM to 256. Will this work? Or whatever i part of the hardware that i upgrade, won't be enough to run gnome?

Thanks, and please reply

---

### Post by DanielFaulknor on 2006-04-06
I used to run Ubuntu Breezy on a 500mhz machine with 64MB of ram so yours should run.... though it may be a bit slow.

---

### Post by tribaal on 2006-04-06
While adding some more RAM will definately make it run smoother, I believe your config is more than enough to run Ubuntu nicely.

I run it on a K6-III 400Mhz, with 128Mb RAM without a hintch.

:KS

---

### Post by racoq on 2006-04-06
What hardware requirements the gnome version of Ubuntu demands? More ram memory than Graphic card's memory or vice-versa? Thanks!

---

### Post by tseliot on 2006-04-06
[QUOTE=racoq]What hardware requirements the gnome version of Ubuntu demands? More ram memory than Graphic card's memory or vice-versa? Thanks![/QUOTE]
[Here]("http://www.ubuntu.com/download/releasenotes/510#head-0d4a97955157354809eda56a6c9e28f6c5a26b21") it says:

```
Table 1 Recommended Minimum Requirements 

Install Type

                 RAM               Hard Drive Space

Desktop  128 megabytes     2 gigabytes

Server    64 megabytes       500 megabytes
```


If you have 128mb of RAM you can install Xubuntu after Ubuntu is installed (sudo apt-get install xubuntu-desktop) which should perform better.

I think your graphic card will work.

---

### Post by Miguel on 2006-04-06
racoq,

don't worry about the graphics card. You will only take profit from the graphics card if you run at very high resolutions, when running the 3d screensavers and when using non-default things such as composite or Xgl. On the other hand, more ram will always be welcome. 256mb's will make your experience much better.

Ah!, note that if you have 128mb, you will have (after some time) 128mb used. If you have 256, it will use all 256. And the same story goes for 512mb. Thus, the SO takes full profit from all your ram.

---

### Post by racoq on 2006-04-06
for instaling xubuntu, i will have to install ubuntu Breezy Badger, in the server mode, and install only the minimal services that i need. And after that installing xubuntu in command line! So the Desktop environment will run ok. 

Is that Right?

---

### Post by tseliot on 2006-04-06
[QUOTE=racoq]for instaling xubuntu, i will have to install ubuntu Breezy Badger, in the server mode, and install only the minimal services that i need. And after that installing xubuntu in command line! So the Desktop environment will run ok. 

Is that Right?[/QUOTE]
You can either install Ubuntu using the default installation. Then (after the installation is completed) you can use the command I posted. In this way you will be able to choose between GNOME (Ubuntu's default Desktop environment) and XFCE (Xubuntu's default Desktop environment) from the login manager.

OR

You can do it from a server installation and then you have to type the command I posted before from the command line.

If you use the 1st method you will have lots of applications you might not need but you will be able to use Automatix without installing additional libraries.

In other words you can do as you like ;) .

---

