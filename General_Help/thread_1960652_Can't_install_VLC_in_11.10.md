---
title: "Can't install VLC in 11.10"
date: 2012-04-17
forum: General Help
---

### Post by ben44b on 2012-04-17
Ubuntu says I have unmet dependancies but I can't seem to fix them. I tried the Fix Broken Packages in Synaptic and I tried "sudo apt-get install -f" but still nothing. 

Anyone know why?

Thanx.





```
bernie@ubuntu:~$ sudo apt-get install vlc -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1.1.12-2~oneiric1) but it is not going to be installed
       Depends: libqtgui4 (>= 4:4.5.3) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.10) but it is not installable
       Depends: libtar0 but it is not installable
       Depends: libva-x11-1 (> 1.0.12~) but it is not installable
       Depends: libxcb-keysyms1 (>= 0.3.8) but it is not installable
       Depends: libxcb-randr0 (>= 1.1) but it is not installable
       Depends: libxcb-xv0 (>= 1.2) but it is not installable
       Recommends: vlc-plugin-notify (= 1.1.12-2~oneiric1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.12-2~oneiric1) but it is not going to be installed

```

---

### Post by cortman on 2012-04-17
Hi, run

```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install -f
```

Please post any error output from any of these commands.

---

### Post by ben44b on 2012-04-19
Thanks for the reply.

I had a problem with my software sources and fixed it. I was then able to install VLC without any hitches.

Thanx.

---

