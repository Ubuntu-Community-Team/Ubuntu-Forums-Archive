---
title: "built banshee 10.7, now no ipod support"
date: 2006-03-06
forum: General Help
---

### Post by zachtib on 2006-03-06
i think its due to this: 
```
zach@notapowerbook:~$ banshee
Player Engine `Helix Framework Engine (hxclientkit)' failed init tests... disabling (Couldn't create player)
Debug: [3/6/2006 8:09:02 PM] (Changed active playback engine) - GStreamer
Debug: [3/6/2006 8:09:02 PM] (Loaded primary playback engine) - GStreamer
Debug: [3/6/2006 8:09:02 PM] (Loaded Audio CD playback engine) - GStreamer
Debug: [3/6/2006 8:09:02 PM] (Audio CD Core Initialized) -
/home/zach/.themes/Cairo-Graphite-P/gtk-2.0/gtkrc:150: error: invalid string constant "metacity-frame", expected valid string constant
Warning: [3/6/2006 8:09:05 PM] (Could not connect to D-Bus) - D-Bus support will be disabled for this instance: Object reference not set to an instance of an object
Scanning library for tracks to update
Done scanning library
Processing track queue for pending queries
Done processing track queue




```

its not connecting to dbus

also, i had ipod support working earlier today, in 10.7, but then i tried to rebuild with the browser added in, and that didn't work, so i recompiled the same way i did earlier and installed, but now the ipod wasn't working

---

### Post by RAOF on 2006-03-06
I presume you built Banshee with --enable-ipod at ./configure, didn't you?  iPod support is disabled by default.

---

### Post by skymt on 2006-03-06
```
Warning: [3/6/2006 8:09:05 PM] (Could not connect to D-Bus) - D-Bus support will be disabled for this instance: Object reference not set to an instance of an object
```

Yep, that's the problem. Looks like a bug, either in Banshee or one of the libraries it uses. Make sure you have the latest versions of everything involved. Then try the latest Banshee from CVS (or SVN or whatever they use). If neither of those work, contact the developers and they'll give you further instructions on how to debug this.

Edit: ... Oh yeah, and also what RAOF said. ;)

---

### Post by RAOF on 2006-03-06
[QUOTE=skymt]```
Warning: [3/6/2006 8:09:05 PM] (Could not connect to D-Bus) - D-Bus support will be disabled for this instance: Object reference not set to an instance of an object
```

Yep, that's the problem. Looks like a bug, either in Banshee or one of the libraries it uses. Make sure you have the latest versions of everything involved. Then try the latest Banshee from CVS (or SVN or whatever they use). If neither of those work, contact the developers and they'll give you further instructions on how to debug this.[/QUOTE]
But I don't **think** that D-Bus support is needed for iPod support.  It might be if you want to plug in your iPod after opening banshee, but if it's plugged in before you run Banshee I think it should work without D-Bus.

---

### Post by zachtib on 2006-03-06
actually, ipod support IS enabled by default in banshee.

ill try the latest from CVS

the weird thing is a had it working earlier... weird

if i ever get it working, id be happy to provide debs

---

### Post by zachtib on 2006-03-06
no good, still doesn't see my ipod

---

### Post by RAOF on 2006-03-06
Does the output from ./configure include: "iPod: yes"?  The last thing it prints is a bunch of information about what support is being built in.

If you've passed --enable-ipod to ./configure, and it doesn't say "iPod: yes" somewhere at the end, I'd suspect that you've got too old a version of either libipoddevice or ipod-sharp.  Get the cvs/svn respectively (you can find out where from [www.banshee-project.org](www.banshee-project.org)), remove the current libipoddevice/ipod-cil (which is what ipod-sharp gets called in synaptic, I believe), and then try again.

---

### Post by zachtib on 2006-03-06
[QUOTE=RAOF]Does the output from ./configure include: "iPod: yes"?  The last thing it prints is a bunch of information about what support is being built in.

If you've passed --enable-ipod to ./configure, and it doesn't say "iPod: yes" somewhere at the end, I'd suspect that you've got too old a version of either libipoddevice or ipod-sharp.  Get the cvs/svn respectively (you can find out where from [www.banshee-project.org](www.banshee-project.org)), remove the current libipoddevice/ipod-cil (which is what ipod-sharp gets called in synaptic, I believe), and then try again.[/QUOTE]

yes it does, and i built the ipoddevice and ipod-sharp from the latest tarball today

this exact same procedure **worked this morning**, then I tried to rebuild banshee with the browser enabled, which is when i broke something, and now I cannot get it to work...

I'm very confused

---

### Post by RAOF on 2006-03-06
Oooh! Oooh!  I seem to remember from the Banshee list that the Browser patch would fail to build with iPod support - maybe the problem is actually in the browser patch.

Try reverting the patch an build again?  If that works, you've got your culprit ;)

Maybe there's some cruft left over from the browser patch.  Have you tried building in a clean directory?

---

### Post by zachtib on 2006-03-06
this is in a clean directory,

i copied my  build directory to banshee_browser, and did the browser work there

now im working in a fresh directory from the tarball

somewhere along the line i broke something else in the process

---

