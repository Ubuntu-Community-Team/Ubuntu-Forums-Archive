---
title: "Can't boot to Kubuntu! I get a black screen that tells me to login!"
date: 2010-04-18
forum: General Help
---

### Post by TheNerdAL on 2010-04-18
When I boot to Kubuntu 9.10, it asks me to login and I do, But then It just doesn't boot. 
 
It's like a big terminal. Help!

---

### Post by new_tolinux on 2010-04-18
Try logging in.....

Then type:
```
startx
```

And produce some nice error report here if that fails.

---

### Post by TheNerdAL on 2010-04-18
It says something like this :
 
```
xinit: No such file or directory (ernno 2): unable to connect to x server
xinit: No such process (errno 3): Server error.
```
 
There is more stuff above that but I can't copy and paste.

---

### Post by TheNerdAL on 2010-04-18
Anyone?

---

### Post by blueridgedog on 2010-04-19
This is a good resource:

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by TheNerdAL on 2010-04-19
> **blueridgedog said:**
> This is a good resource:
 
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
 
Doesn't help.

---

### Post by new_tolinux on 2010-04-19
As I read [here](http://ubuntuforums.org/showthread.php?t=1457486) you did edit your Xorg.conf file manually.

Probably you'll want to rename or delete that file, in order to clear any mistakes you may have made by accident.

---

### Post by TheNerdAL on 2010-04-19
> **new_tolinux said:**
> As I read [here]("http://ubuntuforums.org/showthread.php?t=1457486") you did edit your Xorg.conf file manually.
 
Probably you'll want to rename or delete that file, in order to clear any mistakes you may have made by accident.
 
How? If I can't boot?!

---

### Post by Untitled_No4 on 2010-04-19
After you log in run the following commands:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.back
sudo reboot
```

The first command will rename your xorg.conf file the second, well, it will reboot your computer.

---

### Post by blueridgedog on 2010-04-19
> **TheNerdAL said:**
> How? If I can't boot?!

You could boot on a LiveCD and delete the file from the local hard drive.

---

