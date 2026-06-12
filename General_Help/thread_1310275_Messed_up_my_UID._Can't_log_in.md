---
title: "Messed up my UID. Can't log in"
date: 2009-11-01
forum: General Help
---

### Post by wersdaluv on 2009-11-01
I changed my user's UID and GID (from both 501 to both 1000) on /etc/passwd and through GNOME's (I'm on Karmic so this is what? GNOME 2.28?) "Users Settings" dialog. However, the change I make on the GUI never gets implemented. I can change the GID value but when I go back to check the value on the GUI, it goes back to the old value, which is 501.

Now, I can't use my primary user account because permissions are messed up. Any idea how to fix this?

A bit offtopic but this may help. I had 501 as UID and GID because I had to have the same values as the ones in my other OS. However, having UID<1000 is a bigger pain in Karmic. I already chose to show all user accounts, but it never shows up for the login screen or the "Login Screen Settings" dialog.

---

### Post by falconindy on 2009-11-01
IDs were likely changed but GNOME no longer had access to show it. You might try booting from a live CD and running chown over your $HOME from the terminal (after mounting the drive, of course):
```
sudo chown -R 1000:1000 /path/to/home/dir
```
And of course, from the livecd, you can check in /etc/passwd and /etc/group that your IDs were actually changed...

---

### Post by wersdaluv on 2009-11-02
Coolnees! Itjust worked. It's a good thing I was able to make an extra user account for that purpose. Just made it there.

Thanks! :) :KS

---

