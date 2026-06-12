---
title: "best linux distro for vfx artist"
date: 2012-10-08
forum: General Help
---

### Post by fernansha on 2012-10-08
Hi everyone, 

I am a vfx artist at the moment and i am a fan of linux. i bought a laptop recently and confused which linux distro to use. i need some expertise advise on this please.

many suggested linux mint and ubuntu 12.0 but i am not sure, which would be the best to approach.
i am not a fan of gui, i beleive in bunuch of codes ;) 

thanks for reading!

---

### Post by ragtag on 2012-11-27
This is a bit tricky to answer, as it depends on what software you're using for your VFX, and if you're comfortable with compiling software and scripting.

Blender, will for instance run on pretty much on any Linux distro that has hardware accelerated graphics (it runs in software GL too...but it's not that useful for real work).

A software like Maya comes as .rpm's, and is really designed for RedHat. That said, I wouldn't recommend using RedHat/CentOS on a VFX workstation. It's true that it's very stable, but a lot of the libraries that come with it are quite old. You'll quickly find yourself needing never versions of codecs, OpenEXR, ffmpeg, python and a number of other libraries. If you have the time, and are comfortable with compiling these from scratch, it can be a good choice. Some of the software you need may also need never versions of things like GTK+ and other base libraries, that can make compiling software for RedHat/CentOS much harder than for more up to date distros.

Since a lot of professional VFX software is made for RedHat (comes as .rpm), it would make sense to look at Fedora, but there are some issues here too. Fedora has a very short release and support cycle. This might not be a problem for a home user, but can quickly become problematic for a VFX house with 20+ workstations where it's impractical with upgrades every 6 months. At the same time, Fedora tends to have very up to date software and libraries. Fedora 17 ships with the latest version of both Blender and Gimp, for instance, and has up to date libraries for openEXR, OpenColorIO, ffmpeg and more. Beeing on the bleeding edge, can also be a bit dangerous.

Ubuntu 12.04 LTS, is somewhere inbetween RedHat and Fedora. It has lots of packages, and most of them are reasonably up to date (Gimp is at 2.6.12...for instance, not 2.8), though you may still finding yourself manually installing or compiling some of the tools you need. There is an extra overhead with installing software like Maya, in that you have to convert the .rpm's, and do some tweaking to get it to run correctly...but it's doable.

Not also that a lot of commercial software will only offer you support on officially supported platforms. So if the software says it works on RedHat 5 and Fedora 14, and you're running it on Ubuntu 12.04, they may simply refuse your support request. Yep...sometimes commercial software sucks. :P

The best thing you can do is try several different versions, and see which one works with all the software that you need. Then look at which window manager you like, Unity, Gnome2/3 or alternatives like Cinnamon, XFCE and others. I find this generally just comes down to personal preference.

---

