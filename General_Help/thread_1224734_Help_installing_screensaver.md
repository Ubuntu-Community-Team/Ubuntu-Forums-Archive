---
title: "Help installing screensaver"
date: 2009-07-27
forum: General Help
---

### Post by ztmike on 2009-07-27
From here: [http://somewhere.fscked.org/proj/fireflies/](http://somewhere.fscked.org/proj/fireflies/)

Trying to install the Deb. file of the screensaver, I get an error while it extracts saying "Error: Wrong architecture "i386" 

Now I'm assuming that's because I'm using 64bit version of Ubuntu? Is there anyway I can install this? On Windows you could install 32bit programs on 64bit.

I also tried installing it on my 32bit Ubuntu machine and got this error: "Error: Dependency is not satisfiable: xlibs (>>4.1.0)

Any help??:confused:

---

### Post by sleepy-time-demon on 2009-07-27
on the 32 bit one, open Terminal and type ```
sudo apt-get install xlibs
``` and go. As for the 64 bit, no clue.

---

### Post by ztmike on 2009-07-27
> **sleepy-time-demon said:**
> on the 32 bit one, open Terminal and type ```
sudo apt-get install xlibs
``` and go. As for the 64 bit, no clue.

I get this error 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibs has no installation candidate

When doing what you said for 32bit machine

---

### Post by ztmike on 2009-07-27
Anyone?

---

### Post by andreylosev on 2011-01-12
BUMP. I would like to install this too and have the same problem.

---

### Post by thakas on 2011-02-19
Hi, I came across this thread while trying to make this work in Ubuntu _10.10 Maverick_, this is how I succeeded:

First of, you'll need a deb of the 2.07 version, the latest source is available from the home page: [http://somewhere.fscked.org/proj/fireflies/files/fireflies-2.07.tar.gz](http://somewhere.fscked.org/proj/fireflies/files/fireflies-2.07.tar.gz) 
but I had to admit defeat when trying to compile it; fortunately poster No_Strings at the [http://www.dslreports.com/forum/remark,22775601](http://www.dslreports.com/forum/remark,22775601) forum was better at it than me,
[U][B]but use this deb at your own risk!
[/B][/U][http://www.dslreports.com/r0/download/1453334~690a2df3d3be0e314668b21cc5d9f485/fireflies_2.07-1_i386.deb.zip]("http://www.dslreports.com/r0/download/1453334%7E690a2df3d3be0e314668b21cc5d9f485/fireflies_2.07-1_i386.deb.zip")

This deb successfully installed  on my 32bit machine and, according to other posts on that forum, it should work on 64bit machines as well.

Now, the problem I then had with this particular deb (or the source code it originated from) is that it placed the screen saver file in the wrong location, and it also did not create a couple of .desktop files ubuntu expected. I did not want to modify a working deb, so I made the screen saver work by executing the following steps in terminal:

first:
```
sudo ln -s /usr/libexec/xscreensaver/fireflies /usr/lib/xscreensaver/fireflies
```then:
```
gksu gedit /usr/share/applications/screensavers/fireflies.desktop &

```and once gedit opens, paste this:
```

[Desktop Entry]
Encoding=UTF-8
Name=Fireflies
Comment=Fireflies Screensaver
TryExec=fireflies
Exec=fireflies -r
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver
```then save the changes and close gedit

repeat with:
```
gksu gedit /usr/share/kde4/services/ScreenSavers/fireflies.desktop &

```but this time paste:
```

[Desktop Entry]
Encoding=UTF-8
Exec=fireflies
Icon=preferences-desktop-screensaver
X-KDE-ServiceTypes=ScreenSaver
X-KDE-Category=OpenGL Screen Savers
X-KDE-Type=OpenGL
Type=Service
Actions=Setup;InWindow;Root
Name=Fireflies (GL)

[Desktop Action Setup]
Exec=kxsconfig fireflies
Name=Setup...

[Desktop Action InWindow]
Exec=kxsrun fireflies -- -window-id %w
Name=Display in specified window
NoDisplay=true
 
[Desktop Action Root]
Exec=kxsrun fireflies -- --root
Name=Display in root window
NoDisplay=true
```again save the changes and close gedit, also close terminal.

It should work now, if not restart and see if this made a difference.

If you ever wish to remove this screen saver, first remove fireflies from synaptic package manager and then execute these commands in terminal:

```

sudo rm /usr/lib/xscreensaver/fireflies

sudo rm /usr/share/applications/screensavers/fireflies.desktop

sudo rm  /usr/share/kde4/services/ScreenSavers/fireflies.desktop


```

---

