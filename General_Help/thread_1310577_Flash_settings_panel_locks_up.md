---
title: "Flash settings panel locks up"
date: 2009-11-01
forum: General Help
---

### Post by Fr33d0m on 2009-11-01
I've had this problem since Hardy, and it didn't start out this way.  I am on a Dell XPS M1330.  If I right-click on a flash application to change some settings, it locks up.  I cannot clear the settings dialog without at least a refresh of the web page.  This is the same no matter what the app or browser.

I upgraded to Jaunty and still had the problem so I did a clean install of Karmic (64-bit) with a reformat of all drives and have the problem with the 64-bit player.  The 32-bit also had the problem and Gnash and swfdec don't display the same dialog--they didn't lock up either.

Does anyone have any idea what could be causing this or how I might debug?

---

### Post by jhb1608 on 2009-11-01
Same here, I have same problems.

---

### Post by Fr33d0m on 2010-02-02
Three months later and the problem persists.  Call this a bump if you will but no ideas have been forwarded.

---

### Post by Fr33d0m on 2010-02-02
sudo apt-get install libadns1

That solved it.

---

