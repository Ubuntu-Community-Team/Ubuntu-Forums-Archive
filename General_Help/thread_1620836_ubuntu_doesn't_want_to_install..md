---
title: "ubuntu doesn't want to install."
date: 2010-11-13
forum: General Help
---

### Post by Twixx on 2010-11-13
I was gonna try to install ubuntu 10.10, always got same error, always a black screen and then alot of text.

I have windows 7 home premium x64 bit installed on the computer.

---

### Post by sohlinux on 2010-11-13
what did the error say before the text? I cannot see the error on your image, it only shows the files loading after the error.

did you do a side by side install or you used the whole drive?

or is this the live cd giving the error?

---

### Post by Twixx on 2010-11-13
I booted up the computer with the disc i burned the file on, then I chose install ubuntu, then that popped up
and I've tried side by side and whole drive, even test, this came up every single time

---

### Post by sohlinux on 2010-11-13
boot from the live cd then use admin - gparted to format the whole hard drive ext4, but backup anything you may have on there first. then try the install again. if you see any errors during the install take a pic of the screen and attach it here. I take it your windows was working ok before you tried ubuntu?

---

### Post by Twixx on 2010-11-13
it was working perfectly, gonna try ur way in a sec

---

### Post by Swagman on 2010-11-13
He might not want to lose his Windows 7 install so choosing format entire drive would not be a wise choice.

---

### Post by Twixx on 2010-11-13
I want ubuntu as my OS, gonna get rid of windows 7

---

### Post by Twixx on 2010-11-13
> **sohlinux said:**
> **boot from the live cd then use admin - gparted to format the whole hard drive ext4**, but backup anything you may have on there first. then try the install again. if you see any errors during the install take a pic of the screen and attach it here. I take it your windows was working ok before you tried ubuntu?
I dont quite understand what you mean, where should I write "admin - gparted"

---

### Post by sohlinux on 2010-11-13
> **Twixx said:**
> I want ubuntu as my OS, gonna get rid of windows 7

ok but you may want to keep your windows recovery partition if you have one, its up to you.  if you have the install cd no problem :)

---

### Post by Lancro on 2010-11-13
> **Twixx said:**
> I dont quite understand what you mean, where should I write "admin - gparted"

You need to open a terminal and then type:
```
sudo gparted
```

Then you will be using gparted tool to make your partitions.

---

### Post by sohlinux on 2010-11-13
> **Twixx said:**
> I dont quite understand what you mean, where should I write "admin - gparted"

on the live cd its in the menu - system  - admin - gparted

or via terminal type gksudo gparted

---

### Post by sohlinux on 2010-11-13
> **Lancro said:**
> You need to open a terminal and then type:
```
sudo gparted
```

Then you will be using gparted tool to make your partitions.

better gksudo gparted for graphical applications

---

### Post by Twixx on 2010-11-13
How can I open the terminal through this screen?
[IMG]http://i51.tinypic.com/30semwz.png[/IMG]

---

### Post by sohlinux on 2010-11-13
> **Twixx said:**
> How can I open the terminal through this screen?
[IMG][/IMG]

choose try ubuntu then you can get to the menu and terminal

---

### Post by Twixx on 2010-11-13
that's the thing, I cant do that ;S then the thing i showed in first post comes up

---

### Post by sohlinux on 2010-11-13
> **Twixx said:**
> that's the thing, I cant do that ;S then the thing i showed in first post comes up

download live gparted [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) then clean format the disk then try again

---

### Post by owise1 on 2010-11-13
you could also hit F4 and try another startup mode - could be the graphics card playing up.

---

### Post by owise1 on 2010-11-13
or you could try using the alternative install CD - see [https://help.ubuntu.com/community/GettingUbuntu](https://help.ubuntu.com/community/GettingUbuntu).

I suspect that once you get that live CD going you will not need to modify the HD setup as the installer will do that for you

---

### Post by sohlinux on 2010-11-13
if you have the same problem after formatting the disk you could try installing from a usb stick just in case your cd drive is at fault

also try the disk check utility which you can access from the live cd before the full boot up

---

