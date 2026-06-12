---
title: "Location of X Display"
date: 2010-04-20
forum: General Help
---

### Post by jmhecker on 2010-04-20
[FONT=courier new,monospace]On Ubuntu (as with 99% of other Linux  distros), CTRL-ALT-F7 brings you to your X display on tty7 (:0)...is  there any way for me to get the display to appear on tty2 or tty3  instead of 7? 

I ask because my ubuntu box is a media server running XBMC.  XBMC  has some 'flaws'...one of which is screen refreshing during certain  tasks (other than watching a video)...the easiest way to get it to kick  back into gear is to switch to a terminal, then back to the X  display...not that big of a deal really..but the problem lies in the  fact that the remote I use for the computer (simple USB IR Remote  grabbed off of eBay) has buttons programmed for CTRL-ALT-F[1,2,3,4].   So, if I could get X to appear in CTRL-ALT-F2 for instance, I could  easily switch back and forth without having to get up to walk to the  keyboard.

Any thoughts if this is possible?[/FONT]

---

### Post by dcstar on 2010-04-21
> **jmhecker said:**
> [FONT=courier new,monospace]On Ubuntu (as with 99% of other Linux  distros), CTRL-ALT-F7 brings you to your X display on tty7 (:0)...is  there any way for me to get the display to appear on tty2 or tty3  instead of 7? 

I ask because my ubuntu box is a media server running XBMC.  XBMC  has some 'flaws'...one of which is screen refreshing during certain  tasks (other than watching a video)...the easiest way to get it to kick  back into gear is to switch to a terminal, then back to the X  display...not that big of a deal really..but the problem lies in the  fact that the remote I use for the computer (simple USB IR Remote  grabbed off of eBay) has buttons programmed for CTRL-ALT-F[1,2,3,4].   So, if I could get X to appear in CTRL-ALT-F2 for instance, I could  easily switch back and forth without having to get up to walk to the  keyboard.

Any thoughts if this is possible?[/FONT]

It should be able to be done with minor changes to some configuration files.

This will change the number of PTTYs:
```
sudo dpkg-reconfigure console-setup
```

Starting the X Server/GDM on a different TTY to 7 should be a matter of searching for the appropriate file in the /etc tree.

---

