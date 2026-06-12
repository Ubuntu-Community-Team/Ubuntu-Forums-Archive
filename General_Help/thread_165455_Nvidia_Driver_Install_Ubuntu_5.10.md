---
title: "Nvidia Driver Install Ubuntu 5.10"
date: 2006-04-24
forum: General Help
---

### Post by jedimasterk on 2006-04-24
What a pain in the ... that was. I solved it though. After I installed the latest Nvidia drivers, I had to get out of xserver then sudo CC=gcc-3.4 sh NVIDIA......run. Not just sh NVIDIA ....run. Some how it had to be told to use gcc 3.4 rather than gcc 4.0. Now it works. The Nvidia installer has to rebuild the kernal first. They should make this less cumbersome than it is. With Suse 10 you just load the nvidia driver re-boot and 3d acceleration. Unless you have Google to rely on with questions, your out of luck. The included nvidia glx driver doesn't work. Or better yet do what PCLinux os does. Install it with the distro.8) . I hope it is way easier with Dapper Drake!!.

---

### Post by testube_babies on 2006-04-24
The latest 8756 drivers are in the Dapper repositories.  All you have to do to install them is:
```

sudo apt-get install nvidia-glx
```

---

### Post by izmaelis on 2006-04-24
It's not so hard to search for information  about how to install nvidia drivers in ubuntu forums too. [Here]("http://www.ubuntuforums.org/showthread.php?t=75074") you would find three ways how to install it.
And, btw, is it hard to install nvidia drivers using synaptic package manager? NO!

---

### Post by KillrBuckeye on 2006-05-10
I'm sorry, but as a Linux newb I must agree with the OP.  This driver installation process is an absolute nightmare!  Isn't Ubuntu supposed to be a "user-friendly" distro?  Sure, if you use hardware that was top-of-line 5 years ago you won't have any problems! (Ubuntu installed without a hitch on my Pentium III system with ancient 3D Rage II GPU).  

However, I have a 7900GT in my main rig which is ONLY supported by the latest nVidia driver release (8756), so the "easy" methods don't apply.  I can't even get X started without this driver installed, so everything I do is in text-mode and I need to have a 2nd computer with internet access sitting right next to me in order to search for and apply the fixes.  Hardly a convenient situation if you ask me.

After using method (2) in the link you provided, the driver actually installed using the nVidia installer, and I was able to start X.  However, once I rebooted, X wouldn't start!  So now it's 2 days and counting that I can't even get into X with my fresh Ubuntu install.  Having a wife and job only allows so much time to sit in front of a command prompt and type in commands I find on internet forums in a desperate attempt to get this thing working!  

Nonetheless, it's addictive and fun!  I like a challenge, but I have my limits.

---

### Post by tseliot on 2006-05-11
[QUOTE=KillrBuckeye]I'm sorry, but as a Linux newb I must agree with the OP.  This driver installation process is an absolute nightmare!  Isn't Ubuntu supposed to be a "user-friendly" distro?  Sure, if you use hardware that was top-of-line 5 years ago you won't have any problems! (Ubuntu installed without a hitch on my Pentium III system with ancient 3D Rage II GPU).[/QUOTE]
Blame Nvidia for that, not Ubuntu. If the driver were open source Ubuntu could include it by default.

[QUOTE=KillrBuckeye]However, I have a 7900GT in my main rig which is ONLY supported by the latest nVidia driver release (8756), so the "easy" methods don't apply.  I can't even get X started without this driver installed, so everything I do is in text-mode and I need to have a 2nd computer with internet access sitting right next to me in order to search for and apply the fixes.  Hardly a convenient situation if you ask me.

After using method (2) in the link you provided, the driver actually installed using the nVidia installer, and I was able to start X.  However, once I rebooted, X wouldn't start!  So now it's 2 days and counting that I can't even get into X with my fresh Ubuntu install.  Having a wife and job only allows so much time to sit in front of a command prompt and type in commands I find on internet forums in a desperate attempt to get this thing working!  

Nonetheless, it's addictive and fun!  I like a challenge, but I have my limits.[/QUOTE]
A quick fix have the X server up and running again.
```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "vesa" (instead of "nvidia").
Press CTRL+X to exit (save the file)

Then type:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

Then try one of my scripts:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

If you've got any questions, please post them here:
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by KillrBuckeye on 2006-05-11
I tried your script for Breezy, but it did not work.  It downloaded the installer and seemed to install okay, but it failed to start the X server.  The errors are:

(EE) Failed to load module "glx" (module does not exist, 0)
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.


To give a little more background, I am able to manually install the nVidia drivers myself using the 8756 installer package.  This will allow me to start up GDM just fine and everything appears to be good.  The problem is that when I restart, something changes and X can no longer start.  The error message says:

"Failed to initialize the NVIDIA kernel module!"

At this point, I can manually reinstall the driver and everything is fine again... What is going on?  I've even had some of my friends on IRC try to help me out, but they have run out of ideas.

EDIT:  Oops, sorry I posted this in the wrong thread.  I will try to delete and add to the other thread you mentioned.

---

### Post by KillrBuckeye on 2006-05-11
Intentional double-post:

I just wanted to let you know that your script, while it didn't fix my problem in one shot, seems to have resolved whatever conflict was causing me problems before!!!  Basically I had given up on your script, so I decided to manually reinstall the driver using the nVidia package.  Once I did this, I was able to reboot my computer and GDM and X started up okay!!!  Something in your script did the trick!  I am very grateful for your help!  I was just about to give up on Ubuntu (and maybe Linux in general). :D

---

### Post by tseliot on 2006-05-11
BTW There was a bug in my script (which I fixed).

---

