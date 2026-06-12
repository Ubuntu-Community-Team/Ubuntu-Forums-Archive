---
title: "Problems with RaLink 3090 Wireless Card"
date: 2011-03-21
forum: General Help
---

### Post by Crabaroni on 2011-03-21
I've been having problems with this card for 2 weeks. I make a directory with an empty .dat file named RT2860STA and Rt3090STA and neither work. I stumbled upon this thread [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498). This seems like it will work, but I don't understand some of the steps. Can someone explain to me exactly what to type into terminal or do to a file because I'm totally lost. I am a complete linux beginner.

---

### Post by Crabaroni on 2011-03-21
What does he mean by compiling, and installing things via synaptic?
What does he mean by "entering DPO_..." is that the actually driver file? What is sudo make and sudo make install, I tried these but they require a "target"? How do I add blacklist rt2800pci at the end of /etc/modprobe.d/blacklist.conf (as root)? And open (as root) file /etc/modules and add: rt3390sta? I changed all of the values to y instead of n, but that is all I could manage. If anybody could help that would be great. I accidentally uninstalled windows while partioning Fedora 14 which would stop at the last second of  installation and crash, so I switched to Ubuntu. I can't use my computer for browsing the internet right now, so I have to type this in my school library with a limited amount of time.

---

### Post by Crabaroni on 2011-03-22
Anyone?

---

### Post by bkratz on 2011-03-22
> **Crabaroni said:**
> What does he mean by compiling, and installing things via synaptic?
What does he mean by "entering DPO_..." is that the actually driver file? What is sudo make and sudo make install, I tried these but they require a "target"? How do I add blacklist rt2800pci at the end of /etc/modprobe.d/blacklist.conf (as root)? And open (as root) file /etc/modules and add: rt3390sta? I changed all of the values to y instead of n, but that is all I could manage. If anybody could help that would be great. I accidentally uninstalled windows while partioning Fedora 14 which would stop at the last second of  installation and crash, so I switched to Ubuntu. I can't use my computer for browsing the internet right now, so I have to type this in my school library with a limited amount of time.


What he/she wants you to do is go to synaptic and search for and [COLOR="DarkOrange"]install[/COLOR] those packages, not compile them. Synaptic is under the menu's  ( system>>administration>>synaptic package manager ).   The statement referring to DPO...is the folder you downloaded from the website (that is it's name). The easiest is to put it on the desktop. He/she then wants you to navigate (in the terminal) to the desktop and do the steps mentioned, in the order mentioned.

---

### Post by Crabaroni on 2011-03-25
Thank you very much. I was totally lost on this. I will give it a try right now.

---

