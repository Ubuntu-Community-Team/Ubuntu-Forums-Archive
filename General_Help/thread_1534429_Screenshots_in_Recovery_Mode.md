---
title: "Screenshots in Recovery Mode?"
date: 2010-07-19
forum: General Help
---

### Post by jedd999 on 2010-07-19
Im using 9.04 64-bit, is there a way to get screenshots in recovery mode? I have been searching around for a little while and havent been able to find anything. 
 
Help is greatly appreciated.

---

### Post by bodhi.zazen on 2010-07-19
After booting to recovery mode, enter the command

```
startx
```

This will start a gnome session , you can take screenshots from there.

Take care, you are running gnome as root. I would not do this with any regularity, but if that is what you need ...

Personally I boot a live CD and mount my Ubuntu partition in a chroot.

---

### Post by jedd999 on 2010-07-19
Thanks for the response. 
 
When I try to use startx, seems that the system will hard hang as soon as gnome opens (some message about an error during user switching)
 
Any links on good instructions for how I can mount my Ubuntu partition in a chroot? I am kindof a nub when it comes to this stuff :)
 
Thanks!

---

### Post by bodhi.zazen on 2010-07-19
What do you want a screen shot of exactly ?

---

### Post by jedd999 on 2010-07-19
I have some graphics-card based applications which need to be run in recovery mode (if they worked in a terminal in gnome that would be too easy :(). I need to get some screenshots of these applications. 
 
I tried to use a virtual machine, but that doesnt work because it needs to load the graphics card, and in the virtual machine it doesnt use the system hardware for the graphics (I think it just uses system memory), and I couldnt find a way to load the graphics card in the VM (I dont think its possible).

---

### Post by bodhi.zazen on 2010-07-19
OK, but why do then need to be run in recovery mode then ? can they not be run in a standard session ?

Just trying to get an idea of the project and the best way for you to obtain the information you need.

---

### Post by jedd999 on 2010-07-19
Honestly, I dont know why they wont just run in a standard environment... I wish they did because I would have been done by now! :D
 
I think it has something to do with some of the drivers that may load when GNOME loads, but I really cant be sure. 
 
Is there a way to SSH into a system in debug mode and be able to see everything that is going on in the system? 
 
I figure there must be some app which will allow you to take a screen capture in debug mode...

---

### Post by bodhi.zazen on 2010-07-19
Try running the application with a standard boot, but run it as root

```
gksu name_of_application
```

---

### Post by jedd999 on 2010-07-20
Still not there... :(

---

### Post by jedd999 on 2010-07-20
AH, I figured it out. 
 
Rather than using startx, I tried to use "init 2" after loading in debug mode, and the application seemed to "work". Though it wasnt working properly, it worked well enough for me to get the screenshots I needed. 
 
Thanks for the help!

---

### Post by bodhi.zazen on 2010-07-20
> **jedd999 said:**
> AH, I figured it out. 
 
Rather than using startx, I tried to use "init 2" after loading in debug mode, and the application seemed to "work". Though it wasnt working properly, it worked well enough for me to get the screenshots I needed. 
 
Thanks for the help!

Glad you got it sorted.

---

