---
title: "PiViTi video editor won't start - complaining about GTK+ Python bindings"
date: 2011-06-11
forum: General Help
---

### Post by darthpenguin on 2011-06-11
Hi Guys, I'm running Ubuntu 10.04 on my laptop (11.04 made the system heat up too much and the fans wouldn't stop running, so I downgraded and upgrading the system is not a viable solution to this problem). I added the PiViTi ppa and installed to most recent version so I can do some simple video editing. But when I try to start the app I get this error message (see also attached screenshot) "You do not have a recent enough version of the GTK+ Python bindings (currently 2.17.0). Install a version of the GTK+ Python bindings greater or equal to 2.18.0."

I assume I need to install something but I don't know what. I've already run "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade" but everything was up to date. I'm not upgrading to 10.10 or 11.04 so am I SOL here or can I just add a Python ppa or something?

Thanks.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **darthpenguin said:**
> Hi Guys, I'm running Ubuntu 10.04 on my laptop (11.04 made the system heat up too much and the fans wouldn't stop running, so I downgraded and upgrading the system is not a viable solution to this problem). I added the PiViTi ppa and installed to most recent version so I can do some simple video editing. But when I try to start the app I get this error message (see also attached screenshot) "You do not have a recent enough version of the GTK+ Python bindings (currently 2.17.0). Install a version of the GTK+ Python bindings greater or equal to 2.18.0."

I assume I need to install something but I don't know what. I've already run "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade" but everything was up to date. I'm not upgrading to 10.10 or 11.04 so am I SOL here or can I just add a Python ppa or something?

Thanks.

Does this problem happen on the other editors available as well? Scroll down this list to install a few of the alternatives:

```

sudo apt-get install kdenlive kino openshot winff avidemux

```

---

### Post by darthpenguin on 2011-06-11
Am I to try these for troubleshooting purposes? Or are you suggesting I actively switch to an alternative video editor? I've tried some of these suggested software packages on other systems before and I was never impressed with them.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **darthpenguin said:**
> Am I to try these for troubleshooting purposes? Or are you suggesting I actively switch to an alternative video editor? I've tried some of these suggested software packages on other systems before and I was never impressed with them.

Yes. I would like to know if it is related to this specific editor or not on your system.   I use it all the time, with no problems.. If you have the same problem with other editors, then you have system config issue.

---

### Post by linuxinstalledfromhdd on 2011-06-11
Also here are a few others I can recommend:

[http://cinderbox.net/2011/03/13/top-5-linux-video-editor-software/](http://cinderbox.net/2011/03/13/top-5-linux-video-editor-software/)

---

### Post by darthpenguin on 2011-06-11
No way. VideoLAN has an editor? Awesome. I installed it but when I try to launch I get this error in the terminal:

"vlmc: error while loading shared libraries: libvlc.so.5: cannot open shared object file: No such file or directory"

...but I guess that's a different problem.

I installed OpenShot and it opens just fine.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **darthpenguin said:**
> No way. VideoLAN has an editor? Awesome. I installed it but when I try to launch I get this error in the terminal:

"vlmc: error while loading shared libraries: libvlc.so.5: cannot open shared object file: No such file or directory"

...but I guess that's a different problem.

I installed OpenShot and it opens just fine.

I'm running 10.10 and it installs with this:
```

sudo add-apt-repository ppa:webupd8team/vlmc 
sudo apt-get update 
sudo apt-get install vlmc frei0r-plugins

```So you tried that and you are getting a missing dependency? 

Do you have all your repositories enabled in synaptic package manager?

BUMP

---

### Post by darthpenguin on 2011-06-27
I ended up installing Ubuntu 11.04 on another machine (not my laptop). The system runs smoothly and I can use the latest PiViTi. I'll just be doing my video editing there. (^_^)

---

