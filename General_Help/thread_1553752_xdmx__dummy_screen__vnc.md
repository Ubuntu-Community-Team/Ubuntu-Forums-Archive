---
title: "xdmx / dummy screen / vnc"
date: 2010-08-15
forum: General Help
---

### Post by ksatta on 2010-08-15
I've been playing around with xdmx for quite a while now. Everything works fine, but my keyboard goes "crazy". I've tried all the command line options to set model etc. For example the cursor keys capture a screenshot. The letters work, but  capslock/shift doesn't, etc..

Today I tried to create a dummy screen in xorg.conf and then vnc into it. Then the mouse didn't show or work in the vnc client.

Any suggestions?

Is there any way to fool the nvidia driver to think that there is a second display connected? I think that would work better. The dummy driver doesn't have xrandr etc.

I'm trying to get this to work on my desktop and laptop. They both have totally different hardware.

I'm running Ubuntu 10.04 and xdmx and vnc have been pulled from the default repos.

---

### Post by venkat_ram86 on 2010-08-23
i also have the same problems with Xdmx on ubuntu 10.04. Everything works fine except the keyboard which acts weirdly. Caps/Shift & other keys dont work. Some keys lead to different characters. All  keybindings are messed up.

Was anybody able to successfully run Xdmx on 10.04.?

---

### Post by ksatta on 2010-08-25
I "fixed" the problem by buying another monitor.

---

### Post by akaihola on 2010-12-04
Keyboard goes crazy when using xdmx between two Ubuntu 10.10 Maverick machines as well.

---

