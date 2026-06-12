---
title: "How to go restore the system to gui mode"
date: 2010-10-20
forum: General Help
---

### Post by pnewbie on 2010-10-20
Hi,
 I was   installing mail server on a desktop for just experimentation using sudo tasksel command. I selected the second option that says mail sending using internet. During installation it asked for something about phpmyadmin, which was already installed on my system. I selected no, and then during installation it removed all the utilities from my system and now system startups in  terminal mode. I have some very important data on that system that i can't afford to lost. please help me out so that i can again start the system in normal graphical mode or tell me a way so that i can transfer my data to anyother media. Please somebody help me to get out of this ......

I was using Ubuntu 10.04

---

### Post by linux-hack on 2010-10-20
You could reinstall the gnome desktop :

```
sudo apt-get install ubuntu-desktop
```
or if you do hav'it just reconfigure the X11 server with this command:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by chessnerd on 2010-10-20
Okay, if you think this removed all of the packages for GUI then I would suggest doing this command to find out:
```
sudo aptitude search gdm
```
See if gdm is listed with an "i" at the start. If so, it hasn't been uninstalled. In which case, I would recommend reinstalling it to reset gdm:
```
sudo apt-get install --reinstall gdm
```
See if that allows you to get to the login screen.

If gdm is not listed with an "i" then that would mean that it has been removed. If so, I would run this command to reinstall all the packages on your system that were there when you first installed it.
```
sudo apt-get install ubuntu-desktop
```
After that, all of your packages should be back.

I have almost no knowledge when it comes to mail servers and php, but if the problem is as you describe, that might fix it.

---

### Post by pnewbie on 2010-10-20
Thanks, for your help. Problem solved

---

### Post by linux-hack on 2010-10-22
Can you say how did you solve your problem and put a SOLVED in the title. This way others with the same problem can see this!
Thanks

---

### Post by pnewbie on 2010-10-22
Oops ... sorry for that,
I have used the method suggested by the chessnerd.
Once again thanks to you all.

---

### Post by pnewbie on 2010-10-22
Oops.. sorry for that .... I have applied the steps suggested by chessnerd.
Once again Thanks to you guys ..... for helping me ...

---

