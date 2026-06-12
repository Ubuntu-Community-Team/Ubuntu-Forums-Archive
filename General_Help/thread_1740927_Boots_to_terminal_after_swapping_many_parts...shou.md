---
title: "Boots to terminal after swapping many parts...should I just start over?"
date: 2011-04-27
forum: General Help
---

### Post by bmtphoenix on 2011-04-27
This is going to be an uber-noob question, but...

Installed Ubuntu 10.10 on a thrown together system for use as an HTPC with XBCD.  Everything was working beautifully until the PSU died, taking the board with it.  So, I've now got my old install of Ubuntu with XBCD and lots of stuff that I would rather not have to copy around, and a completely new set of components.

Ubuntu loads to the command line now instead of the desktop GUI, or XBCD.  I am completely clueless when it comes to the command line, so here is my question: will I spend less time copying all the stuff off that HDD (hours at least), or is there some way to repair the install that I have?  Also, am I likely to run into goofy issues down the road where I will have wished I just reinstalled from scratch?  If it makes more sense to try to repair this install, where do I go for information on that?

Thanks in advance for the help.

Update: I may be confused on what the actual problem is.  I plugged the HDD into the wife's Windows 7 machine to start looking at transferring files, and it booted into XBCD...

---

### Post by bmtphoenix on 2011-04-27
Booted fine off a Live USB, so I know it's compatible.  The board/CPU/GPU is a MSI E350IA-E45, if that matters.

---

### Post by Dutch70 on 2011-04-27
I don't know anything about XBCD, but as far as Ubuntu...

If you're getting to a command prompt, try typing...
```
sudo startx
```

If not, then try either (Cntl+Alt+F1) and/or (Cntl+Alt+F7) to get to a command prompt. Then try the above command.

If you get to a GUI, update your system.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by WorMzy on 2011-04-27
> **Dutch70 said:**
> I don't know anything about XBCD, but as far as Ubuntu...

If you're getting to a command prompt, try typing...
```
sudo startx
```

No need for sudo there, startx should be run as a normal user. :)

You're probably thinking of gdm, which does need to be started as root:
```
sudo /etc/init.d/gdm start
```

---

### Post by bmtphoenix on 2011-04-27
XBCD = XBMC + Tired.  Sorry about that.

Anyway, actually got it going by hitting SHIFT and doing a recovery console, then installing the offered driver.  That got me into the GUI, but unfortunately I'm still getting a "AMD Unsupported Hardware" watermark and just overall crappy graphics performance. 

So, after doing some research on this board/chipset and elsewhere, and seeing all the problems that various people are having, I've decided to try going to 11.04 and updating drivers from there.

---

