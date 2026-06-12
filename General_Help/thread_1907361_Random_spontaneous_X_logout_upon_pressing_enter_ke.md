---
title: "Random spontaneous X logout upon pressing enter key"
date: 2012-01-11
forum: General Help
---

### Post by mvidberg on 2012-01-11
At some point in the last few months I started having a strange problem.  I am currently on ubuntu 11.10 with nvidia GT520 video card.  About once every hour or so as I'm working on my computer and I press the enter key (usually while typing something into firefox) my screen goes black and then I get forced logout from X-org.  This is very annoying as it means anything I was working on that wasn't saved I just lost.

Any suggestions on what log file I should be looking in for clues to solve this?

---

### Post by Pilot6 on 2012-01-11
This is caused by Nvidia drivers. I installed 295. No problems so far.

---

### Post by mvidberg on 2012-01-12
> **Pilot6 said:**
> This is caused by Nvidia drivers. I installed 295. No problems so far.
Where did you get 295?  Going to the nvidia site, the latest they have for 64-bit Linux is 290.10.

---

### Post by Pilot6 on 2012-01-12
[http://www.nvnews.net/vbulletin/showthread.php?p=2514702](http://www.nvnews.net/vbulletin/showthread.php?p=2514702)

---

### Post by mvidberg on 2012-01-25
Thanks for the link but I should mention that the beta driver doesn't seem to work for me.  After installing it X wouldn't start anymore.. the logs showed an error "Failed to initialize the NVIDIA kernel module".

I had to revert back to my previous settings (posting the method I used to revert in case anybody else has to do this).
Press CTRL-Alt-F2 to get to a shell login.  Then do the following:
sudo sh /path/to/NVIDIA-Linux-x86_64-295.09.run --uninstall
sudo apt-get --purge remove nvidia-*
sudo apt-get install nvidia-current
reboot

---

### Post by mvidberg on 2012-02-26
After eventually getting nvidia driver version 295.20 installed and working I thought the problem was fixed.

Ends up I am still experiencing it occasionally.  Any other ideas on what could be causing this?

---

### Post by THizzle7XU on 2012-02-27
I am also experiencing this as well on Ubuntu 11.10. I am running the latest 295 released Nvidia drivers. I usually experience it once soon after logging in for the first time. But not after that. I have auto-login enabled and I am using TwinView with two monitors with the same resolution if that helps at all. I also get the black screen after randomly hitting enter either in the terminal or Firefox, and I am logged out of my session and have to log back in. My card is an EVGA 570 GTX.

---

### Post by LRY on 2012-02-28
Ubuntu 11.10 32-bit
Nvidia [295.20]("http://www.nvidia.com/object/linux-display-ia32-295.20-driver.html") drivers for 8400M GS card (laptop)

Confirmed.  I'm not sure if pressing enter causes the random logouts, but once in a while (half to few hours) I'm logged out of X.  For the time being, I've updated to the previous version ([275.43]("http://www.nvidia.com/object/linux-display-ia32-275.43-driver.html")) for my card.

---

### Post by mvidberg on 2012-06-09
This problem seems to have gone away for me since I updated to Ubuntu 12.04.

---

