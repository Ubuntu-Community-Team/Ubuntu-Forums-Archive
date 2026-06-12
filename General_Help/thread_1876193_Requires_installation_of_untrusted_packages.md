---
title: "Requires installation of untrusted packages"
date: 2011-11-05
forum: General Help
---

### Post by rmjohnson144 on 2011-11-05
I just installed 11.10 and got a message saying there were updates.  When I clicked install, I get this error,"Requires installation of untrusted packages".  I haven't installed anything at all.  this is a fresh install.

I found an article suggesting to run:

```
sudo apt-get update
```

to update the packages.  but I can't find terminal anywhere on this computer?  I tried the software center and I get the stupid untrusted packages error again.

anyone know where terminal is located?  or how to install it manually?  I would hate to do a reinstall.

-=Mark=-
ps. the web laggs out horribly bad.  I have to restart firefox or even reboot to get it to come back.  sometimes those don't work and shut the system down and come back and it works.  I have no issues on any of my other compters, or if I dual boot to windows on this machine.  This is a gigabyte z68 motherboard with a realtek 8111E port.

---

### Post by LinuxFan999 on 2011-11-05
> **rmjohnson144 said:**
> I just installed 11.10 and got a message saying there were updates. When I clicked install, I get this error,"Requires installation of untrusted packages". I haven't installed anything at all. this is a fresh install.
 
I found an article suggesting to run:
 
```
sudo apt-get update
```
 
to update the packages. but I can't find terminal anywhere on this computer? I tried the software center and I get the stupid untrusted packages error again.
 
**anyone know where terminal is located?** or how to install it manually? I would hate to do a reinstall.
 
-=Mark=-
ps. **the web laggs out horribly bad**. I have to restart firefox or even reboot to get it to come back. sometimes those don't work and shut the system down and come back and it works. I have no issues on any of my other compters, or if I dual boot to windows on this machine. This is a gigabyte z68 motherboard with a realtek 8111E port.
Try searching for the terminal through the dash. Open the dash (Ubuntu button in the launcher) and type terminal.
 
Have you tried any other browsers?
What are the specifications of your computer?

---

### Post by BillyBoa on 2011-11-05
The terminal is very well concealed. Try ctrl-alt-T.
In any case maybe you have problem with your software sources. Try to change server to download the updates.

---

### Post by dFlyer on 2011-11-05
I believe you installed a ppa without it's key. This error usually shows up then this happens. What ppa's have you added?

---

### Post by rmjohnson144 on 2011-11-05
thanks BillyBoa, that got the terminal up for me.  The sudo apt-get update seemed to do the trick.  everything is fine again.  

-=Mark=-

---

