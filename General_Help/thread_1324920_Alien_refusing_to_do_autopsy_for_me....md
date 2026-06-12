---
title: "Alien refusing to do autopsy for me..."
date: 2009-11-13
forum: General Help
---

### Post by Gunnder on 2009-11-13
Ok, I am trying to install Staroffice, I get it all the way to the SO graphical installer then all files fail to load with the error that I need to install with Alien.

I already have Alien 8.78 installed.  Also have RPM 4.7.0-9 installed.

I would really like to learn how to make this work.  I have spent countless hours these last two weeks trying to figure this out, searching on the web etc.  It seams that Alien is not kicking in to convert the RPM files or I am failing to do that prior to SO's install starting.

1.  What do I need to do to make this work?  

2.  Where can I learn (ie book, manual, web, etc) on how to use Linux's command line (Ubuntu)?  I can do anything with XP but hate it to death.  I want to learn how to use this awesome new tool as quickly as possible!  Can someone point me in some directions?  I know using it is one of the fastest ways to learn, but I need some ground rules!

---

### Post by mick55 on 2009-11-13
Hi 

To install an .rpm file, you first need to convert it to a .deb file
which can be installed on Ubuntu.
I assume that you downloaded the package to your Desktop (~/Desktop is the directory)
You can convert the .rpm to a .deb by using the following commands.
```
cd ~/Desktop
```-This will change the directory to your desktop, where you have the .rpm file.

```
sudo alien -k name-of-rpm-file.rpm
```- This will convert the .rpm to a .deb.
- The “-k” will keep the version number. Otherwise alien adds a “1&#8243; to the version number.

```
sudo dpkg -i name-of-deb-file.deb
```- This will install the .deb package

Your post was short on details so i am providing a
fairly generic solution.
Hopefully it will work for you.

Good luck
mick

---

