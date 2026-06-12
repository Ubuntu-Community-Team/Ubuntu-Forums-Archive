---
title: "Open folder does not work in Ubuntu 9.10"
date: 2009-11-18
forum: General Help
---

### Post by dancantong on 2009-11-18
Hi!
I just upgraded to Ubuntu 9.10 and I have this issue. When any applications request opening a folder, nothing happens. I think Nautilus is not more registered as the default file manager. I wonder if there is any way to set default file manager for Gnome or to fix this issue.

Thanks in advance.

Daniel.

---

### Post by Giblet5 on 2009-11-18
Click on Places -> Home

Did nautilus start?

If not, then open a terminal window (Applications -> Accessories -> Terminal) and enter ```
nautilus
```

Did nautilus open? Did you get error messages in the terminal window? Post them (select, copy, paste) here inside a CODE block (the '#' icon in the forum's comment editor).

---

### Post by dancantong on 2009-11-18
Thank you Giblet5.

If I execute nautilus in a terminal it opens as expected.
If I click on Places -> Home and error dialog opens saying that there isn't any application registered to handle this file.

---

### Post by Giblet5 on 2009-11-18
Your menus are broken.

Here is a brute-force way to fix it and return your session to the defaults:

Open a terminal window and enter:
```
mkdir config-old
mv .gconf* .config config-old
mv .gnome* config-old
sudo /etc/init.d/gdm restart
```

That will take you directly to the login screen. Log in.

Test it - it should be working perfectly. If so tell me and mark this thread SOLVED with the Thread Tools above.

---

### Post by dancantong on 2009-11-18
Sorry, but It didn't work. The same message shows when clicking on Places.

---

### Post by Giblet5 on 2009-11-18
Try creating a new user "test1". Log off and log in as test1.

Does the new user have the same problem?

---

### Post by dancantong on 2009-11-19
Ok, I created a new user and then nautilus work perfectly.

Thanks for your help.

---

