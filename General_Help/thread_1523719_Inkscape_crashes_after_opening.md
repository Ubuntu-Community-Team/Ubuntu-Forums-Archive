---
title: "Inkscape crashes after opening"
date: 2010-07-04
forum: General Help
---

### Post by JaredFactley on 2010-07-04
Inkscape loads fine, but if I do anything with it, the application crashes and I get the following error:

** ERROR **: Failed to register GObject with DBusConnection
aborting...
Trace/breakpoint trap

Running 10.04. Have found similar reports that say updating or reinstalling has fixed this, but I tried and I'm using the latest version. 

Any ideas?

---

### Post by JaredFactley on 2010-07-04
Update:

I get a very similar error I noticed now in GIMP as well:

VANISH
gimp: fatal error: Failed to register GObject with DBusConnection

(script-fu:23253): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error

---

### Post by alexsleat on 2010-07-04
I'm getting the same error in gimp too

```
:~$ gimp
gimp: fatal error: Failed to register GObject with DBusConnection

(script-fu:3100): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error

```

I managed to get it fixed, remove package appmenu-gtk.

[http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/](http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/)

---

### Post by JaredFactley on 2010-07-05
Thanks a lot, that seemed to do the trick!

---

### Post by randlieb on 2010-08-26
My problem is slightly different. Inkscape won't even open. When I click on Inkscape the cursor twirls for a few seconds and then stops. I can look in my System Monitor and see that it is running but it is nowhere open on the desktop.

I don't know if removing the package **appmenu-gtk** was meant for just GIMP or Inkscape also. Regardless, I looked in Synaptic and couldn't even find the package.

Have re-installed but no change.

Running Ubuntu 10.04.

I really like using this program for basic artwork (as opposed to using GIMP). Had no issues with any previous versions of Ubuntu.

Any ideas anyone?
Thanks

---

### Post by sistarbliss on 2010-11-15
> **randlieb said:**
> My problem is slightly different. Inkscape won't even open. When I click on Inkscape the cursor twirls for a few seconds and then stops. I can look in my System Monitor and see that it is running but it is nowhere open on the desktop.

I don't know if removing the package **appmenu-gtk** was meant for just GIMP or Inkscape also. Regardless, I looked in Synaptic and couldn't even find the package.

Have re-installed but no change.

Running Ubuntu 10.04.

I really like using this program for basic artwork (as opposed to using GIMP). Had no issues with any previous versions of Ubuntu.

Any ideas anyone?
Thanks


I am having the same problem as well.  Have reinstalled.  appmenu-gtk is not listed in synaptic on my 10.04 install.

---

### Post by sistarbliss on 2010-11-15
Ok I figured out my problem. I have too many fonts installed.  I renamed my /home/username/.fonts directory to "fonts" without a dot and it has fixed my problem.

---

### Post by johanbove on 2010-12-23
Hi, just how many fonts did you have installed? How many is too many for these programs to handle?

---

