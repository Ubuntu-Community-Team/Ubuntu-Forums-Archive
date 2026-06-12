---
title: "Where should downloads go?"
date: 2009-11-21
forum: General Help
---

### Post by BAO_Dave on 2009-11-21
My questions are probably elementary to most users here but I am quite new to Ubuntu 9.10, or any Linux OS for that matter.
 
I have a machine set up that does not have internet access yet, that's an internal modem problem, so I need to download a package 'wvdial' to a USB memory stick and transfer it to the Ubuntu machine but I'm not sure where to put it nor what to do with it once it's on the machine. There's a **Places** > **Home Folder** > **Downloads** that seems like the right place.
 
When I get the package in the correct place how do I install it and will Ubuntu know where the installed files go?
 
Thanks, Linux user - day 2 1/2

---

### Post by scragar on 2009-11-21
If it's a .deb then you should be fine to run it from anywhere, without needing to put it in a special place, if you really do want to though then the apt cache is probably the right place, although without a net connection apt might not be aware that the version you've got exists, meaning it won't see it anyway.
/etc/apt/cache I think.

---

### Post by BAO_Dave on 2009-11-21
Okay that's clear as mud to me ;) but thanks for the reply! Yes it's got a .deb tag, the entire package is called **wvdial_1.60.1+nmu2ubuntu_i386.deb** and I managed to get it copied onto my desktop, it looks like a brown cardboard box with a spiral in the middle. While waiting for a reply I went ahead and tried to double click it and it looked like it was extracting but then I got a message **Error: Dependency is not satisfiable:libuniconf4.6**, and I'm not sure what that means.
 
Go easy on me, I've been stuck with Windoze since 3.1!

---

### Post by SuperSonic4 on 2009-11-21
It means that wvdial needs libuniconf4.6 to run (technically speaking libuniconf is a dependency of wvdial)

This is why it's easier to use a package manager because that solves the dependency issue. 

You can search for a deb of libuniconf but that could well require another package. This is known as dependency hell for obvious reasosn

---

### Post by scragar on 2009-11-21
:p sorry.

That's the problem with downloading the packages manually, you miss dependancies. The easiest solution is probably to take a look at [keryx](http://keryxproject.org/) which offers the ability to sync things up and download all the dependencies you need without worrying about such problems.

---

### Post by BAO_Dave on 2009-11-21
Okay I've seen references to using a package manager, but how do I do that on a machine without internet access? Under **System** > **Administration** > **Synaptic Package Manager** resides and I can start that after entering my password but I can find not find the package I want to install....how do I do that?
 
Thanks!

---

### Post by Greenwidth on 2009-11-21
See post #8 of this thread:
[http://ubuntuforums.org/showthread.php?t=1138101](http://ubuntuforums.org/showthread.php?t=1138101)

There's a zip with the files you need for karmic (9.10)

---

### Post by BAO_Dave on 2009-11-21
Okay I found the **wvdial910.zip** file but the machine running Ubuntu does not have WinZip on it.

---

### Post by Greenwidth on 2009-11-21
Put the zip on the the Ubuntu machine and right click, there should be an option to 'extract here' which will unzip them.

---

### Post by BAO_Dave on 2009-11-21
Okay I put the zip file on my desktop and managed to extract the files. Now I have a new folder which has four more brown cardboard boxes with spirals in the middle and a text document. The latter I opened and followed the instructions double clicking each package in order, having to enter a password for each install is a pain though. After completing all of the installs, none of which gave any error messages, I now assume everything is installed. Now I still have a zip file and a folder on my desktop which I am wondering if I still need? Now I need to figure out how to use wvdial....any tutorials lying around?
 
Thanks for the help!

---

### Post by scragar on 2009-11-21
> **BAO_Dave said:**
> Okay I put the zip file on my desktop and managed to extract the files. Now I have a new folder which has four more brown cardboard boxes with spirals in the middle and a text document. The latter I opened and followed the instructions double clicking each package in order, having to enter a password for each install is a pain though. After completing all of the installs, none of which gave any error messages, I now assume everything is installed. Now I still have a zip file and a folder on my desktop which I am wondering if I still need? Now I need to figure out how to use wvdial....any tutorials lying around?
 
Thanks for the help!

From a command line you can install them all at once:
```
sudo dpkg-install -R ~/Desktop/**FolderNameHere**
```
:p

And if there's no errors then it will be installed, never used that program before, so I've not idea how to use it, google is normally a good guide though.

[http://alumnit.ca/wiki/index.php?page=WvDialFAQ#toc8](http://alumnit.ca/wiki/index.php?page=WvDialFAQ#toc8)

Personally I would look at the [wikipedia page](http://en.wikipedia.org/wiki/Wvdial) and look at the graphical interfaces, rather than struggling to use it on the command line if you don't understand it.

---

### Post by BAO_Dave on 2009-11-21
Well I didn't get your reply before I installed the files one at a time but I think the result was the same, no errors reported. Now is there a way to verify all the files are where they need to be? Also can I trash the zip file and created folder on my desktop or should I file them away some place?
 
Thanks, I'm off to read the [[COLOR=#000000]wikipedia page[/COLOR]]("http://en.wikipedia.org/wiki/Wvdial")!

---

### Post by scragar on 2009-11-21
You can safely delete the folder once they are installed without errors, although I would recommend keeping them incase you ever need them again(say an upgrade breaks support, or you accidentally uninstall the driver using the system cleaner/computer janitor application).

If there was no error it should be installed, just to be sure try running:
```
which wvdial
```
If it responds with a path then it's installed, if it tells you that it's not found then there's an error, really though, if it's installed that shouldn't happen.


EDIT: :p
Suggested graphical front end: [http://packages.ubuntu.com/karmic/gnome-ppp](http://packages.ubuntu.com/karmic/gnome-ppp)

---

### Post by steveneddy on 2009-11-21
Is there anywhere you can take the machine that has an internet connection that you could use until you get all of your updates and downloads done?

---

### Post by BAO_Dave on 2009-11-21
> **steveneddy said:**
> Is there anywhere you can take the machine that has an internet connection that you could use until you get all of your updates and downloads done?
 
Yep, I am in the process of moving the machine to a room with a phone jack. That will bring up other questions for me though like, how do I connect (I see references to using Terminal but I'm totally unfamiliar with it), how do I download and what do I download. This is a brand new build and other than the wvdial package it's just as after the original install.
 
Thanks, I really do appreciate knowledgable people helping out a newbie!

---

### Post by BAO_Dave on 2009-11-21
> **scragar said:**
> You can safely delete the folder once they are installed without errors, although I would recommend keeping them incase you ever need them again(say an upgrade breaks support, or you accidentally uninstall the driver using the system cleaner/computer janitor application).
 
If there was no error it should be installed, just to be sure try running:
```
which wvdial
```
If it responds with a path then it's installed, if it tells you that it's not found then there's an error, really though, if it's installed that shouldn't happen.
 
 
EDIT: :p
Suggested graphical front end: [http://packages.ubuntu.com/karmic/gnome-ppp](http://packages.ubuntu.com/karmic/gnome-ppp)
 
scragar,
 
In reply to your post typing that in a Terminal window returns **/usr/bin/wvdial**, not sure what that means but I'm hopeful!

---

### Post by SuperSonic4 on 2009-11-21
> **BAO_Dave said:**
> scragar,
 
In reply to your post typing that in a Terminal window returns **/usr/bin/wvdial**, not sure what that means but I'm hopeful!

That means it installed

---

### Post by BAO_Dave on 2009-11-21
SuperSonic4,
 
I just noticed that your location just happens to be my last name....interesting!
 
Thanks for the enlightenment! I also just downloaded and installed gnome-ppp and was able to find it under **Applications** > **Internet**. I started the app and got a window asking for Username Password and Phone number into which I plugged my info. Not sure what, if any, changes I should make in the three tabs under **Setup** tab there though but I'm going to give it a try now that I have the machine hooked up to a working phone line.
 
Thanks!

---

### Post by BAO_Dave on 2009-11-21
Well with all, I think, the packages installed along with scragar's suggestion of gnome-ppp I ran that and plugged in my information and clicked **Connect** and got an error message, **Cannot open /dev/modem: No such file or directory**. So I went into the **Setup** area of gnome-ppp and at the **Device: /dev/modem** I asked it to **Detect** and got another error message, **No modem was found on your system**. The latter is not true as Windoze uses the installed Telepath 56K Voice Faxmodem PNP (PCI) all the time to connect to the internet on COM3, Interupt 5, Address 3E8, UART NS 16550AN at up to 115K Baud.
 
[SIZE=1]HELP![/SIZE]

---

### Post by steveneddy on 2009-11-21
This Google search:

[http://www.google.com/search?hl=en&source=hp&q=ubuntu+dial+up&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&source=hp&q=ubuntu+dial+up&aq=f&oq=&aqi=)

revealed this link:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

and this link:

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

either of which should help you get a dial up connection, but you may need an internet connection to install more software.

Like I said before, take it somewhere that has an internet connection already (neighbor's house, library, internet cafe) and get the software that you need in this manner, then take it home and dial up all night long.

One last link:

[http://www.linmodems.org/](http://www.linmodems.org/)

but you are going to have to DL more software before you get to the end of this project.

---

### Post by steveneddy on 2009-11-21
I assume that you are in the US?

---

### Post by BAO_Dave on 2009-11-21
> **steveneddy said:**
> I assume that you are in the US?
 
In the Heartland, southern Illinois.
 
Thanks for the links in your previous post, I have them bookmarked for further reading. And in reference to your other post, you have no idea of what it's like living out in the sticks or rural America! I have better access to the internet than my neighbors and the library!....internet cafe what's that?

---

### Post by EXCiD3 on 2009-11-22
> **BAO_Dave said:**
> In the Heartland, southern Illinois.
 
Thanks for the links in your previous post, I have them bookmarked for further reading. And in reference to your other post, you have no idea of what it's like living out in the sticks or rural America! I have better access to the internet than my neighbors and the library!....internet cafe what's that?

From Illinois too? Cool! I'm from the Springfield area but go to school down in Edwardsville.   

As for an internet cafe, ever been to starbucks or some hometown coffee shop that offers free wifi? That's where I live when I'm home for the summers, most of [Keryx]("http://keryxproject.org") was developed and tested in the local coffee shop.

---

### Post by BAO_Dave on 2009-11-22
Down here in southern Illinois there are mostly farmers and coal miners. I think the nearest Starbucks is almost forty miles from me and I doubt they would appreciate me setting up a desktop on site.
 
This is turning out not to be one of my better ideas, although the idea of ending my contributions to Mr. Gates was appealing. If someone would point me to a tutorial on how to remove Ubuntu that was installed side by side with Windoze, including the partition, I certainly would appreciate it. If I can't get things set up on a test computer I certainly don't want to start messing around with my observatory computers, way too critical for my research.
 
Thanks for attempting to help me though you all.

---

