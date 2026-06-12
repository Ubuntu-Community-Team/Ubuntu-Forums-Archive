---
title: "Boots fine, but won't load Plasma Workspace"
date: 2009-08-09
forum: General Help
---

### Post by a3uge on 2009-08-09
I'm getting a bit frustrated. I spent all day trying to get Kubuntu to boot, because it decided to remove everything after I tried to remove a single package. So I reinstalled Kubuntu with in a partition, copied all my files from the old partition to the new one, upgraded, and have yet to remove the old partition. So I'm furious that amarok still is 2.0, and not 2.1 in Jaunty and Kubuntu doesn't upgrade to 4.3 TILL THE END OF OCTOBER, so I installed the Jaunty backports to get the new version of amarok.

So this morning I go to boot the freshly installed Kubuntu and log in and I get greeted with:
```

A Fatal Error Occurred

The application Plasma Workspace (plasma) crashed and caused the signal 11 (SIGSEGV)

```

	This was complete with a bug report:

```


This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

(no debugging symbols found)
0x00007ff854623cf0 in nanosleep () from /lib/libc.so.6
[Current thread is 0 (process 3297)]
Thread 1 (Thread 0x7ff85814e750 (LWP 3297)):
#0 0x00007ff854623cf0 in nanosleep () from /lib/libc.so.6
#1 0x00007ff854623b47 in sleep () from /lib/libc.so.6
#2 0x00007ff8563b15af in ?? () from /usr/lib/libkdeui.so.5
#3 0x00007ff8563b1eba in KCrash::defaultCrashHandler () from /usr/lib/libkdeui.so.5
#4 <signal handler called>
#5 0x00007ff83b480f60 in ?? () from /usr/lib/libsolidcontrol.so.4
#6 0x00007ff83b48966d in ?? () from /usr/lib/libsolidcontrol.so.4
#7 0x00007ff83b483826 in ?? () from /usr/lib/libsolidcontrol.so.4
#8 0x00007ff83b483dc4 in ?? () from /usr/lib/libsolidcontrol.so.4
#9 0x00007ff83b483f4c in ?? () from /usr/lib/libsolidcontrol.so.4
#10 0x00007ff83b483fdc in Solid::Control::NetworkManager::networkInterfaces () from /usr/lib/libsolidcontrol.so.4
#11 0x00007ff8398bccc9 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#12 0x00007ff8398beb04 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#13 0x00007ff8398c2967 in KPluginFactory::createInstance<NetworkManagerApplet, QObject> () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#14 0x00007ff85789ac9d in KPluginFactory::create () from /usr/lib/libkdecore.so.5
#15 0x00007ff84f59bff6 in Plasma::Applet::load () from /usr/lib/libplasma.so.3
#16 0x00007ff84f5aa9f0 in ?? () from /usr/lib/libplasma.so.3
#17 0x00007ff84f5ad929 in Plasma::Containment::restoreContents () from /usr/lib/libplasma.so.3
#18 0x00007ff84f5afe73 in Plasma::Containment::restore () from /usr/lib/libplasma.so.3
#19 0x00007ff84f5b3099 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.3
#20 0x00007ff84f5b4ba2 in Plasma::Corona::initializeLayout () from /usr/lib/libplasma.so.3
#21 0x00007ff84bbc99e7 in ?? () from /usr/lib/libkdeinit4_plasma.so
#22 0x00007ff84bbc9ff5 in ?? () from /usr/lib/libkdeinit4_plasma.so
#23 0x00007ff84bbcd048 in ?? () from /usr/lib/libkdeinit4_plasma.so
#24 0x00007ff857c82ea2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#25 0x00007ff857c8814f in ?? () from /usr/lib/libQtCore.so.4
#26 0x00007ff857c7d263 in QObject::event () from /usr/lib/libQtCore.so.4
#27 0x00007ff855238f4d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#28 0x00007ff85524118a in QApplication::notify () from /usr/lib/libQtGui.so.4
#29 0x00007ff85634b71b in KApplication::notify () from /usr/lib/libkdeui.so.5
#30 0x00007ff857c6d6ac in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#31 0x00007ff857c9a516 in ?? () from /usr/lib/libQtCore.so.4
#32 0x00007ff857c96b2d in ?? () from /usr/lib/libQtCore.so.4
#33 0x00007ff853ccc20a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#34 0x00007ff853ccf8e0 in ?? () from /usr/lib/libglib-2.0.so.0
#35 0x00007ff853ccfa7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#36 0x00007ff857c96a8f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#37 0x00007ff8552d1bdf in ?? () from /usr/lib/libQtGui.so.4
#38 0x00007ff857c6bf42 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#39 0x00007ff857c6c314 in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#40 0x00007ff857c6e5e4 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#41 0x00007ff84bbb79bb in kdemain () from /usr/lib/libkdeinit4_plasma.so
#42 0x0000000000407215 in _start ()
#0 0x00007ff854623cf0 in nanosleep () from /lib/libc.so.6


```

So essentially I have no desktop, no windows, but apparently Konqueror will open, but with no title-bar. Any help is greatly appreciated, as I don't want to create a third partition and reinstall Kubuntu for the second time in two days.

---

### Post by Zorael on 2009-08-09
Upgraded halfway, perhaps?

Can you open up a terminal (alt+f2: 'konsole', or somehow via konqueror)? Omit the dollarsigns.
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```
If the second command says dependencies are broken and it start giving suggestions on solutions, paste them here.

This should get you your titlebars, or at least an error message why not.
```
$ kwin --replace &
```
Likewise, you can try running plasma-desktop manually, still from the terminal.
```
$ plasma-desktop
```
And if you suspect your plasma settings files may just be botched up, this'll move those out of the way. (If it's a fresh install I don't see why they would be, but still.)
```
$ kquitapp plasma-desktop       # this may/will spawn an error message, ignore that
$ mkdir ~/plasmabackup
$ mv ~/.kde/share/config/plasma* ~/plasmabackup
$ plasma-desktop
```

---

### Post by a3uge on 2009-08-09
Well the first thing I thought of was to do a "sudo apt-get update... sudo apt-get upgrade". Guess I didn't notice that 66 packages were kept back. Among those were plasma-desktop. Go figure. So a sudo apt-get dist-upgrade (which is the same as 'full-update'? I figure I'd try a dist-upgrade first).

So I re-boot up and ........ BAM what's up KDE 4.3.

Guess it got confused when I tried to update Amarok and added the backports. I guess it tried to switch to KDE 4.3, but was content with blocking packages. Really wish Kubuntu would just get their #@$% together and upgrade to 4.3 like every other distro.

Thanks for the help! Hope Kubuntu won't break on me for awhile.

---

### Post by cmost on 2009-08-09
Unfortunately, Kubuntu has a well deserved reputation for being unpolished and sub-par in quality compared to its bigger sibling Ubuntu.  Think of it as Jan Brady to Ubuntu's Marsha.  I hate to do this but you will probably have much better luck with KDE 4.3 by utilizing a distribution that actually pays some attention to its KDE variant like Fedora or OpenSUSE.

---

### Post by a3uge on 2009-08-09
> **cmost said:**
> Unfortunately, Kubuntu has a well deserved reputation for being unpolished and sub-par in quality compared to its bigger sibling Ubuntu.  Think of it as Jan Brady to Ubuntu's Marsha.  I hate to do this but you will probably have much better luck with KDE 4.3 by utilizing a distribution that actually pays some attention to its KDE variant like Fedora or OpenSUSE.

I've been using Kubuntu for almost 3 years now. I hated OpenSUSE back then, required FOUR DISKS for an install. That's completely ridiculous. Hardware support seemed much worse.

I don't know why Kubuntu gets shoved on the back-burner. It's so much more versatile than Gnome. I can't stand Gnome. That's my opinion. But I love the Ubuntu project. If I switch to anything it'll be Mint. I'll stick to Kubuntu for now, seems to be more support for when I tinker too much anyways. Just wish Kubuntu wouldn't wait till THE END OF OCTOBER to update the window manager it bases off of. That's just sounds inane to me.

---

