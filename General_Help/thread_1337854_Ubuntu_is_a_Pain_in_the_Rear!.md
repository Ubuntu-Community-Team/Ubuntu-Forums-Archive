---
title: "Ubuntu is a Pain in the Rear!"
date: 2009-11-25
forum: General Help
---

### Post by Mel Shepherd on 2009-11-25
I am about to delete Ubuntu 9.10 and return to 9.04. I have been trying to install VMWare Tools because I am using Ubuntu within Workstation 6.5. However, every person you think might have an answer from my Firefox research, are unable to help me.  I have followed this image 

[http://www.ubuntugeek.com/images/vt/4.png](http://www.ubuntugeek.com/images/vt/4.png)

However, when it got down to the C headers as to where the kernel directory files are stored, I couldn't find the directory that would be accepted. So, I tried downloading every file having to do with Kernel 2.6.31-15 generic, but it still doesn't work.  Then I read on the internet that VMWare doesn't accept VMWare Tools for this distro.  Is this true? 

Likewise, the audio doesn't work!  I have a Sound Blaster X-Fi PCIe card, and it worked fine with other distro's. Likewise, I'm unable to get flashplayer to install so as to use utube video's. Who created this monster? Why do you have to look for special drivers for those things you say this distro will handle?  

Sorry, for sharing my frustrations, but does anybody know how to handle these problems? Yes, I am somewhat of a newbie at mounting and installing programs from the synaptic package manager. First, I would like to get VMWare Tools installed, then my audio working, and then my video's working.

---

### Post by Sin@Sin-Sacrifice on 2009-11-25
```
apt-cache search vmware
``` or enter synaptic and type vmware in the search box and install the packages you need.

[This]("http://ubuntuforums.org/showthread.php?t=205449") for sound. One solution or another from that thread got sound working on every box I've had an issue with.

[This]("http://www.reddit.com/tb/9z2xk/") also has a bunch of info about installing flash. Although the ubuntu-restricted-extras package is probably the package you're looking for. It installs flash for 32 bit OS. If you have a 64 bit ubuntu you can Google "installing flash in ubuntu x64" to get a solution. I have a script that will do it for you if you need it (only for x64)

---

### Post by FXEF on 2009-11-25
Here's how to find the location of C header files.

```
find / -iname 'stdio.h'
```

Location will be the directory which stdio.h resides in.

Sound Blaster X-Fi PCIe card will require drivers to be installed.

Don't complain about bugs... help squash the bugs.

---

### Post by 3rdalbum on 2009-11-25
Your copy of Ubuntu is running as the guest OS? Then you don't need X-Fi drivers.

Check in Alsamixer to see if all your audio channels are turned up.

Flash Player is installed simply by installing the "flashplugin-nonfree" package from Synaptic. Before doing this though, make sure you remove all your previous attempts at installing it.

---

### Post by ibuclaw on 2009-11-25
Chances am that VMWare doesn't support the newer kernels yet. So probably nothing we can do to help you there yet.

---

### Post by Sin@Sin-Sacrifice on 2009-11-25
> **tinivole said:**
> Chances am that VMWare doesn't support the newer kernels yet. So probably nothing we can do to help you there yet.

It shows when I apt-cache search it in karmic x64... figured it had to work.

---

### Post by Cheesemill on 2009-11-25
Make sure you have all the correct packages installed that you need to compile kernel modules:
```
sudo aptitude install build-essential linux-headers-$(uname -r)
```

It sounds like you haven't installed the headers.

---

### Post by FXEF on 2009-11-25
> **Cheesemill said:**
> Make sure you have all the correct packages installed that you need to compile kernel modules:
```
sudo aptitude install build-essential linux-headers-$(uname -r)
```

It sounds like you haven't installed the headers.

 It's asking for C header files location not kernel headers. Now he may also need those linux-headers but that what the screen shot ask for.

---

