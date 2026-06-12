---
title: "No bootsplash screen."
date: 2010-09-10
forum: General Help
---

### Post by fragment137 on 2010-09-10
I was very impressed by the bootsplash screen when I've previously installed Ubuntu. This time, all I get is the Verbose boot, and no pretty boot screen before my login screen.

I've attempted to install usplash through Synaptic as well as even with apt-get install, but I keep getting errors relating to gdm and plymouth.

Something else as well, when I tried to install using Synaptic, I got a message saying that a whole shloo of applications were going to be removed, and some of them looked important.

I'm quite a newbie with Ubuntu, and any help would be appreciated

Terminal results from apt-get install usplash:

```
fragment@fragment-linux:~$ sudo apt-get install usplash
[sudo] password for fragment: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  usplash: Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
           Recommends: usplash-theme-ubuntu but it is not going to be installed or
                       usplash-theme
E: Broken packages
```

I would also like to mention that both initramfs-tools and upstart are installed. Update manager shows nothing for either of them,

---

### Post by fragment137 on 2010-09-10
Bump... Nobody can help me with this?

---

### Post by DomesDKG on 2010-09-10
Maybe try some of the solutions in the FAQ about bootup/plymouth.  I dunno if they will help your situation thought...

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by garvinrick4 on 2010-09-10
Install plymouth and remove usplash. Then open a terminal and:
```
sudo -i
``````
echo FRAMEBUFFER=y> /etc/initramfs-tools/conf.d/splash
``````
update-initramfs -u
```Now Hit ctrl and d same time to get out of root

Plymouth is used now for your splash screen.
This code makes your graphics drivers start before mountall package.

---

### Post by wajdigary on 2011-01-24
> **garvinrick4 said:**
> Install plymouth and remove usplash. Then open a terminal and:
```
sudo -i
``````
echo FRAMEBUFFER=y> /etc/initramfs-tools/conf.d/splash
``````
update-initramfs -u
```Now Hit ctrl and d same time to get out of root

Plymouth is used now for your splash screen.
This code makes your graphics drivers start before mountall package.
Great Job!

---

