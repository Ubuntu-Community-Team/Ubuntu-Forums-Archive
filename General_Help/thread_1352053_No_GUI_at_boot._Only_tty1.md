---
title: "No GUI at boot. Only tty1"
date: 2009-12-11
forum: General Help
---

### Post by OldGrantonian on 2009-12-11
I have dual-boot WinXP and Karmic.

Sometimes when I try to boot to Karmic, I get the tty1 console.

How do I launch the GUI from this screen?

---

### Post by tom66 on 2009-12-11
Type 'startx'. Though there's probably a reason why you aren't getting a GUI - it should start automatically. A similar problem occurred with my laptop due to faulty graphics drivers.

---

### Post by john newbuntu on 2009-12-11
sudo /etc/init.d/gdm start

---

### Post by OldGrantonian on 2009-12-11
Thanks for both replies :)

The tty1 problem occurs when I restore an /etc backup. So I've made a new post for this:
[http://ubuntuforums.org/showthread.php?p=8479588#post8479588](http://ubuntuforums.org/showthread.php?p=8479588#post8479588)
.

---

