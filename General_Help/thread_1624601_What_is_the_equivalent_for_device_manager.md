---
title: "What is the equivalent for device manager?"
date: 2010-11-17
forum: General Help
---

### Post by AceRimmer on 2010-11-17
Hi I'm messing around with Ubuntu again after not touching it since 7.04 I think. Anyway I threw 10.10 64 bit on my old Opteron system but I'm having a problem.  It isn't showing my Netgear WN311T wireless card and the sound doesn't work, AC 97 onboard audio.  I'm trying to see if it even detected them when I installed it but I can't find something to list all installed hardware. I thought there were was something in the older distros I used to use. 

"lspci -v | less" didn't show any wireless card. 

Thanks for any help.

---

### Post by David802 on 2010-11-17
Try 

> sudo lshw

There may be something better... but that was the command I kept using when I was troubleshooting my wifi a while back.

---

### Post by madberry on 2010-12-15
Try my solution see this blogpost: [http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/](http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/)
--
Berry van der Linden
[http://undiff.com](http://undiff.com)
[http://q3w.org](http://q3w.org)

---

### Post by branscombe_richmond on 2010-12-15
howcome ubu doesn't just have a built in GUI app for this yet?  how far behind is ubu in terms of having something like this?

---

### Post by junapp on 2010-12-15
not sure if hardinfo is sort of what you are after, although most of it can be obtained through system monitor.

sudo apt-get install hardinfo

screenshots:
[http://hardinfo.berlios.de/Screenshots](http://hardinfo.berlios.de/Screenshots)

---

### Post by piquat on 2010-12-16
Isn't device "manager" really the wrong title for this application.

Maybe I'm not seeing it but it doesn't really "manage" anything.  IE. you can't really CHANGE anything with it.

It's more like a device/hardware "displayer" or "lister".

Nice to have but kind of deceiving if you're coming from windows and looking for an analog.

---

### Post by mastablasta on 2010-12-16
> **branscombe_richmond said:**
> howcome ubu doesn't just have a built in GUI app for this yet? 
 
maybe because devices and drivers are managed differently in linux.

---

### Post by amsterdamharu on 2010-12-16
> IE. you can't really CHANGE anything with it.Never used Windows after XP but you can remove devices and then refresh for plug and pray.

Anyway hardinfo is the gui but it's not installed by default so as junapp suggested install that.

---

