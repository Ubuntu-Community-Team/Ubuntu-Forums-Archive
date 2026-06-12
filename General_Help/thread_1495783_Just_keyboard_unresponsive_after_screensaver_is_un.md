---
title: "Just keyboard unresponsive after screensaver is unlocked"
date: 2010-05-28
forum: General Help
---

### Post by chcarver on 2010-05-28
Problem: When my screen saver kicks in after idle timeout and I get back to my desktop the keyboard is unresponsive in already opened applications with text fields. This happens with and without the password required after screen saver is engaged. This doesn't happen all the time and seems to be transient. It happens at least once a day, but not often.

Workaround: The mouse is still usable, so I open a terminal and hit a few keystrokes. The keyboard is now responsive and I can go back to typing in the open applications that I previously had open prior to the screen saver being engaged.

---

### Post by dino99 on 2010-05-28
you might look at errors and warnings logged:

- .xsession-errors into /home (unhide it with menu)
- system admin log viewer

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

[http://www.google.fr/search?as_q=lucid%2B+&hl=fr&tbo=p&num=10&btnG=Recherche+Google&as_epq=lost+mouse&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=lucid%2B+&hl=fr&tbo=p&num=10&btnG=Recherche+Google&as_epq=lost+mouse&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

