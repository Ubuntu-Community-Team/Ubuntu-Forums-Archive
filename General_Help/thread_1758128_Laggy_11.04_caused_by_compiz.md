---
title: "Laggy 11.04 caused by compiz"
date: 2011-05-14
forum: General Help
---

### Post by Naike on 2011-05-14
I've had lag problems in all 11.04 distros, whether it be ubuntu or any other linux distro I've tried.
Laggy window draggins, laggy animations etc.
Well, I tried linux mint 11 RC, and I found out that when I changed the window manager from compiz to metacity, everything runs crystal smooth.

Can anyone help me get another window manager to ubuntu?

---

### Post by ghostborg on 2011-05-14
If you have ATI graphics try turning off Sync To VBlank in the Compiz Config Settings Manager, General -> OpenGL -> Preferences.
I had this problem with an ATI HD3200 and I also had to enable Tear Free in the Catalyst Control Center.
Specify your graphics for other people to help you.

---

### Post by Naike on 2011-05-14
Sorry, I have the 5870, and none of the mentioned fixes work for me.

---

### Post by cottfcfan on 2011-05-14
Naike...
I also have to agree with you.
Try running gtkperf with compiz on, then switch to Metacity, run it again and see the difference.
In Lucid compiz runs smoother and faster, in Natty i've had to switch to Metacity & enable compositing.
I'm using a radeon HD2400 gfx card btw.
There does seem to be a problem with compiz & ati gfx cards.

---

### Post by Naike on 2011-05-14
I'm currently downloading 10.04, I'm ditching 11.04 for now, so many problems.

---

### Post by linuxuser12345 on 2011-05-14
Duplicate thread.
[http://ubuntuforums.org/showthread.php?t=1757828](http://ubuntuforums.org/showthread.php?t=1757828)

---

### Post by Naike on 2011-05-14
Not really.

---

### Post by creitve on 2011-06-08
Have this problem, nothing helped. Tried switching to metacity, it's okay without compisiting. But with compositing both compiz and metacity start to lag horribly. I have radeon hd3850. Any advice for me?

---

### Post by linuxinstalledfromhdd on 2011-06-08
Try using 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

