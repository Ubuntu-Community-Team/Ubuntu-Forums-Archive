---
title: "Cylinder head count exceeded"
date: 2010-02-06
forum: General Help
---

### Post by reyals140 on 2010-02-06
Why is it telling me that my hard drive cylinder head count isn't supported by bios when I've been using this hard drive with this bios for over a year?
I mean Linux is booting off the hard drive this is supposedly unsorted apparently and managing telling me is unsupported... so it can't be that unsupported now can it?
Sounds more like linux trying to blame bios for linux's problem.  Regardless how do I make it go away?  Thoughts?

---

### Post by dcstar on 2010-02-06
> **reyals140 said:**
> Why is it telling me that my hard drive cylinder head count isn't supported by bios when I've been using this hard drive with this bios for over a year?
I mean Linux is booting off the hard drive this is supposedly unsorted apparently and managing telling me is unsupported... so it can't be that unsupported now can it?
Sounds more like linux trying to blame bios for linux's problem.  Regardless how do I make it go away?  Thoughts?

You are probably using a legacy BIOS mode for your hard disk instead of letting it auto-detect and use the best mode.

Be warned that changing an existing mode can totally stop your HD data being accessed.

---

### Post by reyals140 on 2010-02-06
> **dcstar said:**
> You are probably using a legacy BIOS mode for your hard disk instead of letting it auto-detect and use the best mode.

Be warned that changing an existing mode can totally stop your HD data being accessed.

It can't be the BIOS' fault (unless it broke in which case I don't think the computer would be  able to load linux far enough to give me an error message).
The BIOS hasn't changed since I bought the computer.
The last thing the computer did was install some updates, restart, and now suddenly the hard drive is to big?  Something broke in the OS.....

If it helps the exact error is 
Error 18: Selected cylinder exceeds maximum supported by BIOS
Most of what I could google up seemed to blame GRUB...?

---

### Post by reyals140 on 2010-02-06
Well the live CD still works so I'm going to have to copy everything off through the network and reinstall linux.... AGAIN

---

