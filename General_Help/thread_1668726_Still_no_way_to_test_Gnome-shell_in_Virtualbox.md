---
title: "Still no way to test Gnome-shell in Virtualbox?"
date: 2011-01-16
forum: General Help
---

### Post by winchendonsprings on 2011-01-16
I've searched and read lots about trying to get gnome-shell to run in Virtualbox(v4) with no success on my end.  Lots of the posts are outdated and are using Virtualbox 3. 

So anyone have any tips or hints for testing the Gnome-shell?  (I'd prefer to test in with 10.10 in Virtualbox 4, but am open to upgrading to 11.04 if necessary)

---

### Post by winchendonsprings on 2011-01-18
yay? nay?

---

### Post by akand074 on 2011-01-18
Did you install guest additions? I haven't used Virtual Box in a while but 4.0 supports guest additions in Linux and it's somewhere in the menu and it runs as a removeable disk. Once installed you should be able to set up 3D acceleration. 

Though, if I'm not mistaken, Unity requires 3D, but gnome-shell does not and it should revert to that by default if you don't have 3D acceleration enabled. There were also rumours of gnome-shell being pulled out of Natty for now, there were also rumours of Unity going to support 2D as well. Not sure of all the facts.

---

### Post by winchendonsprings on 2011-01-19
I believe Virtulabox 4 still doesn't support gnome-shell "as is." It does have 3d acceleration but neither gnome-shell or unity 3d work. At least not in Maverick. When launching gnome-shell from the terminal, it launches, but is totally scrambled. I do, however, have unity 2d(changed today from unity qt in the repo) working fine. 

If someone knows a trick to get it working I'd love to know.

---

### Post by nilarimogard on 2011-01-20
Unity 3D does work in VirtualBox 4.0. Gnome Shell still doesn't...

---

### Post by nilarimogard on 2011-01-20
[Unity 3D does work in VirtualBox]("http://www.webupd8.org/2010/12/how-to-test-ubuntu-1104-with-unity-in.html"). Unfortunately Gnome Shell still doesn't...

---

### Post by winchendonsprings on 2011-01-23
Unity 3d works in virtualbox on 11.04, but not 10.10 correct?

---

### Post by winchendonsprings on 2011-04-06
Gnome 3 is released. Still can't use gnome shell in Virtualbox, correct?

---

### Post by techunit on 2011-04-06
Yeah we are aware. The problem is because Gnome insisted on using Mutter for acceleration with isn't supported by the guest additions. There is no way of making it work with compiz.

---

### Post by Another Monkey on 2011-04-12
Ah!  Thanks you for the succinct summary.  I had forgotten that the VB GA did not support Mutter.
Dman - Shell looks so good to, but I want to test it virtually before changing my main desktop.

---

### Post by WorMzy on 2011-04-12
Try out a LiveCD/USB of it?

[http://www.gnome3.org/tryit.html](http://www.gnome3.org/tryit.html)


In all honesty, you're not missing out. It's unintuitive, slow, clunky, and completely unnecessary. I'll be sticking with GNOME 2 for the foreseeable future.

Of course, that's just one man's opinion. :)

---

