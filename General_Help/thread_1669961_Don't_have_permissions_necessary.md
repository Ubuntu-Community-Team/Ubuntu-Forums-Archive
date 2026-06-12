---
title: "Don't have permissions necessary"
date: 2011-01-18
forum: General Help
---

### Post by benthicbread on 2011-01-18
I recently created a dual boot on my son's laptop (Dell Latitude D610) with Ubuntu/Windows when he was having issues with his Windows OS.  I think that his hard drive is failing, as a few boot issues continued and it finally failed to boot.  I am currently trying to salvage his data which is all in one folder on his desktop on the Ubuntu partition.  I am able to boot from CD (Karmic) and view the contents of this partition.  I can see the folder he needs in his "Desktop" directory, but it won't let me see the contents of the folder or copy it because I "do not have the permissions necessary".  How do I set permissions for this while booting from CD?  Thank you!

---

### Post by tredegar on 2011-01-18
Congratulations on finding the files.

The live CD lets you become root without any passwords.
So boot to the live CD
Then open nautilus as root from a terminal

**gksudo nautilus**

From _that_ nautilus window, open another, so you have 2 root windows to drag & drop from & to, as root.

Navigate to the folder you wish to copy, drag it to where you want it to be, hopefully an external HDD or something that is reliable, and not failing.

Once the files are copied, if you still have permissions issues, post again or read **man chown** to learn for yourself how to fix it up.

Good luck (and replace of the failing disk).

---

### Post by benthicbread on 2011-01-18
Well, as soon as I posted the question, I figured it out - created a new user with same name and password.  Logged in and voila!

---

