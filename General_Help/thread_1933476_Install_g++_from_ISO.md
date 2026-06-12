---
title: "Install g++ from ISO"
date: 2012-02-29
forum: General Help
---

### Post by MrBean355 on 2012-02-29
Hello,

I have just started learning C++ at university and we are required to use Ubuntu. I installed Kubuntu on a virtual machine (using Oracle VM VirtualBox). All that I need to do now is to install G++ (compiler). The thing is that I have an ISO of the install files, not an actual disk. How can I install G++ from an ISO?

I have done Google searches for this issue, but nothing has helped so far. I also don't have an internet connection.

Thanks,

**Mr_Bean**

---

### Post by holycow131415 on 2012-02-29
While in kubuntu, the vm has a menu. Go to devices > cd/dvd devices > choose a virtual cd/disk file.
Find iso file, and kubuntu will see it as a regular disk.

---

### Post by QIII on 2012-02-29
g++ is in the Ubuntu repos.  The simplest thing to do would be to add the "build-essential" package from the Software Center.  That will give you a lot of useful things beyond g++.

Edit:  Ah!  Just noticed that you have no internet connection, so disregard.  You can add packages off line.  I'm not at my home computer, or I'd give you a url with instrucions.

---

### Post by drdos2006 on 2012-02-29
Set your VM to be able to read from the CD/DVD/Blu-Ray reader/writer.

[edit]
From your VM... [/edit]
 
Put your ISO disk into the CD/DVD/Blu-Ray reader/writer and open up your ISO. Go to /pool/main/g/gcc-4.4

Doubleclick on the .deb file and install.

regards

---

### Post by MrBean355 on 2012-03-20
Thanks guys! I have now done a full install of Kubuntu 11.10 (no more virtual machine). How would I now install G++ from the ISO?

EDIT: I ran the .deb file that ***drdos2006 ***mentioned and it seemed to install (no error message). But when I type "*g++*" in the Terminal, it still doesn't work.

***Mr_Bean***

---

### Post by SeijiSensei on 2012-03-20
You need to install the **build-essential** package, not just the compiler.

---

### Post by gleedadswell on 2012-03-21
Hey folks.  It sounds like the original poster is new enough to all of this that they don't know how to install a package in the usual ways.

Not having an internet connection could be a problem.  What I'm going to describe below requires one.  Is there somewhere you can temporarily connect your machine?

Once you've got a connection the easiest way is to open a terminal.  Now type

sudo apt-get install build-essential

and hit enter.  It will ask for your password.  When this runs it will download the packages you need from the software repositories.  I suspect the g++ compiler you need isn't on the .iso.  That's why you need to download it like this.  This is the normal way to add software to a linux machine.

If you prefer, there is a graphical user interface package manager called Ubuntu Software Center that allows you to search or browse for packages and install them with a few clicks.  Some of us (me included) prefer the older package manager, Synaptic.  But when you know the name of the package you need it is usually faster to do it from the command line by the method above. 

Have fun with your c++ coding!

---

### Post by MrBean355 on 2012-03-21
> **gleedadswell said:**
> Hey folks.  It sounds like the original poster is new enough to all of this that they don't know how to install a package in the usual ways.

Not having an internet connection could be a problem.  What I'm going to describe below requires one.  Is there somewhere you can temporarily connect your machine?

Once you've got a connection the easiest way is to open a terminal.  Now type

sudo apt-get install build-essential

and hit enter.  It will ask for your password.  When this runs it will download the packages you need from the software repositories.  I suspect the g++ compiler you need isn't on the .iso.  That's why you need to download it like this.  This is the normal way to add software to a linux machine.

If you prefer, there is a graphical user interface package manager called Ubuntu Software Center that allows you to search or browse for packages and install them with a few clicks.  Some of us (me included) prefer the older package manager, Synaptic.  But when you know the name of the package you need it is usually faster to do it from the command line by the method above. 

Have fun with your c++ coding!

Thanks. I do know how to install with sudo apt-get..... the problem is that I don't have an internet connection. So basically I HAVE TO have an internet connection to install it?

> **heldurd said:**
> Go to devices > cd/dvd devices > choose a virtual cd/disk file.

I'm not using a virtual machine anymore, I installed it properly.

---

### Post by westie457 on 2012-03-21
It is possible to install 'build-essential' from the media you you did your kubuntu installation from.

The steps are 

1, Boot your system normally

2, Put your install CD in the tray or plug in your USB stick

3, Open the File-browser (konquerer)

4, In the left pane locate the CD/USB and click on it.

5, Navigate your way to /pool/main/b/build-essential. Double-click the build-essential*.deb file and it should install.


These instructions work in Ubuntu, they should also work in Kubuntu and others.

---

### Post by MrBean355 on 2012-03-21
Thanks westie457. However, the only file in the ***pool\main\b*** is located in ***pool\main\b\b43-fwcutter\b43-fwcutter_014-9_i386.deb***

Hmmm...

---

### Post by SeijiSensei on 2012-03-21
I don't think any compilation tools are packaged on the standard CD.  There's just too little space available to include something that very few people will actually use.  The [DVD versions]("http://cdimage.ubuntu.com/kubuntu/releases/11.10/release/") include a much larger array of packages.

@MrBean
Please don't take this the wrong way, but Ubuntu, like most modern Linux distributions, pretty much assumes you'll have an Internet connection available.  The entire system of software updates relies on being able to connect to the online repositories.  The last time I installed Windows 7, it also used the Internet to download missing drivers and update the software.

If you're affiliated with a university, isn't it possible to connect to the Internet from there?  Did you get the CD from the instructor for your class?  Perhaps you should mention to him/her that the CD doesn't include g++ and other vital packages and suggest they distribute the DVD version instead.

---

### Post by MrBean355 on 2012-03-23
I've downloaded the DVD version and it looks like there are many more packages. Will let you know how it goes.

Thanks!

---

