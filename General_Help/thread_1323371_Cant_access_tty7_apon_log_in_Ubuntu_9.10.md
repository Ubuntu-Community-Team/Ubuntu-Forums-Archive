---
title: "Cant access tty7 apon log in Ubuntu 9.10"
date: 2009-11-11
forum: General Help
---

### Post by IGM0937 on 2009-11-11
I don't know what's going on... Im an absolute Ubuntu noob but ill try to explain it to the best of my ability...

I had Ubuntu since 8.10 and It does what I want it do with some problems here and there but it was all mostly fixed with each update. I recently updated to 9.10 but after a few miss clicks I had to reinstall Ubuntu from scratch and I have to set up 9.10 all over again.

One day I was trying to load into Ubuntu and then all of a sudden I get a command line from tty1? I doesnt show me any sort of GUI. I should be getting the Login Screen but it shows me the tty1 login version instead. I tried to access tty7 by pressing Ctrl+Alt+F7 but it dont work... it works for all tty1 to tty6 but it wont work for any others.... ESPECIALLY the GUI one tty7!

I can log into my account via tty1 but i don't know what to do then.. I don't remember what I have done to make this happen? Can someone help get it back to normal... Re-installation at this moment isnt an option since I dont have 20GB available for back up and I don't have any spare CD's for an Ubuntu ISO.

---

### Post by IGM0937 on 2009-11-12
Anyone wanna help me?

---

### Post by AeroCross on 2009-11-12
Well, you might wanna try starting a session or starting the X server from there.

When you log in, try a startx or gnome-session commands. Post back the outputs.

Perhaps is some corruption with your graphic drivers, preventing you from starting the X Server.

---

### Post by IGM0937 on 2009-11-12
> **AeroCross said:**
> Well, you might wanna try starting a session or starting the X server from there.

When you log in, try a startx or gnome-session commands. Post back the outputs.

Perhaps is some corruption with your graphic drivers, preventing you from starting the X Server.

THx for the reply.

I have started xserver when i logged into the command line. After I run it, it says that there is no monitor available. Now that I think of it, I did mess around with the Monitor settings since I was trying to get my monitor settings sorted for my 24" monitor. I used it on 9.04 and after I had to reinstall to 9.10 the OS didnt recognize my monitor like 9.04 did.

I should really be asking how to restore my default monitor settings?

---

### Post by wojox on 2009-11-12
Try:

```
xrandr --output default --mode 1024x768 --rate 75
```

---

### Post by IGM0937 on 2009-11-12
> **wojox said:**
> Try:

```
xrandr --output default --mode 1024x768 --rate 75
```

Tried that... I logged in as SuperUser and returns with something along the lines of "no monitor found".. im sorry if i forget but I have to switch between OS and i just forget... I can go back and check if it's needed.

---

### Post by AeroCross on 2009-11-13
Weird. In my experience, I've had better monitor support in 9.10 than in 9.04, especially with dualscreen (without nVidia, from an Intel-Powered Laptop).

If you were messing with the monitor settings, your XOrg config file must be screwed up. The command you might be looking for could be:

sudo dpkg-reconfigure -phigh xserver-xorg

It worked for me in 9.04, dunno if here. It enables you to set you X config correctly.

---

### Post by gatordude on 2009-11-13
I tried that for my problem (almost the same problem) and it did not work for me. (using 9.1)

> 
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by IGM0937 on 2009-11-13
-- post deleted --

---

### Post by IGM0937 on 2009-11-13
> **AeroCross said:**
> Weird. In my experience, I've had better monitor support in 9.10 than in 9.04, especially with dualscreen (without nVidia, from an Intel-Powered Laptop).

If you were messing with the monitor settings, your XOrg config file must be screwed up. The command you might be looking for could be:

sudo dpkg-reconfigure -phigh xserver-xorg

It worked for me in 9.04, dunno if here. It enables you to set you X config correctly.

I tried it and I though it worked since after I typed it returned nothing to which I thought it worked... so i reboot and it actually did nothing. I till get tty1 login screen and when i switch to tty7 it looks like the boot process stopped half way... its obviously something wrong with the drivers... is there a was to reinstall them from the tty1 command line?

---

### Post by AeroCross on 2009-11-13
Yeah, by apt-get install - what drivers does your PC uses?
Also, you can try xterm -- :0 or :1 - see what happens. And if nothing productive happens, try reinstalling your drivers (perhaps you should sudo apt-get remove package --purge then reinstall them.

---

### Post by IGM0937 on 2009-11-14
Anyway... I fixed it... As I suspected, I have had problems with the display, but it was the xorg.conf file that was corrupt...

All I did is went into /var/X11/ and replaced the xorg.conf with a diffrent version fond in the same folder and presto!

I have had expert help!

---

