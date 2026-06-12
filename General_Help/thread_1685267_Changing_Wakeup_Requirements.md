---
title: "Changing Wakeup Requirements"
date: 2011-02-10
forum: General Help
---

### Post by cearlp on 2011-02-10
I'm running Ubuntu 10.10. Is there a way to eliminate, or at least change the length of time, of having to enter your password after the screen timesout from no activity? I've looked all though Preferences but have not found anything that seems to address this.

---

### Post by I&#9829;HTML5 on 2011-02-10
Open Terminal and enter ```
gconf-editor
``` click "Apps" on the left, click "gnome-power-manager" on the left, select "lock" on the left, and uncheck the box next to "suspend". Now close that window and Terminal. Now watch as your screen fades to black, then resumes flawlessly!

Info from [http://ubuntuforums.org/showthread.php?t=283768]("http://ubuntuforums.org/showthread.php?t=283768")

---

### Post by cearlp on 2011-02-11
Sorry, gconf-editor did not solve what I wanted. I even unchecked the hibernate and that has no effect on what I want to change. After the screen goes black, any key click reactivates the system, but the screen has the enter password dialog on it. I just want to get rid of the dialog so I don't have to enter a password every time the system suspends.
Any other suggestions?

---

### Post by P4man on 2011-02-11
also disable the lock for the screensaver. System > preferences > screensaver, uncheck 'lock screen when screensaver is active".

---

### Post by cearlp on 2011-02-11
Thanks all, The combination of all the replies solved my problem.

---

