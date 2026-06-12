---
title: "Help! Gui has gone..."
date: 2009-07-30
forum: General Help
---

### Post by Teaspooner on 2009-07-30
Hi all.
 
I have Eeebuntu 2 Standard (based on Ubuntu 8.10, I think) installed on SD card on my Eeepc 701. Several days ago, I booted into it to discover that it now boots into the command line only. This was the first boot after an update so maybe the update was somehow the cause. I would be grateful for advice on how to get it to boot into the Gui again!
 
I have tried the relevant recovery boot options but no luck; fsck didn't find errors, so at least the filesystem is probably ok.
 
I can log in at the prompt and have tried startx, which gives these error messages: 
x: warning: process set to priority -1 instead of requested priority 0
giving up.
xinit: no such file or directory (errno 2): unable to connect to x server
xinit: no such process (errno 3): server error.
 
I have also tried starting Gnome desktop manager (gdm), which is apparently already running. 
 
I am not very experienced with linux as yet and would therefore be grateful for guidance as to how best to proceed. Hopefully, I can learn something from this as well as rescuing my installation!
 
Thanks in advance for your suggestions,
 
Teaspooner

---

### Post by wojox on 2009-07-30
This may help:

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by Teaspooner on 2009-07-30
> **wojox said:**
> This may help:
 
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
 
Thanks for the suggestion, which I've just tried. Alas, everything is still the same, only boots into the command line, same error messages when trying startx, gdm already loaded.
 
Teaspooner

---

### Post by Teaspooner on 2009-08-12
Further to my post above, I've now tried to reinstall to the sd card several times but without success. Either the installation process takes ages (>3 hrs!) and then fails to boot at the end of it, or it doesn't start to install at all and throws up two error messages: 

(1) i/o error, dev sdb (the sd card reader) sector 31387632 and 

(2) i/o error on device sdb, logical block 3923454.

The sector and logical block numbers are the same each time.

I would conclude from this that my sd card is faulty but for the fact that Eeebuntu installs successfully and in a reasonable time (40 mins or so) if I put the sd card in an external usb card reader. Now I'm really not sure whether the internal card reader in the eeepc 701 or the sd card itself is faulty. Alas, I don't have another known good sd card to try. I'm fairly confident that the install cd, the eeepc's RAM and the drive I am installing from are all okay. 

If anyone can shed light on which bit may be faulty I'd be grateful.

 
Teaspooner

---

### Post by Mi*6d@# on 2009-08-12
Apparently this is an SD card reader malfunction. I would recommend you just to get ordinary Ubuntu Jaunty CD (write it or get it for free) and install it with no problem.

---

### Post by Teaspooner on 2009-08-12
> **SkyBon said:**
> Apparently this is an SD card reader malfunction. I would recommend you just to get ordinary Ubuntu Jaunty CD (write it or get it for free) and install it with no problem.
 
Thanks for the suggestion. I'm already installing from a cd though, to an sd card.
 
What I'm not sure of is whether it's the sd card itself or the card reader/writer that is causing the problems I am having. The fact that the number of the faulty sector is always the same makes me think it's the sd card at fault, but the fact that Eeebuntu installs okay with the sd card in a usb reader makes me think it's the internal reader in the Eeepc. 
 
Can anyone shed further light on this?
 
Cheers
 
Teaspooner

---

