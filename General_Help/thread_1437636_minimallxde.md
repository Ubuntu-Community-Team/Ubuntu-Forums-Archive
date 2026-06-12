---
title: "minimal/lxde"
date: 2010-03-24
forum: General Help
---

### Post by dzon65 on 2010-03-24
I've already spent some time on this on the forum but...This is a minimal/cli/9.10/gnome-core install.I installed lxde on top of it in order to be able to log in a lxde session.I've already installed/reinstalled lxde a number(s) of times and always the outcome was the same.1)no option to set default progs2)no thumbnails in pictures/images folder3)no extract option in the menus.
I'm a bit tired having to go through a total reinstall once more.So,I was wandering someone else has encountered these problems and found out what's wrong.For now gonna install the latest lubuntu ppa and try a lubuntu desktop (which I wan't looking for in the first place).Tried lubuntu before with the same problems.The problems do not occur when installing another distro using pcmanfm and OB.Noy sure if they would occur when having lxde installed on a full karmic install (so far nobody had),and not really want to try it.
So,is there anyone out there with the same setup 9.10 gnome-core/lxde having the same problems?
Second shot shows pictures folder respectively  pcmanfm and thunar.

---

### Post by dzon65 on 2010-03-24
So,installed the latest ppa...........same result.

---

### Post by kerry_s on 2010-03-24
have you tried with 10.04? 
9.10 had a lot of problems, even i skipped 9.10, i stayed with 9.04 then moved to the lubuntu 10.04 just before lucid went beta.

mini.iso you like:
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/)

---

### Post by dzon65 on 2010-03-24
Well ,gonna give that one a try.Just found out some more stuff not working (language,menu icons)...
Gonna gat rid of this and gonna mark this thread as solved.Oh,one more thing;Nothing to do with this but if you happen to know how to set the screenresolution to 1280X800 (highest now 1024.)in slitaz,let me know please.
Kind regards,J.

---

### Post by kerry_s on 2010-03-24
> **dzon65 said:**
> Well ,gonna give that one a try.Just found out some more stuff not working (language,menu icons)...
Gonna gat rid of this and gonna mark this thread as solved.Oh,one more thing;Nothing to do with this but if you happen to know how to set the screenresolution to 1280X800 (highest now 1024.)in slitaz,let me know please.
Kind regards,J.

that's the 1 you said has vesa right?
as far as i know vesa only does 1280x1024, 1024x768 & 800x600
you'll have to install xorg then you can run "X -configure" to get you a xorg.conf that you can copy to /etc/X11/xorg.conf 
(tip: cat /root/xorg.conf > /etc/X11/xorg.conf).

---

### Post by dzon65 on 2010-03-24
Hi kerry.Sorry,"momentary" lapse of time.Yeah,had xorg installed,had to adjust some more stuff.Working now.Veeery nice distro,very fast.Been busy with it,no time to try minimal lynx/lxde yet.'Ve heard still a bit buggy though.
Thanks for the replies.Kind regards,J.

---

### Post by dzon65 on 2010-03-24
Forgotten something.This rig's processor is a amd turion.back then tried to install kde to check it out.Turned out there was no support for this kind of processor;Don't know now,but made me think about that lxde prob.

---

