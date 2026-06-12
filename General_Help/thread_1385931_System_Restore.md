---
title: "System Restore"
date: 2010-01-20
forum: General Help
---

### Post by JasonInferno on 2010-01-20
I'm looking at completely restoring my Jaunty system to default. Thing is, I have no spare LiveCDs lying around, and my only LiveCD is scratched.
Does Jaunty include a tool or command to restore the system to as it was a clean install?
I'm not asking to remove it completely (I can use my GParted LiveUSB for that), nor am I asking for it to be a terminal-only install. I want it restored to it's original state, like when it was first installed to my machine.

inb4 format /dev/sdb

---

### Post by wojox on 2010-01-20
You could try [time vault]("https://wiki.ubuntu.com/TimeVault") but it's to late since it wasn't installed ahead of time. It makes snapshots of directories.

---

### Post by mechro on 2010-01-20
Unetbootin?...

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

... it says you can do a "frugal install" if you don't have a USB drive.

---

### Post by iponeverything on 2010-01-20
There is nothing like this. It would be fairly complex to keep track of very package upgrades and file modifications and the information need to revert to its original state. 

Many windows machines have this but it is accomplished via a hidden partition containing an image of the original install.

---

### Post by JasonInferno on 2010-01-20
> **mechro said:**
> Unetbootin?...
Yeah, I've actually been using that as an alternative to CD/DVD discs, as I can re-use the live media and modify the live system on-the-fly. Thing is, my internet's limited until February, and is running too slow to download any large files, including .iso files. So frugal installs and live media creation (or anything involving .iso files) isn't on my list as of now.
Try living at 7 kb/s for an entire month. :(


> **iponeverything said:**
> There is nothing like this. It would be fairly complex to keep track of very package upgrades and file modifications and the information need to revert to its original state.
I'll be sure to keep that noted. I never woulda thought of that.

---

### Post by mechro on 2010-01-20
Any chance you've got the jaunty .iso somewhere on your hard drive? For example I've got one in my intrepid back-up.

---

