---
title: "sudden low graphics mode"
date: 2010-07-17
forum: General Help
---

### Post by rap3point0 on 2010-07-17
While using Ubuntu I have had few problems and it has generally just worked.  One problem I have had is that while using my computer on occasion everything will be stopped and there will a message against a black background telling me the graphics card and screen could not be detected I have several options which are something like.

Run Ubuntu in low graphics mode for one session (which brings me to a normal login)
Run Ubuntu from a console (or something like that, it goes to a console)
Troubleshoot the error (I'm new to Ubuntu and never tried it)
Restart X (I never used it)

I think I missed one or two 

"Run Ubuntu in low graphics mode for one session" works for me, but it is still a nuisance that I have to login again. Has anyone else had this problem or know of a solution.  It doesn't happen that often, not everyday at least and happens at random. I could have been using it for over an hour so I wonder why it suddenly can't detect the graphics card or monitor

Thanks in advance

---

### Post by Sef on 2010-07-17
What is your graphics card?  (and system specs.)

---

### Post by rap3point0 on 2010-07-17
The Intel Graphics Media Accelerator 3150
It has a n450 1.66gigahertz
1 gig of ram
250 gig HDD
It's a netbook but I use Gnome

---

### Post by spycell on 2010-07-17
Everything was working fine with ubuntu 10.04 netbook for my acer aspire 532h. intel GMA 3150. But since the last updates, I get low graphics mode error on startup. After few searches, I found those errors on X startup:

intel(0): [drm] failed to set drm interface version
            Failed to become DRM master
            failed to get resources : bad file descriptor
            kernel modsetting setup faibled
Screen(s) found, but none have a usable configuration.

I'm stuck to terminal and unable to start X again.

Can someone help us?

---

### Post by rap3point0 on 2010-07-18
[color=red]**bump**[/color]

---

### Post by rap3point0 on 2010-07-19
bump

---

### Post by rap3point0 on 2010-07-20
bump

---

### Post by rap3point0 on 2010-07-20
bump

---

### Post by Devananda.vdv on 2010-08-12
*bump*

I bought an Aspire One 532h yesterday and of course put Ubuntu Netbook 10.04 on it right away. Everything's great ... except that it randomly gets the error described in this thread. Rebooting brings the normal UI back, but after a few hours, it crashes again.

---

