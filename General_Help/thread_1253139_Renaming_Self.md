---
title: "Renaming Self"
date: 2009-08-29
forum: General Help
---

### Post by Stuart P. Bentley on 2009-08-29
Had this question for myself and noticed some of the information from [http://ubuntuforums.org/showthread.php?t=64021](http://ubuntuforums.org/showthread.php?t=64021) was a little inaccurate/out of date.

Anyway, GNOME doesn't allow a user to rename themselves through the UI. However, this can be effectively accomplished by entering the following commands (where <oldname> is the current username going in and <newname> is the desired new username) into a terminal (either from Applications->Accessories->Terminal or from the one provided in the alternate sessions from the login screen):

```
sudo usermod -l <newname> -d /home/<newname> -m <oldname>
```This performs the actual username switch and moves your home directory.

```
sudo groupmod -n <newname> <oldname>
```This should be performed as well, to rename your corresponding user group.

```
grep -l "home/<oldname>" -R . | xargs sed -i.BAK 's|home/<oldname>|home/<newname>|'
```This will update any of your files that contain static links to your old home directory (such as the bookmarks under "Places") to your new home directory.

(It's probably a better idea to do this from a terminal from the login screen where your desktop isn't running simultaneously, although I did the last one from inside GNOME and haven't had any trouble.)

---

