---
title: "noob question about banshee media player"
date: 2009-12-13
forum: General Help
---

### Post by DevonS on 2009-12-13
today i was using banshee media player sound preferences.  under the applications tab, banshee shows up as /usr/lib/Banshee-1/Banshee.exe
i checked out the path, and sure enough there was an exe file.  which made me go WTF.  banshee's web site only allows you to download it for various versions of linux.  so why would there be a windows binary in my linux install of banshee?  was it just lazy programmers using wine?  or can exe mean something other than windoze executable?

---

### Post by DevonS on 2009-12-13
[http://packages.ubuntu.com/karmic/amd64/banshee/filelist](http://packages.ubuntu.com/karmic/amd64/banshee/filelist)
there are 4 exe's in this list.  so what's going on?

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
exe is an extension meaning executable and if the programmer wrote it to understand banshee.exe in stead of just banshee then that was their prerogative and you'd have to ask Novell why. Makes me wonder, though, if it would execute in Windows. I doubt it though.

---

### Post by DevonS on 2009-12-14
so it doesn't necessarily mean windoze?  thats a releif... it would be nice to know why... i'll test it out sometime in my vista install when i have time (cuz it takes so long to boot it lol)

it just would be a bit strange if part of their program runs on wine, and there is not a windows version available... hope thats not the case.

---

### Post by Tonurics on 2010-01-27
Actually banshee is cross platform; it uses Mono (Linux compatible version of .Net) and GTK for the main program. The exe files that you see are more than likely Windows binaries, however many of the dependencies required to make it work do not exist on Windows (so it won't run).

Some of the developers on the project were working towards having working Windows binaries. Unfortunately progress on that front seams to be extremely slow (maybe even stopped).

[http://abock.org/2007/02/21/banshee-on-windows](http://abock.org/2007/02/21/banshee-on-windows)

---

