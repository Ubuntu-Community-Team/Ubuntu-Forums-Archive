---
title: "Can't install nvidia 190 on Karmic"
date: 2010-05-16
forum: General Help
---

### Post by gamblor01 on 2010-05-16
Hi folks,

I just recently upgraded from Jaunty to Karmic and now I can't seem to get the nvidia drivers to work properly.  It originally came up in low graphics mode and said that the 190 driver was installed, but it didn't work properly so I disabled it.

After rebooting, the 190 driver will never properly activate.  I tried launching jockey-gtk and it tells me to see /var/log/jockey.log which shows:

```

2010-05-16 08:54:58,054 DEBUG: Installing package: nvidia-glx-190
2010-05-16 08:54:58,778 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting

```I wasn't able to get the 185 drivers either until I did a manual apt-get install nvidia-glx-185.  Then it eventually worked and nvidia-xconfig got my xorg.conf updated and correct.  So now the 185 drivers are installed (though jockey-gtk does NOT show those drivers in green -- it doesn't think that I have any of the drivers enabled so all of the little bubbles show up as grey).  The 185 drivers are definitely installed though (185.18.36 to be exact) and Compiz is enabled, desktop effects are on, etc.

Any idea what is up with this?  Why doesn't jockey show the drivers that are installed and more importantly, how come I cannot install the 190 drivers?  I tried doing it via apt but this is what it tells me:

```

$ sudo apt-get install nvidia-glx-190
[sudo] password for bdmayes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-190 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-190 has no installation candidate

```I don't usually install via synaptic, but when I load that up and search for "nvidia" packages, the 190 module isn't listed anywhere in there.  The only thing related to 190 that is listed is nvidia-190-modaliases (which is currently installed).  Am I missing something in /etc/apt/sources.list that prevents me from install the 190 version?

---

### Post by lidex on 2010-05-16
I don't think there is a 190 version. I see 96, 173, 185, and 195. Unless you can find a ppa with 190, you'll need to use one of those.

Edit:
Here we go. PPA info 190.xx
[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html]("http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html")

---

### Post by gamblor01 on 2010-05-16
Cool thanks!  I was trying to install the 190 version instead of 195 because that was the latest that jockey gave me but I'll gladly install the 195 drivers instead!

I followed the instructions in the link that you gave me and things didn't go smoothly at first.  The install of the nvidia-195-glx package failed, and when I tried to install manually with dpkg -i (using the file in /var/cache/apt/archives) I got a similar error.  It appears that the 185 drivers were conflicting somehow, so I just ran "sudo apt-get autoremove" and it took care of the 185 package that was no longer necessary.  After that the 195 drivers installed perfectly, I rebooted, and I'm up and running:

```

bdmayes@ubuntubox:~$ nvidia-settings -q NvidiaDriverVersion

  Attribute 'NvidiaDriverVersion' (ubuntubox:0.0): 195.36.15

```
Thanks for the help!!!  :)

---

