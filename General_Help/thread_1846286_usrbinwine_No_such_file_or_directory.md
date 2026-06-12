---
title: "/usr/bin/wine: No such file or directory"
date: 2011-09-18
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2011-09-18
Not sure if this has to do with a recent lib32 update but just tried to run a game in wine and in playonlinux and the title of the post is what I get for both (albeit a different path for playonlinux). If I ```
ls -la /usr/bin/wine*
``` I get ```
-rwxr-xr-x 1 root root   9684 2011-08-26 19:02 /usr/bin/wine
lrwxrwxrwx 1 root root      4 2011-08-26 19:01 /usr/bin/wine-auto -> wine
-rwxr-xr-x 1 root root   1582 2011-08-26 19:01 /usr/bin/wineboot
-rwxr-xr-x 1 root root 108120 2011-08-26 19:02 /usr/bin/winebuild
-rwxr-xr-x 1 root root   1582 2011-08-26 19:01 /usr/bin/winecfg
-rwxr-xr-x 1 root root   1582 2011-08-26 19:01 /usr/bin/wineconsole
lrwxrwxrwx 1 root root      7 2011-08-26 19:01 /usr/bin/winecpp -> winegcc
-rwxr-xr-x 1 root root   1582 2011-08-26 19:01 /usr/bin/winedbg
-rwxr-xr-x 1 root root 140928 2011-08-26 19:02 /usr/bin/winedump
-rwxr-xr-x 1 root root   1582 2011-08-26 19:01 /usr/bin/winefile
lrwxrwxrwx 1 root root      7 2011-08-26 19:01 /usr/bin/wineg++ -> winegcc
-rwxr-xr-x 1 root root  34340 2011-08-26 19:02 /usr/bin/winegcc
-rwxr-xr-x 1 root root  89910 2011-08-26 19:01 /usr/bin/winemaker
-rwxr-xr-x 1 root root   1582 2011-08-26 19:01 /usr/bin/winemine
-rwxr-xr-x 1 root root   1582 2011-08-26 19:01 /usr/bin/winepath
-rwxr-xr-x 1 root root  12828 2011-08-26 19:02 /usr/bin/wine-preloader
-rwxr-xr-x 1 root root 391276 2011-08-26 19:02 /usr/bin/wineserver
-rwxr-xr-x 1 root root 493083 2011-04-19 07:05 /usr/bin/winetricks
```  which seems ok. Help?

---

### Post by SavageWolf on 2011-09-18
What version are you using? 11.10 seems to do some weird things with 32 bit...

---

### Post by Sin@Sin-Sacrifice on 2011-09-18
```
sin@Purgatory2:~$ uname -a
Linux Purgatory2 3.0.0-11-generic #18-Ubuntu SMP Tue Sep 13 23:38:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
sin@Purgatory2:~$ aptitude show wine
Package: wine                            
New: yes
State: installed
Automatically installed: no
Version: 1.2.2-0ubuntu7
Priority: optional
Section: universe/otherosfs
Maintainer: Scott Ritchie <scottritchie@ubuntu.com>
Uncompressed Size: 69.6 k
Depends: wine1.2, ia32-libs (>= 1.6), lib32asound2 (> 1.0.14), libc6-i386 (>=
         2.6-1), lib32nss-mdns (>= 0.10-3)
Conflicts: wine
Provided by: wine1.2, wine1.3
Description: Microsoft Windows Compatibility Layer (meta package)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine does
 not require Microsoft Windows, however it can use native system dll files in
 place of its own if they are available. 
 
 This meta-package always depends on the latest version of Wine.
Homepage: http://www.winehq.org/
```

Playonlinux is newest and in my GTASA bottle it's running the latest wine 1.3 and it gives me the same error with a different path. Same for other playonlinux bottles. I have one program running in the default bottle (installed with wine /path/to/exe) but either way it was working 3 days ago and now it's telling me that the binaries don't exist.... even though they do.

---

### Post by SavageWolf on 2011-09-18
I meant what version of Ubuntu, sorry, but I'm assuming you are using 11.10.

Uh, in Synaptic, are there separate packages with ":i386" or the like? If so, try installing wine:i386.

EDIT: I'm assuming you are trying to run the 32 bit wine for some reason.

---

### Post by Sin@Sin-Sacrifice on 2011-09-18
Yes 11.10. Thought the uname -a would clear that up but I guess it doesn't print the Ubuntu version. Anyway... I don't have synaptic and never used it but here are my choices of wines:

```
sin@Purgatory2:~$ apt-cache search wine
libkwineffects1abi2 - library used by effects for the KDE window manager
wine-gecko - Microsoft Windows Compatibility Layer (dummy package)
wine1.0-gecko - Microsoft Windows Compatibility Layer (Web Browser)
wine1.2-gecko - Microsoft Windows Compatibility Layer (Web Browser)
wine1.3-gecko - Microsoft Windows Compatibility Layer (Web Browser)
gnome-colors - set of GNOME icon themes
gnome-exe-thumbnailer - Wine .exe and other executable thumbnailer for Gnome
gnome-wine-icon-theme - red variation of the GNOME-Colors icon theme
libkwineffects1abi2-gles - library used by effects for the KDE window manager - Open GL ES
q4wine - Qt4 GUI for wine (W.I.N.E)
shiki-colors - set of Metacity/GTK-2+ themes
shiki-wine-theme - red variation of the Shiki-Colors theme
tellico - collection manager for books, videos, music
tellico-data - collection manager for books, videos, music [data]
tellico-scripts - collection manager for books, videos, music [scripts]
ttf-symbol-replacement - Free font with the same metrics as Symbol
unmass - Extract game archive files
wine - Microsoft Windows Compatibility Layer (meta package)
wine1.2 - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine1.2-dbg - Microsoft Windows Compatibility Layer (debugging symbols)
wine1.2-dev - Microsoft Windows Compatibility Layer (Development files)
wine1.3 - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine1.3-dbg - Microsoft Windows Compatibility Layer (debugging symbols)
wine1.3-dev - Microsoft Windows Compatibility Layer (Development files)
winefish - LaTeX Editor based on Bluefish
winetricks - Microsoft Windows Compatibility Layer (winetricks)
playonlinux - This program is a front-end for wine.
```

As far as I know the x64 wine is useless because you can't yet run anything in it. I just run what's in the repos unless there's issues.

---

### Post by SavageWolf on 2011-09-18
Try installing "playonlinux:i386", that should install the 32 bit version.

---

### Post by Sin@Sin-Sacrifice on 2011-09-18
There is only a 32 bit version...

---

### Post by quequotion on 2011-10-16
I've just run into this after upgrading to the final release of Oneiric.

Am I interpreting this correctly?

Canonical has finally pushed multi-arch support into a release as default.

Packages can now be installed in their amd64 or i386 versions and no amd64 packages should contain i386 libraries anymore.

So I can install wine1.3, but it does nothing, or I could install wine1.3:i386... which is not compatible with my amd64 system and thus requires the removal of several packages, like **xorg**.

Can I have a better option?

I thought the point was to have two architectures running together, not against each other. Aren't we supposed to be moving on to 64bit and emulating 32bit as a legacy mode someday?

---

### Post by quequotion on 2011-10-17
I was not interpreting this correctly.

In fact, [there was a bug in ia32-libs]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all").

Personally, I've been having trouble getting dpkg to understand dependency chains since upgrading so it could be that dpkg failed to notice it needs ia32-libs-multiarch. The other possibility is that the dependencies haven't been properly implemented in the wine or ia32-libs packages.

Anyway, the solution is:
```
sudo apt-get install ia32-libs-multiarch:i386
```

I have a feeling this is going to get messy down the line. As it stands, i now have two 32bit libc6 packages which apparently don't conflict with each other....

---

### Post by razorxpress on 2011-10-22
sudo apt-get install --reinstall libc6-i386

does the job

Source: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

If you have generic opengl library(mesa) and finding hard to start wine applications, you can link /usr/lib32/libGL.so to /usr/lib/libGL.so.1

sudo ln -s /usr/lib32/libGL.so /usr/lib/libGL.so.1

---

### Post by matiche on 2013-01-10
did the command apt-get install --reinstall libc6-i386 and got this mind you i was sudo su already any idea what i may be doing rong i am useing 11.04 the newer version i could use because it aprently doesn't know how to handle wireless drivers for ndiswrapper modles and there isn't any thing you can do about it atm and yes useing 32bit

/home/matiche# apt-get install --reinstall libc6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libc6

E: Package 'libc6-i386' has no installation candidate

---

### Post by overdrank on 2013-01-10
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

