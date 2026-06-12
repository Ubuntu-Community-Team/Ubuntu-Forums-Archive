---
title: "Ubuntu seems sluggish."
date: 2011-03-22
forum: General Help
---

### Post by Objekt on 2011-03-22
I can't quantify the behavior, but every time I run Ubuntu 10.04 LTS (32-bit), I get the impression that I'm using a much slower machine.

All I have to compare it to is my Windows 7 64-bit install on the same machine (specs in signature), where almost everything is very snappy by comparison.

I don't have skipping audio or delayed video when watching DVDs in VLC Media Player, and Urban Terror (a 3D game) runs fine, but just general stuff like browsing the filesystem (Nautilus) and Firefox seems reaaaaallly sluggish compared to the Windows 7 counterparts.

What I'm doing at the time does not appear to affect the sluggishness.  I have noticed the same impression of sloth both while copying large files, and while doing nothing in particular.

That's not how it's supposed to work, is it?  Does an Ubuntu install normally slow down over time?  I have only been running 10.04 LTS since last October or so.

---

### Post by lithopsian on 2011-03-22
Simple window actions in Linux can seem sluggish compared to Windows.  This is a consequence of windowing being a native part of Windows but something operated by an application (X server) in Linux.  Believe me, it used to be really clunky back when machines were less powerful.  Note that the applications themselves will run just as well or better but it can seem like everything is slow if it takes a window 2 seconds to open instead of 1.

Some other applications I also find can be slow when your CPU isn't quite up to the task.  Some of the file managers can be just awful when there are lots of files in a directory.  If this affects you, try a different file manager.  Thunar seems to be one of the best if you have a low-end CPU.

There are other factors that can affect your performance.  If your disk is fairly full, the common Linux filesystems will degrade.  In general performance doesn't degrade as badly as old Windows installations do with thousands of useless dlls getting loaded, but they can get cluttered especially if you don't uninstall major services that you don't need any more.

---

### Post by Objekt on 2011-03-22
That's another thing I noticed wit Nautilus: if a directory contains hundreds of files, it takes a while to show them.

---

### Post by cookiecloud on 2011-03-22
> **Objekt said:**
> That's another thing I noticed wit Nautilus: if a directory contains hundreds of files, it takes a while to show them.

It's "indexing" them, and creating a thumbnail cache. Don't sweat it, all will come right :)

CC

---

### Post by s-p-n on 2011-03-22
Huh, would've never guessed Ubuntu would ever be "slower" or more sluggish than Windows Vista and up... Those things are pretty heavy :/ 

KDE comes off as sluggish to me (compared to gnome- it still beats Windows Vista by far), but gnome is pretty good. If you REALLY want a speedy system, I'd choose LXDE instead of gnome..
```

sudo apt-get install lxde

```Then just log out, click your account, click the drop-down by "Sessions:" at the bottom, choose "LXDE" and you should have LXDE with OpenBox WM on your Ubuntu machine... Which is REALLY fast... Like Windows XP/Puppy/Damn Small Linux, out-of-the-box fast.

Never had a problem with it on my server, but it doesn't have any eye-candy.. really. People say it "looks nice" but I respectfully say, I don't think it looks "nice", but it doesn't look bad. Gnome, KDE, and Windows Aero look nice, to me. Windows 2.1, Puppy, Damn Small Linux look strange (too many hard lines) to me. LXDE falls somewhere in between.. next to Windows XP.

Also, it's a rock. LXDE+OpenBox **never** crashed on me or my web server.

---

### Post by gshenold on 2011-03-22
I'm running 10.10, and I have done a few things to tweak my system that I found online. You can tweak firefox via about:config. There are a few sites that can run you through this. I also tweaked open office, and there is a 200 line script you can install also, which i'm not sure really made a difference in any thing, but eh you can try it.

[http://www.multimediaboom.com/how-to-speed-up-your-ubuntu-with-a-200-line-script%EF%BB%BF/](http://www.multimediaboom.com/how-to-speed-up-your-ubuntu-with-a-200-line-script%EF%BB%BF/)

My first and main goal for Ubuntu though, is convincing apple to either give me their source code for Itunes, so I can personally convert it for debian/ubuntu users, or have them make a version for us. Lost cause most likely lol. But, optimizing your system isn't, so keep your chin up.

---

### Post by Objekt on 2011-03-24
Did the 200-line patch a while ago.  I never noticed that it made any difference.

FWIW, I do see some odd delays in Windows 7 as well.  For example, I've noticed that when viewing a directory with several hundred files and a few dozen folders, the folders often take several seconds to appear.

So no OS is perfect.

I do get tired of Firefox choking up.  Maybe Firefox 4 will be better.  Supposedly, it does some whiz-bang 2D acceleration stuff if you have an Nvidia graphics card, which I do (see below).

---

