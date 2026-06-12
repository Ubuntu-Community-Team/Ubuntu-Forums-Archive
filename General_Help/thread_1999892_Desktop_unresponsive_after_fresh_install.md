---
title: "Desktop unresponsive after fresh install"
date: 2012-06-08
forum: General Help
---

### Post by Ninetailed on 2012-06-08
Running into a strange problem here. Have downloaded the 12.04 live image and installed to my HDD. Upon logging in, the desktop becomes unresponsive, with the mouse cursor freezing in place for minutes at a time. The system does not respond to any of the usual Ctrl-Alt-keypress combinations and a hard reset is required.

Curiously, this does not happen if I boot into the live image's environment rather than the one I installed.

In both cases, colord reports a crash. Not sure if that's relevant or what detail would be required.

System specs:
CPU: Intel G6950
Main Memory: 4GB DDR3 1333MHz
Graphics: nVidia GeForce 8800 GTS

Anyone have any idea what's going on? Searching the forum hasn't revealed anything promising.

---

### Post by wilee-nilee on 2012-06-08
> **Ninetailed said:**
> Running into a strange problem here. Have downloaded the 12.04 live image and installed to my HDD. Upon logging in, the desktop becomes unresponsive, with the mouse cursor freezing in place for minutes at a time. The system does not respond to any of the usual Ctrl-Alt-keypress combinations and a hard reset is required.

Curiously, this does not happen if I boot into the live image's environment rather than the one I installed.

In both cases, colord reports a crash. Not sure if that's relevant or what detail would be required.

System specs:
CPU: Intel G6950
Main Memory: 4GB DDR3 1333MHz
Graphics: nVidia GeForce 8800 GTS

Anyone have any idea what's going on? Searching the forum hasn't revealed anything promising.

Have you updated the OS, and checked the additional drivers app?

---

### Post by Ninetailed on 2012-06-08
> **wilee-nilee said:**
> Have you updated the OS, and checked the additional drivers app?

I have updated by switching to a virtual terminal pre-login and running `sudo apt-get upgrade`. The graphical environment is not responsive enough to run the additional drivers app; is there a command line version?

---

### Post by kaldor on 2012-06-08
> **Ninetailed said:**
> I have updated by switching to a virtual terminal pre-login and running `sudo apt-get upgrade`. The graphical environment is not responsive enough to run the additional drivers app; is there a command line version?

Yep. You can either install the driver from the repos (nvidia-current package) or use Jockey.

```
jockey-text --list
```

Then, when you get the list: 

```
jockey-text --enable=yourdriver
```

---

### Post by wilee-nilee on 2012-06-08
> **Ninetailed said:**
> I have updated by switching to a virtual terminal pre-login and running `sudo apt-get upgrade`. The graphical environment is not responsive enough to run the additional drivers app; is there a command line version?

Not sure graphic stuff is out of my area, but try a nomodeset login using this link, or the unity 2d from the login in choices as well.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

My guess is that the nvidia card is the problem here.

---

### Post by Ninetailed on 2012-06-08
> **kaldor said:**
> Yep. You can either install the driver from the repos (nvidia-current package) or use Jockey.

```
jockey-text --list
```Then, when you get the list: 

```
jockey-text --enable=yourdriver
```
 
nvidia_current was already enabled, so I then enabled nvidia_current_updates, rebooting to be absolutely sure it took effect. 

This appears to have resolved the issue. Thank you both for your patience in dealing with what I am sure is a common new-user pitfall.

---

### Post by Maju on 2012-06-10
I have the same problem: now and then, for no apparent reason, when running the most unrelated programs (can be anything, really) it freezes and can only be solved with hardware restart - no response from any keys' combo and although the mouse can be moved on screen it does not seem able to effectively click on anything. 

Specs: Emachine EL 1200 with AMD Athlon 64 CPU. NVidia-something graphics card but the driver is not installed because of the bug that destroys Compiz (I understand: I fear installing and going back to that disaster after I first installed and upgraded Precise, which is going to get the nickname of Rather Imprecise, what a mess!)

---

