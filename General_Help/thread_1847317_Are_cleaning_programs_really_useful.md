---
title: "Are cleaning programs really useful?"
date: 2011-09-20
forum: General Help
---

### Post by pretty_whistle on 2011-09-20
The kind I speak of deletes unnecessary files to free valuable disk space, maintain privacy, and remove junk. It removes cache, Internet history, temporary files, cookies, and broken shortcuts.

Is that really useful?.....considering it would be done on Ubuntu 11.04.  I did it on Windows and my ignorance of Linux is sparking this question.

And how about a program that wipes free disk space?  Yeah, I'm into privacy but I wonder because this is Linux and not Windows..  I did it on Windows.

(I have a program in mind that does both-cleans and wipes free disk space.)

---

### Post by blueridgedog on 2011-09-20
My opinion is no.  If you are running low on disk space, there are other tools to search for the offending files.  Others with an orientation more towards privacy may feel different about scrubbing free disk space.  Keep in  mind that to have a chance to recover deleted files someone must have physical access to your disk.  If you are that concerned about privacy, then you should run some of the popular RAM only distributions that leave no trace after a reboot.

---

### Post by t0p on 2011-09-20
My desktop PC has a small hard drive (30 GB) and if I'm not vigilant I can easily run low on space.  So I find the app **BleachBit** useful sometimes.  Of course I could clear out the logs, caches etc manually, but it is rather nice to do it with just a couple of clicks.

Of course, if your computer is *not* prehistoric, you probably won't have much use for such an app.

---

### Post by pretty_whistle on 2011-09-20
> **t0p said:**
> My desktop PC has a small hard drive (30 GB) and if I'm not vigilant I can easily run low on space.  So I find the app **BleachBit** useful sometimes.  Of course I could clear out the logs, caches etc manually, but it is rather nice to do it with just a couple of clicks.

Of course, if your computer is *not* prehistoric, you probably won't have much use for such an app.

BleachBit?  That's the one I have in mind.

Yeah, it's easier to have the program clear those out than to do it manually-I agree.  That's one reason I am wondering if I should have the program or not.  One reason.

---

### Post by raja.genupula on 2011-09-20
+1 
Bleach bit is good software for cleaning operations .
i think it's PPA pre loaded .
```
sudo apt-get install bleachbit
```
use this to install it .

All the best .

---

### Post by pretty_whistle on 2011-09-20
> **raja.genupula said:**
> +1 
Bleach bit is good software for cleaning operations .
i think it's PPA pre loaded .
```
sudo apt-get install bleachbit
```use this to install it .

All the best .

Thanx.

---

### Post by _d_ on 2011-09-20
For the most up to date version of BleachBit:

[http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux)

---

### Post by pretty_whistle on 2011-09-20
> **blueridgedog said:**
> My opinion is no.  If you are running low on disk space, there are other tools to search for the offending files.  Others with an orientation more towards privacy may feel different about scrubbing free disk space.  Keep in  mind that to have a chance to recover deleted files someone must have physical access to your disk.  If you are that concerned about privacy, then you should run some of the popular RAM only distributions that leave no trace after a reboot.

I'm interested in wiping free space not because of privacy.  I'm thinking outside the box, thinking, "If computer forensics can recover deleted stuff then this means in some way there's space being used by the deleted items.  If I neglect wiping free space it may be that over time that space being used would accumulate and I'd lose some free space to it-like if I let it go for 4 years, for example."

I don't even know if this is true-if I'm wrong, let  me know.  I wouldn't be surprised if the space all that takes up over time is probably negligible.

---

### Post by raja.genupula on 2011-09-20
> **pretty_whistle said:**
> Thanx.

Always welcome , Enjoy The Ubuntu .

---

### Post by pretty_whistle on 2011-09-20
> **raja.genupula said:**
> Always welcome , Enjoy The Ubuntu .
I always enjoy that.  :D :D

---

### Post by blueridgedog on 2011-09-20
> **pretty_whistle said:**
> I'm interested in wiping free space not because of privacy...this means in some way there's space being used by the deleted items

Forensic teams can recover data because it is simply flagged as free and not overwritten.  The wipe programs you speak of will simply write new data over it (each bit is either 1 or 0).  Flagged as free is free regardless of the value the bit has.

Out of curiosity, what size storage do you have?  I guess I have become spoiled lately as drives are so large and so cheap that I have generally gotten out of the habit of watching it like a hawk.

---

### Post by pretty_whistle on 2011-09-20
> **blueridgedog said:**
> Forensic teams can recover data because it is simply flagged as free and not overwritten.  The wipe programs you speak of will simply write new data over it (each bit is either 1 or 0).  Flagged as free is free regardless of the value the bit has.

Out of curiosity, what size storage do you have?  I guess I have become spoiled lately as drives are so large and so cheap that I have generally gotten out of the habit of watching it like a hawk.

What size?  A 250GB portable drive and the Linux sits on a 160GB.

And thanx for the forensic explanation.

I'll mark this thread as resolved then.

---

