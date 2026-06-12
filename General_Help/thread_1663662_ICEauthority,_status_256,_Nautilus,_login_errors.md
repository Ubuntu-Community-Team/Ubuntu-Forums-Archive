---
title: "ICEauthority, status 256, Nautilus, login errors"
date: 2011-01-09
forum: General Help
---

### Post by lordknows on 2011-01-09
Running ubuntu 10.10
dell inspiron N5010
sorry if prefix is wrong wasn't really sure in what category to put it

Could not update ICEauthority file /home/anon/.ICEauthority

There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Nautilus could not create the required folder "/home/anon/.nautilus".
Before running Nautilus please create the following folder, or set permissions such that Nautilus can create it.

---

### Post by Lian Radu on 2011-01-13
The message appears after logging in with your user name (before that, the user is root).
Check the owner for .ICEauthority. It this is root, you can change it to your username:
sudo chown anon /home/anon/.ICEauthority

You can open the folder /home/anon/ as root with
sudo nautilus /home/anon

or install nautilus-gksu with
sudo apt-get install nautilus-gksu
then restart, and you can open any folder with root privileges by right-clicking on it -> Open as administrator.
Then you can change the owner of a file if you right click on it -> Properties -> Permissions

---

### Post by TheHackOps on 2011-01-13
I had the Ice.Authority error due to a mounting error

Anyone who gets /home won't mount Press C or w/e

1. Login as root
2. Open partition manager
3. mount /home
4. Copy the uuid of the HDD
5. open fstab file as root
6. replace the /dev/sda1 or w/e with UUID= <Insert UUID there>
7. reboot and viola :)

---

### Post by TheHackOps on 2011-01-13
I had the Ice.Authority error due to a mounting error

Anyone who gets /home won't mount Press C or w/e

1. Login as root
2. Open partition manager
3. mount /home
4. Copy the uuid of the HDD
5. open fstab file as root
6. replace the /dev/sda1 or w/e with UUID= <Insert UUID there>
7. reboot and viola :)

---

