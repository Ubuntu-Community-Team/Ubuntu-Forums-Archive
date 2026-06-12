---
title: "Replacing Thunar with Nautilus not sticking?"
date: 2011-09-30
forum: General Help
---

### Post by AdamShumpisxXx on 2011-09-30
I'm running Xubuntu 11.04 and I'm having issues with Thunar. Whenever I navigate to my FTP share on the local server or my SMB share on the local printer everything works fine. When I go to drag the folders onto the bar on the bottom left to bookmark them that works as well. The problem is that whenever I restart or shutdown my computer the bookmarks dissapear by the time I get back into it. I always had a positive experience with Nautilus so I installed that from the terminal. It was only about 5.5MBs when it was all downloaded and installed. I went to Applications Menu - Settings - Settings Manager - Preferred Applications - Utilities - File Manager and then I chose Nautilus to be the default. Unfortunately, whenever I open a folder it still comes up in Thunar. I even restarted the computer and went back into the Settings Manager to double check that the default File Manager was still set to Nautilus. It was but everything still uses Thunar. How do I get it to fully switch over? Also, if possible, I would like to add a Places button next to Applications Menu or wherever it has to go. I liked having the "Connect to Server..." option. This is a secondary concern however but I would like to solve both if possible. Thank you very much in advance for your help!

---

### Post by Morbius1 on 2011-09-30
You need to be very careful with using Nautilus in XFCE since it can affect the desktop itself.

What I did was the following:

Edit the application launcher as root:
```
gksu mousepad /usr/share/applications/nautilus-browser.desktop
```And change one line from this:
> [Desktop Entry]
Name=File Browser
Comment=Browse the file system with the file manager
TryExec=nautilus
Exec=nautilus --no-desktop --browser %U
Icon=system-file-manager
Terminal=false
StartupNotify=true
Type=Application
NoDisplay=false
Categories=System
**[COLOR=Blue]OnlyShowIn=GNOME;[/COLOR]**
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.32.2.1
X-Ubuntu-Gettext-Domain=nautilus
To this:
> [Desktop Entry] 
Name=File Browser 
Comment=Browse the file system with the file manager 
TryExec=nautilus 
Exec=nautilus --no-desktop --browser %U 
Icon=system-file-manager 
Terminal=false 
StartupNotify=true 
Type=Application 
NoDisplay=false 
Categories=System 
[COLOR=Blue]**OnlyShowIn=XFCE; **[/COLOR]
X-GNOME-Bugzilla-Bugzilla=GNOME 
X-GNOME-Bugzilla-Product=nautilus 
X-GNOME-Bugzilla-Component=general 
X-GNOME-Bugzilla-Version=2.32.2.1 
X-Ubuntu-Gettext-Domain=nautilus It's the "--no-desktop" part of the exec that prevents damage to things in xfce.

It should now show up in the Menu under > System > [COLOR=Blue]File Browser[/COLOR] as opposed to Accessories > [COLOR=Blue]File Manager[/COLOR] for Thunar.

---

### Post by AdamShumpisxXx on 2011-09-30
Unfortunately what you suggested had no effect what-so-ever. There is no entry for Nautilus or File Manager in Applications Menu - System. Also, Thunar is still in charge. Is there a way to completely remove Thunar and force Nautilus safely? Thanks again.

---

### Post by Morbius1 on 2011-09-30
I do not know how to replace Thunar with Nautilus other thn what you've done in the settings manager. Until someone comes by that does open Thunar and right click:
```
/usr/share/applications/File Browser
```And select: Send To > Desktop

That will be the safe Nautilus.

---

### Post by yetiman64 on 2011-09-30
AdamShumpisxXx, check out [[COLOR=Blue]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4490813#post4490813"), it is old (from 2008, note and read the green banner at the top of the browser window) it seems lke an idea that may work. It works by repointing the symlink for the thunar binary to a script calling on nautilus, so when the system calls for thunar, nautilus is launched. Another OP on a [[COLOR=Blue]different thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6808006&postcount=6") on the topic points to it as as a solution to his/her similar situation

Please note the case of the letter "t" in thunar carefully as /usr/bin/Thunar is the actual binary and /usr/bin/thunar is the symlink pointing to the binary, removing the wrong one could get messy.

I will be trying it out here as soon as I get the time as I'm on Xubuntu as well and have been on the lookout for it.

Hope it works for you.

Edit: note you will still be able to launch Thunar by directly calling on /usr/bin/Thunar and not the symlink /usr/bin/thunar.

---

### Post by AdamShumpisxXx on 2011-10-03
That also did nothing. These two commands:

```
chmod +x /usr/local/bin/myfm
```
```
ln -s /usr/local/bin/myfm /usr/bin/thunar
```

...would not run unless "sudo" was placed before them. could that be the issue? Either way, whenever I open the File System icon or my Home icon it still opens in Thunar. Running this:

```
/usr/bin/thunar
```

...in a terminal opens Nautilus, however. What is going on? It should not be this hard to change. Thanks for your help so far.

---

### Post by yetiman64 on 2011-10-03
Yes those commands will need sudo, I didn't notice that code missing myself on finding those threads. Running a command against anything outside your home folder (in root's ownership) will require the use of sudo (elevated privileges).

> Either way, whenever I open the File System icon or my Home icon it still opens in ThunarOne more suggestion is to look in "(right click the desktop) > Applications > Settings > Settings Manager > Preferred Applications > Utilities > File Manager > other", and set a entry that is pointing to /usr/bin/thunar (whidh in turn points to your script). The current thunar entry here may be pointing directly to the binary and bypassing your script (though I'm _not _100% certain of this, it may be of some help).

Please note I still haven't got to testing this myself and will be at least a few days till I do, but I will attempt it asap and get back here if I have any luck or find any discrepancies etc.

---

### Post by AdamShumpisxXx on 2011-10-04
Thanks for the suggestion but absolutely nothing came of it. There is a new peice of information though...I plugged a USB flash drive into my computer for the first time on Xubuntu and both Thunar AND Nautilus popped up and displayed it's contents.

Another unrelated matter that's bothering me depends on the answer to this question:

Is my current Desktop managed by Thunar?

I think it may be. I'll elaborate. The entire reason why I need Nautilus is because Thunar absolutely refuses to remember my network locations in it's left sidebar and also refuses to allow unmounting them to prevent time-outs. I have one network share from my printer's internal storage for scans and I have an FTP network share I prefer to interface by using Nautilus through a folder shortcut. Something is happening in Nautilus to where I cannot drag and drop to copy a file or folder from my FTP network share to my Desktop. I have to right-click the item, select "Copy To" and choose Desktop. I can however drag and drop from the Desktop to my FTP network share no problem.

Here's where I'm at...Is there any way to COMPLETELY remove Thunar and all of it's traces and force Xubuntu to use Nautilus? I absolutely HATE Thunar and to me and my needs it's 90% useless.

Thank you for the help so far. I hope someone can help.

---

### Post by AdamShumpisxXx on 2011-10-06
Still no development. Should I just "sudo apt-get remove thunar" and see what happens? Hopefully this bump will garner a response...

---

### Post by yetiman64 on 2011-10-06
> **AdamShumpisxXx said:**
> Still no development. Should I just "sudo apt-get remove thunar" and see what happens? Hopefully this bump will garner a response...
Just pay careful note if anything else gets taken out with Thunar. IIRC a bunch of programming may also be removed from xfce it Thunar is removed.

---

### Post by AdamShumpisxXx on 2011-10-06
I'm aware. I wasn't being completely serious. I was just looking for a reason to bump the thread hoping for someone who could help me. This is VERY frustrating. I hate Thunar...

---

### Post by AdamShumpisxXx on 2011-10-06
Also, here are the additional programs that would be removed along with Thunar:

```
USER@COMPUTER:~$ sudo apt-get remove thunar
[sudo] password for USER: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  thunar thunar-archive-plugin thunar-media-tags-plugin thunar-volman
  xubuntu-desktop
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 2,666 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

I'm cool with everything but "xubuntu-desktop" obviously. LAME!

---

### Post by AdamShumpisxXx on 2011-10-11
BUMP! It's been 4 days. I really need help still if someone is able. Thank you!

---

### Post by AdamShumpisxXx on 2011-10-12
Bump!!!

---

### Post by AdamShumpisxXx on 2011-10-13
Abandoned by OP. NOT SOLVED! Good luck to those who come across this in search of an answer for a similar situation.

Long story short? Stay away from Thunar at all costs.

---

### Post by crdlb on 2011-10-13
xubuntu-desktop is just a metapackage; it shouldn't hurt anything to uninstall it. You may need to install it before performing an upgrade, though.

---

### Post by Bezgo on 2011-10-31
Hello, I have been playing with a lot of distributions and have found im very fond of xfce and Xubuntu.
Honestly I've had no issues with thunar until I realised that it has no network places (I have no idea how I made it this far and failed to notice that thunar doesnt have network places)......now onto the interesting part...


I am working in VirtualBox with a fresh install of xubuntu for this very purpose also updated. I tried removing thunar and adding nautilus with not so great results unless I make a custom launcher with the command "nautilus --no-desktop". I then reverted to the snapshot I had taken of a fresh & up-to-date install. I then left thunar alone and installed nautilus and started playing arround, it seems that thunar can use part of nautilus to get to network places. To get it to do this (tested twice to verify before writing this)...... leave thunar alone and install nautilus (using the one in package manager called just "nautilus" Version 1:3.2.1-0Ubuntu1. When thats done go to preferred applications and change it to nautilus, log out and back in then change it back to thunar and logout/in once more ... you will then notice that when you open a folder is uses thunar but has a network button in the side panel.:D

ps. I still have much to learn and I do not know why this works but I assume it has something to do with the other packages that get installed with nautilus, maybe there is way to just install the one that adds the network feature.

Also, what else do you not like about thunar? Maybe there is more I wont like but have not come across yet.

Cheers
Signed Bezgo

---

### Post by Morbius1 on 2011-10-31
"Network" in Thunar depends on a package - **gvfs-backends** - which for most people doesn't install by default for reasons unknown.

The reason adding nautilus fixed it in thunar is that nautilus also has gfvs-backends as a dependency but this time it installed.

---

### Post by Bezgo on 2011-10-31
Thankyou Morbius1, after installing that package GVFS-Backends I simply logged out/in and thunar now has network capabilities. No need to install nautilus.

EDIT-
I would like to report this so that newcomers do not have this as an issue but I'm unaware if it needs to be a suggestion or a bug report, do I go to Thunar, Xubuntu, or both?

---

### Post by Morbius1 on 2011-11-01
Fresh install of Xubuntu 11.10 misses gvfs-backends package: [https://bugs.launchpad.net/ubuntu/oneiric/+source/xubuntu-meta/+bug/878682](https://bugs.launchpad.net/ubuntu/oneiric/+source/xubuntu-meta/+bug/878682)

---

