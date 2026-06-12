---
title: "lost sound"
date: 2010-10-19
forum: General Help
---

### Post by sonicbs on 2010-10-19
Hi,
My machine shut down unexpectedly today (laptop battery is crap) and when I rebooted it I lost all sound.
I tried to go to Preferences->Sound but it just opens a little window saying "waiting for sound system to respond" and nothing happens. When my computer rebooted it did warn me of some errors in the filesystem after the unexpected shut down, but I let it correct all errors it found.
I understand I may need to reinstall some packages, but I don't know which.

System: 
Dell XPS m1330
Ubuntu 10.10 64bit 

Is there anyone out there who can help me?
Thanks in advance!

---

### Post by dallasWolf on 2010-10-19
Have you check your bios settings? It is possible that your sound setting reset when your machine failed.

---

### Post by sonicbs on 2010-10-19
dallasWolf, thanks for the quick reply. I did check the BIOS settings, and nothing there was disabled. I also booted to Windows (I hate to do that... :-) ) and there sound works... so this ruled out the BIOS suggestion.
Any other ideas?!... :-)

---

### Post by qianian on 2010-10-21
I did a clean install of 10.10 x64 on a Thinkpad R61i. Sound preferences were fine until I got the same error yesterday after numerous updates. I can't touch the main volume except mute, though applications and web videos have working volume adjustment.

Complete uninstall and reinstall of pulseaudio, restart did nothing.

Sorry this is unhelpfully vague because I did install a bunch of programs e.g. jackd, but it's not running.

---

### Post by sonicbs on 2010-10-21
Just to cross-ref, I posted the same question on Ubuntu stack exchange. Still no answer there either, but this may be a useful link:

[http://askubuntu.com/questions/8324/how-can-one-reinstall-sound-drivers]("http://askubuntu.com/questions/8324/how-can-one-reinstall-sound-drivers")

---

### Post by Yellow Pasque on 2010-10-21
Try removing the .pulse files in your home directory (may have been corrupted by sudden shutdown):
```
cd ~/
rm -rf .pulse*
```
Log out and log back in.

---

### Post by sonicbs on 2010-10-21
> **Temüjin said:**
> Try removing the .pulse files in your home directory (may have been corrupted by sudden shutdown):
```
cd ~/
rm -rf .pulse*
```
Log out and log back in.

It worked!! Thank you!
Marking thread as solved

---

