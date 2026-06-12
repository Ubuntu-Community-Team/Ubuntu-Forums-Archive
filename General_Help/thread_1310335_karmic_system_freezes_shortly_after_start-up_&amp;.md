---
title: "karmic: system freezes shortly after start-up &amp; wifi crash"
date: 2009-11-01
forum: General Help
---

### Post by prettygully on 2009-11-01
Dear All,
I upgraded my Dell Latitude D600 from Jaunty to Karmic at the weekend, using standard
upgrade procedure. All went well, however, with the new kernel (2.6.31-14) the system
freezes shortly after I have logged in - I seem to get a couple of mouse click which work
and then nothing happens - the  'wheel' for busy is showing, but not spinning.
An additional problem: I get a crash report for the wifi interface, again shortly after bootup.
The freeze problem does not occur when I boot with the previous kernel (2.6.28-16), but
the wifi problem persists (intel iw2100 mini pci card - worked well before update).

any advise how to deal with these problem would be greatly appreciated !
many thanks

karin

---

### Post by prettygully on 2009-11-02
Progress: following some advice on the web, I've solved my wifi-radar crash problem -
all it took was
**sudo rm /etc/wifi-radar.conf**
and to restart wifi-radar; apparently there was some consistency problem in this file between versions of wifi-radar on jaunty & karmic.

---

### Post by may88 on 2009-11-03
me too.

System locked up again tonight (as it always does).
Applied some updates (bit foolish) but it stayed up.

Then boom again.

Applied your suggestion but renamed my file out of the way.

System appeared stable. no sign of wifi-radar running.
Pulled up system-info and it hung in seconds.

another wifi-radar segfault in the messages file.  Thinking system info starts wifi-radar???

rebooted - ok for 10 minutes  pulled up system info and boom again.  It was at this point I heard a small plink in the back of my head.

Booting again...checking filesystems. Posted this on my windaz system.

---

### Post by may88 on 2009-11-03
having a hard time of it now.
rebooted three times had about 10 seconds to do anything on the gnome desktop and the last boot hung whist still logging in.

---

### Post by toulousain on 2009-11-04
Have a look at this post, this may help you: [http://www.uluga.ubuntuforums.org/showthread.php?t=1305349](http://www.uluga.ubuntuforums.org/showthread.php?t=1305349)

---

