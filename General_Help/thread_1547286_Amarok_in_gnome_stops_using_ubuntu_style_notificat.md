---
title: "Amarok in gnome stops using ubuntu style notifications"
date: 2010-08-06
forum: General Help
---

### Post by pataphysicianu on 2010-08-06
After installing the phonon-gstreamer-backend for Amarok, because the phonon-xine-backend is very buggy and plays some mp3 in a distorted manner, Amarok lost integration with ubuntu style notify-osd notifications when "use knotify" for notifications is selected under Configure Amarok.

I still get notifications but they are knotify styled, whereas before I added the  phonon-gstreamer-backend amarok was using notify-osd properly.

If I unistall phonon-gstreamer-backend it goes back to working with notify-osd properly

phonon-xine-backend is listed as a Canonical supported package, whereas phonon-gstreamer-backend is not. So I assume Canonical has added something in Amarok to patch notifications, and that phonon-gstreamer-backend changes that? Anyone have any ideas on how I could find out what that is, and correct for phonon-gstreamer-backend?

---

### Post by Darkness Des on 2010-08-06
You see, using knotify means that you are using knotify and not notify-osd. Uncheck the box and you'll be fine.

---

### Post by pataphysicianu on 2010-08-06
> **Darkness Des said:**
> You see, using knotify means that you are using knotify and not notify-osd. Uncheck the box and you'll be fine.

Actually no, if you have nothing checked for notifications you will receive none(otherwise it would suck for people who don't want notifications), if you check OSD you will get Amarok styled notifications, if you select knotify with the default ubuntu install of Amarok with only phonon-xine-backend you will get ubuntu style notify-osd notifactions. But manually installing the unsupported phonon-gstreamer-backend breaks this.

Canonical has been making supported KDE apps use notify-osd if they are running in gnome, and you choose knotify, to create an integrated appearance.

---

### Post by pataphysicianu on 2010-08-06
Well it turned out the gstreamer backend in amarok has other worse problems than xine, so I went back to xine backend. In further research it seems xine will barf on mp3s with certain unknown streams in the file, whereas gstreamer will play these without problem. I only hit on two or three of these after playing mp3 for several days, and using mp3diags I fixed them and they now play fine in xine.

---

