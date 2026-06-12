---
title: "Run Ubuntu in low graphics mode for just one session"
date: 2011-05-05
forum: General Help
---

### Post by newbun on 2011-05-05
Hi Forum

The above subject was one of the options I was given on the boot up of Ubuntu 11.04 (natty) after the message **'Your screen graphics card and input device could not be detected correctly'**

I OK'd the message to run in low graphics mode.

The question is: What's causing this?  I've had a look through previous posts with (apparently) the same problem, but the methods used were inconclusive, even though in some cases the problem was resolved.

Nvidia was mentioned - about deleting all references to it in Packet manager.  Would this work?  And if so, why?

This was one of the lines of an LSPCI command in terminal...

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

Don't know if that helps?

How can I get the graphics to run properly?

Thanks, hope you can help.

---

### Post by zvacet on 2011-05-06
Maybe you have to install drivers to run Unity,so on login screen>session> choose Ubuntu classic and if that works try to install drivers for your gpu.

---

