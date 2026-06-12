---
title: "Server vs Desktop ? (was Unable to boot 9.10 without a screen attached )"
date: 2010-03-14
forum: General Help
---

### Post by houldsworth1 on 2010-03-14
I have Ubuntu 9.10 installed on an old Gateway desktop. It is running a system called Jira using a Tomcat web server, so 99% of the time access is thorugh the web browser. For the rest of the time I access it remotely using TightVNC.
 
This works great so far but the system will not boot if I remove the screen (which I need to do since it is in the way). I have tried several remedies suggested by folks on this forum but none of them have worked. So my question is this...
 
a. If I uninstall and reinstall using Ubuntu Server edition (32-bit) will the system boot without the screen?
 
b. Assuming the above will work - can I still access the machine directly using TightVNC (I presume not since that needs the graphics setup). If not, how do I connect to the machine remotely?
 
Thank you!

---

### Post by Brandon Williams on 2010-03-16
There should be absolutely no need to reinstall to clear up this problem. What have you tried so far? It should be enough to change the value for GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub (it should be an empty string) and to change /etc/X11/default-display-manager (it should be empty). You'll need to run 'sudo update-grub' after changing the config. These two changes are enough to make it work for me, so if they aren't enough, it may be the case that your computer's bios is prevent the boot and/or some other config step that is specific to the computer will be required. In other words, if the two steps that I suggest aren't enough, then reinstalling with Ubuntu Server might not do the trick either. You're better off continuing your investigation to figure out what the specific problem is.

As for using VNC ... that should be no problem. The tightvncserver package depends upon everything that is specifically required to run enough of X for vnc to work. You'll need to install more apps to get your desktop environment, but be careful with what you select to ensure that you don't override the above suggested changes (for example, don't install ubuntu-desktop or gnome-desktop-environment; install gnome-core and the specific additional apps that you need).

---

### Post by houldsworth1 on 2010-03-16
> **Brandon Williams said:**
> There should be absolutely no need to reinstall to clear up this problem. What have you tried so far? 
 
My previous post can be found here [http://ubuntuforums.org/showthread.php?t=1412565](http://ubuntuforums.org/showthread.php?t=1412565) and I followed all of the advice posted there including creating an xorg.conf file.  
 
There is also a screen shot there of what happens when I take the screen off and reboot - it definately ends up in a "GNU GRUB screen" so I am hopeful that it is not the machines BIOS.  
 
If I get time tonight I will give this a shot and let you know the results.  If it does my wife will be very happy because the machine is under her desk.
 
Thanks!

---

### Post by houldsworth1 on 2010-03-16
OK...and the early results are in and...<drum roll>...
 
The machine will now boot without the screen attached, which is good.  Instead of starting the GUI it drops to a login prompt and I can log in and access the machine using command lines.  
 
The problem now is...I don't know how to connect to the machine remotely when it is in this mode.
 
Using TightVNC doesn't connect and neither does using Putty SSH.
 
So if you know a way to access the machine and get the log in prompt from a remote computer then I am all the way there.
 
Thanks for getting me this far!

---

### Post by dcstar on 2010-03-16
> **houldsworth1 said:**
> OK...and the early results are in and...<drum roll>...
 
The machine will now boot without the screen attached, which is good.  Instead of starting the GUI it drops to a login prompt and I can log in and access the machine using command lines.  
 
The problem now is...I don't know how to connect to the machine remotely when it is in this mode.
 
Using TightVNC doesn't connect and neither does using Putty SSH.
 
So if you know a way to access the machine and get the log in prompt from a remote computer then I am all the way there.
 
Thanks for getting me this far!

I will assume that you have no network connectivity in this mode when it boots, is that correct?

If that is the case, manually edit the /etc/network/interfaces file with all the correct info and then see if you can connect after a reboot.

---

### Post by houldsworth1 on 2010-03-16
> **dcstar said:**
> I will assume that you have no network connectivity in this mode when it boots, is that correct?
 
If that is the case, manually edit the /etc/network/interfaces file with all the correct info and then see if you can connect after a reboot.
 
Hmmm...you could be onto something here.  The network connector is a USB wireless thing.  Once I login I can start the web server on it and access it from other machines - so I am not sure when the connector driver loads.  But even once it is logged on and the web server can be accessed I still can't get access to it using putty.

---

### Post by houldsworth1 on 2010-03-16
Ahh!  Found it.  I needed to install SSH.
 
Might sound obvious but I'm still new :)
 
Thanks!

---

