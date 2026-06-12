---
title: "Virtualbox crashing"
date: 2012-03-20
forum: General Help
---

### Post by steveray100 on 2012-03-20
I installed virtualbox 4.1 from oracle through their website but it did not work poroperly. So I removed it and then installed the one available through the repository. I set up a virtual Windows machine and when I pressed START in Virtualbox I received this error:

(See the screenshots)


I then ran the command in terminal and this is what I got. I'm a noob , so I do not even know where to start. Should I just re-install Virtualbox?


steveray100@steveray100-desktop:~$ sudo modprobe vboxdrv
[sudo] password for steveray100: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
steveray100@steveray100-desktop:~$

---

### Post by Paddy Landau on 2012-03-21
The Repository version is an older one with an older license.

It is advised always to use the latest version from Oracle's website.

I suggest you deinstall Virtual Box. Install the one from Oracle (don't download the file, but add the PPA as instructed on [the Linux download page]("https://www.virtualbox.org/wiki/Linux_Downloads") under "Debian-based Linux distributions"). I suggest you also install the Extension Pack (download it from [the main download page]("https://www.virtualbox.org/wiki/Downloads")).

If Virtual Box still does not work correctly, start a new thread to ask about it.

---

