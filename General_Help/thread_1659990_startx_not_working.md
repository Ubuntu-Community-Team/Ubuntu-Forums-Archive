---
title: "startx not working"
date: 2011-01-04
forum: General Help
---

### Post by mmsmc on 2011-01-04
Hi all, im stuck in tty again, i was downloading the newest version of nvidia when it told me that noveau was saved int a file and that i would have to erase in order to boot noveau again, nvidia of course failed on me again, and now i cant get back on to my desktop!

---

### Post by lidex on 2011-01-04
Can you be a little more concise? What driver was installed? What did you do exactly? Can you access the partition with a LiveCD? The contents of /var/log/Xorg.0.log would be helpful.

---

### Post by mmsmc on 2011-01-04
the default noveau driver was installed, nvidia uninstalled it, and when it went throught the installation process and failed without putting noveau back, im not to sure how to open the file through the terminal im using a usb drive, and no i cannot boot from it

---

### Post by mmsmc on 2011-01-04
ive been searching and have not found anything useful

any ideas any body?

---

### Post by lidex on 2011-01-04
Can you boot into recovery mode? If you can, then get to a console, log in and run this command:
```
sudo nvidia-xconfig
```
and reboot.

---

### Post by BicyclerBoy on 2011-01-04
From your tty login check the Xorg log file.
/var/log/Xorg.0.log

You need to check if the nouveaux driver kernel module is stopping the nvidia from loading.

Solution for that can be by blacklisting nouveaux module.

Google is your friend..

What was the error message from the nvida installer ?

Do you have the required linux-headers that match your kernel ?

---

### Post by mmsmc on 2011-01-05
what is blacklisting and how do you do it, will it work?

---

