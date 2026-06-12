---
title: "Can you install ubuntu from an SD card?"
date: 2009-07-04
forum: General Help
---

### Post by cptrohn on 2009-07-04
Hi, I have a friend that wants to install ubuntu on their computer, but the DVD/CD drive on their computer is bad,  I was wondering if I could put ubuntu on a 2GB SD card that I have here at the house and install it that way?  Would it be close to the same as installing from a USB stick or would it be something different altogether?  I saw some stuff on this in a google search but they were all for much older versions of ubuntu than 9.04 and I was wondering if anything had changed as far that would go.

---

### Post by Boondoklife on 2009-07-04
I guess it would really depend on if the computer is able to boot from sd and how it sees it. Why not just dump a usb install on there and see what happens.

---

### Post by cptrohn on 2009-07-04
You mean the USB stick?  I was just wondering if it could be done from the SD card since I have one laying around that I don't use much... I guess I could check the BIOS to see if it can do it....

I do have an old external CDRW that might work though...  I might have to try that one.

---

### Post by Boondoklife on 2009-07-04
Yea put a usb installer on the sd card and see if it works.

---

### Post by Gizenshya on 2009-07-04
you can try it on an SD card.  But it depends on the comp... some can, some can't.  you might not be able to know before just trying it.

some things I would try...

the external CD drive you talked about.  USB is usually active on boot, and it should recognize it.  In fact,I don't even have a CD drive in my new computer (never did).  everything I've installed has been installed from a former external HDD drive-to-CD drive conversion :)

Another option...

Put the hard drive in your computer and install it, then swap back.  This works fine with windows, but I've never tried it with a linux distro, so I can't vouch for it.

another...

Put a cd rom drive in his computer just to install it.

---

### Post by snowpine on 2009-07-04
Unetbootin works for SD cards as well as USB flash drives:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by twright on 2009-07-04
Most computers cannot boot from SD and only newer ones can boot from USB. If the CD drive is really that bad I am guessing that neither SD or USB boot will work (you can always check in the BIOS). Wubi is always an option and if it meets your needs it might be the easiest approch.

---

