---
title: "gnome-shell on 11.10?"
date: 2011-10-13
forum: General Help
---

### Post by loolooyyyy on 2011-10-13
this isn't my day, i'm going nuts :(
after VMWare not working (**corrupted installation file 327MB!! turned to 32.7 on NTFS, strange, isn't it? *any suggestion for fixing?***)

and after "making" Virtual Box working(not working by itself) and after making it recognize USB, and after messing with "groups" and **accidentally removing myself from every existing group including sudoers(*what groups should i be a member of by default? tell me so i can fix it*)**

i finally managed to install gnome-shell on 11.10, but it looks like a regular gnome-2
not the "DEFAULT" dash or those beautiful transparent things here: [http://live.gnome.org/GnomeShell/Design/](http://live.gnome.org/GnomeShell/Design/)
and it doesn't look like any of those images found in a google image search "gnome shell"
what am i doing wrong?
***how do i make it look like this:***
[http://www.gnome.org/~mccann/screenshots/clips/20100106201448/shell-mockup-overview-test.png]("http://www.gnome.org/%7Emccann/screenshots/clips/20100106201448/shell-mockup-overview-test.png")
i should say again that it totally looks like gnome2 except that clock is now in the middle of panel, thats all

---

### Post by Vaphell on 2011-10-13
you need a flawless 3d acceleration inside the virtual machine which is no trivial thing to achieve. If anything in virtual_driver_of_guest/driver_of_host/hardware path is not working right, you are left with unaccelerated guest system with no fancy eyecandy.

---

### Post by loolooyyyy on 2011-10-14
ok, since it didn't mess anything up in VM, i'm gonna install it in host
but i've activated both 2d and 3d acceleration, what's wrong?

and vaphell, you, are a life saver!

---

