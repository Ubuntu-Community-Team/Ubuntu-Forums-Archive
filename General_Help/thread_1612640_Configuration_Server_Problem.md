---
title: "Configuration Server Problem"
date: 2010-11-03
forum: General Help
---

### Post by John Merlyn on 2010-11-03
hi,

I am a complete noob to UNIX/LINUX, i managed to install ubuntu 10.10 yesterday with a little effort and dual boot it with windows 7. 

today after the screen went to screensaver i was unable to bring it back and had to restart by turning the power off. the next time i booted ubuntu i am getting this error. please help


"There is a problem with configuration server
(/usr/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

then on the top right i get this message

"The configuration defaults for GNOME Power Manager have not been installed correctly 

Please contact computer admin"

Unfortunately i am the admin for the comp, can someone suggest a repair that does not involve a re-installation.

thanks in advance 

John

---

### Post by cj13579 on 2010-11-03
Hey, welcome to the forums.

Try running the following commands from a terminal:

```
sudo chmod 1777 /tmp
```

---

### Post by John Merlyn on 2010-11-05
hey,
 
thanks for the response. i talked to a friend and he suggested the same. also i did something really bad(cause i was playing around in the command line, part of the learning process :D) i was not able to open a few folders , as i was trying to find where what is stored. so i gave this command
 
sudo chmod 755 /root.
 
could this have done anything to the boot process because of access (i dont understand how as i gave execute permission to all). i was also unable to run the command you suggested in the normal mode(cntrl+alt+f2) or safe mode. 
 
thanks for your time and patience
 
John

---

### Post by CharlesA on 2010-11-05
Did you chmod "/" or "/root" ?

---

### Post by John Merlyn on 2010-11-05
hi,
 
not sure but i think 
 
chmod 755 /
 
John

---

### Post by CharlesA on 2010-11-05
Yeah, you're pretty much toasted.

If you use the -R switch, your system is probably hosed.

If you can boot off a livecd and pull yer data off, then reinstall, that would be the best way to fix it.

---

### Post by Verbeck on 2010-11-05
just out of curiosity : why did you chmod 755 / ?

edit: if you cant browse to a folder, put a sudo in front of it (sudo cd /root) or run the root nautilus (gksu nautilus). just remember that access to those folders is restricted for a reason

---

