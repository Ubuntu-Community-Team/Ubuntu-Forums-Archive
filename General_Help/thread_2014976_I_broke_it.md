---
title: "I broke it"
date: 2012-07-02
forum: General Help
---

### Post by gishaust on 2012-07-02
I have been using ubuntu 12.04 for months and today I update the 
new skype. Then unity failed. I restarted the laptop and I get a purple screen and then the screen goes black and it stops. How 
do I get it working again?

---

### Post by stderr on 2012-07-02
Ok, a couple of possibilities. First - hardware failure - but that's quite unlikely, so we'll stick that possibility out the way for the time being. Second, and most likely by the sounds of things - a graphics driver update and/or kernel update. 

Ultimately, what will help us is knowing more about your laptop's hardware and a couple of log files. E.g., the command line output from:

```
lspci
```
```
less /var/log/Xorg.0.log
```
```
less /var/log/messages
```
```
less /var/log/syslog
```

To get to a state where you can run these and other commands, you'll need to boot your laptop to an operable state. Preferably, you do this with just your laptop. Worst-case, you do it via an Ubuntu CD. 

So, first thing's first: try to get a terminal. When your laptop boots and drops to a black screen, press Ctrl + Alt + F1. See if you get a username prompt. If not, use Alt + PrintScreen + R. Then Ctrl + Alt + F2. If by now you have a login prompt, you can login with your username and password, and run the above commands. If copying the output is a problem, we are probably most interested in the output of:

```
lspci | grep VGA
```
```
tail /var/log/Xorg.0.log
```
```
tail -n 10 /var/log/syslog
```

If you haven't managed to get a login prompt, reboot (try using [magic keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") if possible - Alt + PrintScreen + R,E,I,S,U,B). Then, at the boot prompt, choose the Recovery mode. See if you can get a login screen then.

If not, there are plenty of other routes to go down - fret not. Let us know how you get on.

---

