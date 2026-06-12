---
title: "file system"
date: 2006-04-23
forum: General Help
---

### Post by icedragon2002002 on 2006-04-23
can some one explain how linux uses its files and what files contain what

---

### Post by Jason_25 on 2006-04-23
[Here]("https://wiki.ubuntu.com/LinuxFilesystemTreeOverview?highlight=%28filesystem%29") ya go.

---

### Post by woedend on 2006-04-23
can you explain a little further in detail what you are looking for?

---

### Post by icedragon2002002 on 2006-04-23
a basic all over converson from windows to linux

---

### Post by icedragon2002002 on 2006-04-23
a basic all over converson from windows to linux

---

### Post by woedend on 2006-04-23
eek, thats a tall order, but i'll try to get started.  First realize, they are very different!
Normally, when installing packages, you will not have the equivalent of a Program Files type folder, they are separated.  Executable files(binaries, similar to exe's in windows) all go into /usr/bin  or /usr/sbin normally
libraries normally go into /usr/lib

there is no c:\, instead just /
any documents you save, songs, pictures, etc, use your home folder.  the path to your home folder is
/home/yourusername/

nautilus is your file browser instead of explorer, they look similar in a lot of ways.  It will open in your home folder, so if you wish to create subfolders, do so in your home directory, which will make the path
/home/yourusername/subfolder/

you have to have root permission(sudo) to access the other folders.  It's a good idea, when starting out, to leave them alone, however, unless absolutely necessary.

Your cdrom wont be d:\, instead it actually uses a pointer to the device.  so to access a cdrom, its normally something like /dev/cdrom     or /dev/hdc  (it depends).  These should be automounted though, and appear in nautilus on the left when you put a disk in.

---

### Post by icedragon2002002 on 2006-04-23
so there is no test folder and when you install something it installs in many different folders to be used later. 

where are the short cuts and quck launch icons?

---

### Post by woedend on 2006-04-23
shortcuts i wasn't too familar with...its been a while.  quick launch is equivalent to 'launchers'.  Basically, you have two choices.  The easiest is, whenever you install something that has an interface(as you call them in windows, programs :p), it will add itself to your menu's, normally under applications.  When you want to put it to make a launcher, right click on any item on your menu, and click add launcher to panel.  The panels are similar to you taskbar, except you have two.  They are very customizable and I use only  1 similar to windows style, play around with them.  If you want to make a shortcut to something on the desktop, instead of clicking add launcher to panel, click add launcher to desktop.  
As far as installing things, you almost always if possible want to use .deb files. You can now double click them to install, without all the annoying setup questions windows has. The benefit is one stop uninstalling/reinstalling any program you have ever installed.  It's called synaptic.  Think of it like add/remove programs, except theres a huge amount of things to install, its much easier, and everything is free.

---

### Post by icedragon2002002 on 2006-04-23
ok good im making progress
ive installed wine and then i went out to try a windows program so i tried to install winamp which i sucessfully did the thing is that it couldnt find the audio drivers which is no loss because im using an old pos which i didnt expect everything to work. i have no clue where it installed winamp and how to get it back up again i alos tried to install a hoyle card game from a cd but it dosent seem to want to run it says that it installed but it wont run.

oh and sorry for the runon's and the bad spelling.

---

### Post by Jason_25 on 2006-04-23
.

---

### Post by woedend on 2006-04-23
wine works with some programs, not all.  installing winamp with wine isn't really intelligent..there are plenty of great alternative for linux.  XMMS is a LOT like winamp, even in looks, it's my favorite.  For now i'd stick to getting used to using synaptic to install programs, theres an unbelievable amount of them, once you warm up a bit try wine-ing things that don't have a viable alternative.  And does your hoyle CD specifically mention linux compatible?  Most install cd's are not and will not work.

---

### Post by icedragon2002002 on 2006-04-23
so im guessing you have no clue

---

### Post by icedragon2002002 on 2006-04-23
ignore that last post

and no it isint for linux i was trying to use wine again.
my hole purpose of trying out linux it to see if i can play some if not all my origional games that i played on windows which consist of call of duty all of those and halo for pc

---

