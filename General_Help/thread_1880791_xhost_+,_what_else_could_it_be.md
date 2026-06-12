---
title: "xhost +, what else could it be?"
date: 2011-11-14
forum: General Help
---

### Post by sectshun8 on 2011-11-14
So here at work we recently got a new machine that has Red Hat Enterprise 5 on it.  We had 4 previously.  Anyhow, generally from this machine I'll ssh into a Solaris 9 machine and run a few applications and display them on the Red Hat one.  On the version 4, this was never an issue.  Always did an "xhost +" on RedHat, then on Solaris, would "setenv DISPLAY localhost:0.0"  Then would run my applications with no issue.

With this new version, somehow this doesn't work.  Everytime, I get the "Can't connect to X11 window server using 'localhost:0.0' as the value of the DISPLAY variable".

So what gives?

I've tried doing the export DISPLAY=localhost:0.0, I've tried it the IP address, tried most anythign I can think of and I'm getting nowhere.

Help?

---

### Post by sectshun8 on 2011-11-14
If anyone cares, this was the resolution:

Close down everything.
su root
init 3
init 5

then log back in and do xhost +, and BAM, can now do what I needed to do.

---

