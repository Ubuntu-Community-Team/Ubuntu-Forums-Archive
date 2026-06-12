---
title: "questions about Linux"
date: 2010-02-11
forum: General Help
---

### Post by hunterkasy on 2010-02-11
Ever since I have started to use Ubuntu on a few machine's, around a year ago, I have been wondering about a few things, like,  with Linux do you have to do any system cleanup like you do with windows? for example I use ccleaner for windows to clean out all temp files and cache and also for cleaning up the registry. does Linux have temp folders, and if they do, do they auto delete their contents after awhile?  and does Linux use a registry system like windows does?  

And finally does a hhd running Linux gets fragmented like a hhd with windows? or does Linux store files in proper order in order to prevent fragmentation

sorry may be stupid questions to a seasoned Linux user, but I am not seasoned yet

---

### Post by audiomick on 2010-02-11
The short answer is "no to all of the above".
There is a good explanation of why a Linux  file system doesn't (usually) need de-fragging here:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)
the tmp files get erased when you shut down, as far as I know.
There is no "registry file" or equivalent that I know of, although others are welcome to correct me if I am wrong.

There is a way of cleaning out "orphaned" packages, but I don't know it off hand.
Here are 2 links that might be relevant
[http://ubuntuforums.org/showthread.php?t=1328596](http://ubuntuforums.org/showthread.php?t=1328596)
[http://ubuntuforums.org/showthread.php?t=1379606](http://ubuntuforums.org/showthread.php?t=1379606)

---

### Post by abhishek.malhotra35 on 2010-02-11
Nice questions. I am able to answer only one. Linux does have a temp directory where it unpacks the softwares before installing it. Its /tmp. I haven't seen a tool that clears this directory automatically. I do it manually.

Waiting for more replies from others.

---

### Post by 2hot6ft2 on 2010-02-11
There is no registry in linux.
There are ways to clean linux see the link in my sig below.
You can also use QuickStart which is real nice but it's not in the repos. [http://www.quickstart.freeforums.org](http://www.quickstart.freeforums.org)
Some other ways are in a terminal
Applications > Accessories > Terminal
you can use:
```
sudo apt-get autoremove
```
or
```
sudo aptitude autoclean
```

---

### Post by 2hot6ft2 on 2010-02-11
> **audiomick said:**
> 
There is a way of cleaning out "orphaned" packages, but I don't know it off hand.
That would be deborphan and the GUI for it is gtkorphan
```
sudo apt-get install deborphan gtkorphan
```

---

### Post by MJBoa on 2010-02-11
There is in fact a registry of sorts in Ubuntu. There is GConf for GNOME preferences. It's more... modular and cleaner, plus a lot smaller so you don't ever have to worry about cleaning it or anything. There are a lot of GNOME settings there though, so it's good to know about.

The package management usually keeps clutter under control, sometimes your Home folder might get a little unkempt though.

As far as I know, ext3/4 (usual linux filesystems) are even less affected by fragmentation than ntfs (the filesystem of windows). So defragmentation is even more useless on linux than it is on windows.

---

### Post by sisco311 on 2010-02-11
> **2hot6ft2 said:**
> That would be deborphan and the GUI for it is gtkorphan
```
sudo apt-get install deborphan gtkorphan
```

computer-janitor-gtk (System -> Administration -> Computer Janitor) is installed by default.

---

### Post by ron999 on 2010-02-11
Hi
There's a program in the repo called BleachBit.
It's the nearest thing to Ccleaner that I've come across for Linux.

---

### Post by 2hot6ft2 on 2010-02-11
> **MJBoa said:**
> There is in fact a registry of sorts in Ubuntu. There is GConf for GNOME preferences. It's more... modular and cleaner, plus a lot smaller so you don't ever have to worry about cleaning it or anything. There are a lot of GNOME settings there though, so it's good to know about.

The package management usually keeps clutter under control, sometimes your Home folder might get a little unkempt though.

As far as I know, ext3/4 (usual linux filesystems) are even less affected by fragmentation than ntfs (the filesystem of windows). So defragmentation is even more useless on linux than it is on windows.
Never thought of gconf-editor as being like a registry, but I guess you're right it is kinda similar in some respects but it's still nothing like a windows registry. You can actually make sense of gconf-editor and easily make changes to the system with it.

If the OP wants to poke around in it just use ALT+F2 and put in ```
gconf-editor
```
or you can put it in a terminal.

---

### Post by 2hot6ft2 on 2010-02-11
> **ron999 said:**
> Hi
There's a program in the repo called BleachBit.
It's the nearest thing to Ccleaner that I've come across for Linux.
Very interesting. That's the first time I heard of BleachBit. May have to give that a try sometime.
> BleachBit deletes unnecessary files to free valuable disk space, maintain
privacy and remove junk. It removes caches, temporary files, cookies and
broken shortcuts.

It handles Bash, Beagle, Epiphany, Firefox, Flash, Java, KDE, OpenOffice.org,
Opera, RealPlayer, rpmbuild, VIM, XChat, and more.


---

### Post by audiomick on 2010-02-11
> **sisco311 said:**
> computer-janitor-gtk (System -> Administration -> Computer Janitor) is installed by default.
Just be a bit careful with the Janitor. Have a look at what it wants to remove before you OK it. I have read of a number of instances of it wanting to remove stuff that was not junk at all.

---

### Post by ssulaco on 2010-02-11
> **hunterkasy said:**
>  with Linux do you have to do any system cleanup like you do with windows? 
Not as much as windows,but yes it does need some maintenance,I would like to add to what 2hot6ft2 posted
```
sudo apt-get clean
```
```
sudo apt-get autoremove (application-name)
```
also open up synaptic (System-> Administration-> Synaptic Package Manager). On the left, click on the Status button. You will see a few options appear on the top left pane. If there is a Not Installed (residual config) option, click on it. This will reveal all the residual config package in the system.Check the box beside the package and select &#8220;Mark for complete removal&#8221;. Click Apply.
I also use Bleachbit,it is an equivalent to crapcleaner,be careful and read documentation on it,you can wipe out your bookmarks if your not careful

---

### Post by 2hot6ft2 on 2010-02-11
> **ssulaco said:**
> Not as much as windows,but yes it does need some maintenance,I would like to add to what 2hot6ft2 posted
```
sudo apt-get clean
```
```
sudo apt-get autoremove application-name
```
also open up synaptic (System-> Administration-> Synaptic Package Manager). On the left, click on the Status button. You will see a few options appear on the top left pane. If there is a Not Installed (residual config) option, click on it. This will reveal all the residual config package in the system.Check the box beside the package and select &#8220;Mark for complete removal&#8221;. Click Apply.
I also use Bleachbit,it is an equivalent to crapcleaner,be careful and read documentation on it,you can wipe out your bookmarks if your not careful
LOL I'm surprised you didn't add
```
sudo aptitude clean
```
;)
Seriously though several of these just do the same thing.

---

### Post by hunterkasy on 2010-02-11
> **ron999 said:**
> Hi
There's a program in the repo called BleachBit.
It's the nearest thing to Ccleaner that I've come across for Linux.


I think I am going to try this program out, sounds like the easiest thing to use

---

### Post by ron999 on 2010-02-11
.

---

### Post by dave collin on 2010-02-12
Hi, I've been running bleachbit for past 6 months or so in Jaunty, it works great - but read the messages and cancel stuff it says is under development, or takes time, or resets custom folders, etc. Simple to use, although you have to run it twice - once as admin., once as normal for full clean.

---

