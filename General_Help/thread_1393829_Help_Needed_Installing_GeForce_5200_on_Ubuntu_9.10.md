---
title: "Help Needed Installing GeForce 5200 on Ubuntu 9.10"
date: 2010-01-29
forum: General Help
---

### Post by jackreisinger1511 on 2010-01-29
I am very new to Ubuntu and Linux in general (~3 days). I've just installed Ubuntu 9.10 on my desktop and attempting to enable Visual Effects. Everytime I try to enable any selection (Normal, Extra, etc) I get the following error message, "Desktop effects could not be enabled". I tried to work around this by installing a GeForce 5200 video card but I am still getting the same error. I did some Googling, other people said it was because both video cards are enable (which both of mine are, the onboard and PCI). I tried to blacklist the onboard with no success. Also there is no option to disable Onboard Video in the BIOS, the only option is to change Primary from Onboard to PCI and to change the memory size from 8mb to 1mb. 
 
Attached are my H/W specs, again I am very new to Linux so please let me know if you need any additional information. So far I've tried the following items:
 
1. Blacklisting the onboard video modules (e.g. blacklist agpgart & blacklist intel_agp)
2. Install NVIDIA drivers using GUI and using Envy
 
 
Thanks in advance. 
 
jack

---

### Post by jackreisinger1511 on 2010-01-29
I've also attached the video card information using sudo lshw -C video

---

### Post by jackreisinger1511 on 2010-01-30
Could someone please help, let me know if I'm not providing the correct information to trouble shoot this issue.

---

### Post by frankwakeman on 2010-01-30
Something here might be of use.  Works for me, despite other measures I've tried out since 8.10.

[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

---

### Post by SemiBuz on 2010-01-30
```
sudo apt-get install nvidia-glx-173
sudo nvidia-xconfig
sudo shutdown -r now
```

Have you done this ?

---

