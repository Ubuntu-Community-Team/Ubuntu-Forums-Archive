---
title: "How to install Nvidia 185.18.36 (stable) or 190.25(beta) drivers on Jaunty"
date: 2009-10-28
forum: General Help
---

### Post by gordong11 on 2009-10-28
For i386, 32-bit only.

I spent four hours cleaning up errors and get my rig working again because I downloaded and installed Nvidia drivers from Nvidia.com and followed their directions. I would keep the 180 drivers, but if you must upgrade....

DO NOT DOWNLOAD THE NVIDIA-Linux-x86-185.18.36-pkg1.RUN FILE AND EXIT GDM TO INSTALL. YOU WILL BE IN HELL TRYING TO GET EVERYTHING WORKING CORRECTLY AGAIN.

FOR JAUNTY FOLLOW THESE INSTRUCTIONS AND THERE WILL BE NO INSTALL ISSUES:

check kernel and dependencies in the terminal:

sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)

1. OPEN TERMINAL:

sudo sh -c "echo 'deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"

AND 

sudo sh -c "echo 'deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"

2.  IN TERMINAL: Import the GPG key:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767

3. INSTALL DRIVERS:

185.18.36 STABLE: 
sudo apt-get update && sudo apt-get install nvidia-185-modaliases nvidia-glx-185

OR

190.25 BETA:
sudo apt-get update && sudo apt-get install nvidia-190-modaliases nvidia-glx-190

4. REBOOT

If there is an error, you can re-activate the version 180 drivers from System > Administration > Hardware Drivers.

I hope this helps save time and effort. see the attached acreenshot for proof it is installed and working on rig.

---

### Post by DeMus on 2009-10-28
[COLOR="Silver"]From the website: [_nVidia drivers_]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-190/") I downloaded these files suited for Jaunty. I have the 64-bits OS so I used the 64-bits files. If you have a 32-bits OS use the 32-bits files.

```
[COLOR="Silver"]nvidia-190-kernel-source_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-libvdpau_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-modaliases_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-glx-190_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb[/COLOR]
```

Download them to your download folder. Open Nautilus and you'll see 4 .deb files. Double-click them in the order mentioned above and they will be installed automatically using gdebi.
Then after a reboot all was fine and I now have the latest nVidia proprietary driver.[/COLOR]

I retract my post since I just found out the website U am referring to has been changed. The files listed there ar for the new Karmic release of Ubuntu and I can not say if they also work for Jaunty.

---

### Post by falconindy on 2009-10-28
Sorry, but this is blatant misinformation. Tinivole wrote a [comprehensive guide]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185") to compiling and installing the 185 (and 190) drivers manually with the run packages from the nvidia website. I followed these directions a few weeks ago with fantastic results. Your misinformation only serves as a detriment to the community.

---

### Post by DeMus on 2009-10-28
> **falconindy said:**
> Sorry, but this is blatant misinformation. Tinivole wrote a [comprehensive guide]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185") to compiling and installing the 185 (and 190) drivers manually with the run packages from the nvidia website. I followed these directions a few weeks ago with fantastic results. Your misinformation only serves as a detriment to the community.

Why is that? I used it a couple of times and it works fine. What is the problem?

---

### Post by gordong11 on 2009-10-28
> **falconindy said:**
> Sorry, but this is blatant misinformation. Tinivole wrote a [comprehensive guide]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185") to compiling and installing the 185 (and 190) drivers manually with the run packages from the nvidia website. I followed these directions a few weeks ago with fantastic results. Your misinformation only serves as a detriment to the community.

Dude,

try it..you will see..perhaps if you do all that work correctly it will work fine.....but it didnt for me....there are a ton of steps to foul up.

When i exited gdm via sud /etc/init.d gdm stop, It errored or was taking longer than 20 minues..i gave up. tried again..this time from contraol+alt+f1 the exit gdm this worked. when i rebooted, i got error after error.

The info i posted worked fine for me....and can be reversed easily. ALL APPS WORKING properly as far as i can tell.

There is more than one way to do it........most peeps will be thanking me for saving them hours of time. see attachment.

---

### Post by psycho5 on 2009-10-28
How can there exist so many ways to do the simplest of things? People should stop posting Howto's over and over again with their own little flavor to them, it just confuses the newbies and then they run into their own troubles, which in turn creates more threads with similar problems. A sticky howto guide exists for nvidia and ati.

---

### Post by djurny on 2009-10-28
not to be the next one to offer another solution; but what's wrong with the nvidia installer ..from nvidia?
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
clicky to the one your want, press agree & download, go to the downloaded folder and simply ```
sudo sh ./NVIDIA-Linux-x86-190.42-pkg1.run
```, follow the onscreen instructions and reboot?
worked for me every time.. (well at least until a new kernel image or initrd came along.. i'd have to reinstall the nvidia drivers as well due to them not being in the initrd image after update..:))

---

### Post by DeMus on 2009-10-28
> **psycho5 said:**
> How can there exist so many ways to do the simplest of things? People should stop posting Howto's over and over again with their own little flavor to them, it just confuses the newbies and then they run into their own troubles, which in turn creates more threads with similar problems. A sticky howto guide exists for nvidia and ati.

[COLOR="Silver"]The thing is there are a lot of ways to do something. What works for one doesn't have to work for another.
I personally had problems using the sh nVidia....run file command in a terminal so I looked for another way. I found it and described it in my first post in this thread.
The way the OP did it could also be a good way, he includes a new repository into his source list file. That way he will be warned whenever there is a new update. The problem here is the driver is already an older one.
I am happy with my way and if others like to use this way they are happy to do so. It's pretty easy and it works.[/COLOR]

I retract my posts in this threads. I just found out the site I referred to has been changed. The files mentioned there are for the new Karmic release of Ubuntu and I can not say they also work on Juanty.

---

### Post by falconindy on 2009-10-28
> **DeMus said:**
> Why is that? I used it a couple of times and it works fine. What is the problem?
My reference to misinformation is that the OP seems to be giving the implication that the debs are a better choice. I don't think so. He botched his install because he didn't take the time to look at the **numerous** guides on this site detailing the steps necessary to compile and install the .run package. Installing the debs is a fine option, but leaves open the possibility of apt doing something strange behind your back. I might be paranoid, but as I learn more and more about Linux, I trust system automation less and less.

In addition, I prefer tinivole's method because its cleaner: ripping out all evidence of the old drivers and reforming the xorg.conf. Compiling the drivers on my own hardware is also appealing to me given how tedious the overall process seems -- this removes a level of complexity (build-deps are easily met). However, his method doesn't give you quite as obvious of a rollback strategy if it turns out you're having issues with the new drivers.

Being gung-ho about updates isn't something you can always get away with in Linux. Especially when they're unsupported for your distro. Understanding the process and reasons behind what you're doing is crucial. Not only will it make your life easier the next time you want to do something similar, but that knowledge will prove useful if/when you brick your system.

[QUOTE=gordong11]Dude,

try it..you will see..perhaps if you do all that work correctly it will work fine.....but it didnt for me....there are a ton of steps to foul up.

When i exited gdm via sud /etc/init.d gdm stop, It errored or was taking longer than 20 minues..i gave up. tried again..this time from contraol+alt+f1 the exit gdm this worked. when i rebooted, i got error after error.[/QUOTE]
Sounds like you tried to install the new drivers on top of the old ones. You openly admit you didn't know what you were doing. What did you expect?

---

