---
title: "unlock from screensaver asks for password twice"
date: 2010-07-06
forum: General Help
---

### Post by philnulty on 2010-07-06
Hi just done a software upgrade to kernel 2.6.32.24-generic from software centre (10.04)now i have a strange issue when the screen saver runs and i enter my password to unlock, I see the desktop for a few seconds then it locks again, when i enter my password a second time all is fine?*

I have disabled lock when screen saver activated and re enabled it just to check but it goes back to asking for my password twice.

Not sure what log files etc you need that might help.

---

### Post by zivley on 2010-08-05
I have the same problem, I don't know what causes it, I've just found that the "gnome-screensaver" has two processes, one run by gdm and the other by my user.
Killing one of them solves the problem, I just don't know how to avoid them from loading on boot.
It happened to me after a regular update a couple of weeks ago...

---

### Post by WorMzy on 2010-08-05
If you consistently have two gnome-screensaver processes, then try disabling the Screensaver entry in Startup Applications Preferences (System -> Preferences -> Startup Applications).

---

### Post by zivley on 2010-08-05
I don't have such an entry in my startup applications, that's where I first looked at...

---

### Post by WorMzy on 2010-08-05
That's weird. Maybe it's launched a different way on Lucid.

Check your crontab (open a terminal and run "crontab -l") and see if there's anything in there. Also look in your /etc/rc.local file, and see if that has any entries.

---

### Post by zivley on 2010-08-05
nope, did that too, I've read there is a bug filed in launchpad about this, I don't know where is it now, I guess it will be solved in some future update.

---

### Post by mjweaver on 2010-09-25
I'm having the same issue. Here's a link to the bug for reference: [Bug #556255]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/556255")

---

### Post by Rebootkid on 2011-05-18
Apparently this bug has been around a while.
I've still got it in 11.04.

---

