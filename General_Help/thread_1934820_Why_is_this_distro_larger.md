---
title: "Why is this distro larger?"
date: 2012-03-02
forum: General Help
---

### Post by neon216 on 2012-03-02
Hello,

 I have a 4 gig netbook (Asus eeepc 900) I had installed 11.04 onto a few times. Something had happened with the screen and I was unable to use it and gotten a new one. Recently I have used this netbook for my tv but want to re-install 11.04 or 11.10 (which Im running on my current netbook) and both installations are greater than 4 gigs for some odd reason now. How has this happened / What can I do to reformat this old laptop (due to memory, or lack there of, it isn't running that well) and re-install a distro to fit comfortably in this tiny 4 gig.Thanks!

---

### Post by Frogs Hair on 2012-03-02
Hello and Welcome 

The minimum suggested is 15 Gib . On my 11.10 installation I allowed 40 but am only using 3.6 because I didn't install any music this time around due to updating every six months . I don't know what the minimum you can get away with is now . I assume the is a certain amount of space needed for expansion during the installation.          

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by critin on 2012-03-03
A fresh install from a live CD or flash drive should fit on a 4g drive.  Is the disk clean?

My 11.04 took 2.4 GIB
The install screen asks for at least 4 gib  The installation will format it.

---

### Post by neon216 on 2012-03-03
> **critin said:**
> A fresh install from a live CD or flash drive should fit on a 4g drive.  Is the disk clean?

My 11.04 took 2.4 GIB
The install screen asks for at least 4 gib  The installation will format it.

Fairly. I am having an odd problem with the keyring where it keeps bringing it up and asking me to enter my pw... constantly. Every time I've tried to do a re-install it says ubuntu needs 4.4 gigs of space to install. Before it was much lower, what is the cause of this?

---

### Post by Frogs Hair on 2012-03-03
I think it may have to do with setup files which are temporary . The ISO is still about 700 Mb.

---

### Post by snowpine on 2012-03-03
15gb is my recommendation too.

However, one thing you can check is that you aren't creating a "swap" partition. You may need to choose manual partitioning to do this.

---

### Post by neon216 on 2012-03-03
> **Frogs Hair said:**
> I think it may have to do with setup files which are temporary . The ISO is still about 700 Mb.

Is there a way to fix this for the installation? I'd like to reformat and start anew with 11.04 or 11.10 if possible but am unsure how without the distro exceeding the hdd space

---

### Post by snowpine on 2012-03-03
Another option is a "minimal install" as described here:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by neon216 on 2012-03-03
> **snowpine said:**
> Another option is a "minimal install" as described here:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Im planning on using the netbook as an internet source for my tv for internet and such, I don't think this would work for what I need it to do. Thank you though

---

### Post by critin on 2012-03-03
> Recently I have used this netbook for my tv but want to re-install 11.04 or 11.10

 > I am having an odd problem with the keyring

So you have an OS installed now that is giving you trouble with the keyring?

Have you run the live flash and used gparted to delete and format the disk?  You can also see if another partition is there somewhere taking up space.  Format the whole disk.

Gparted should clean the disk so you have the full 4g back, and then you can install from the desktop icon.

---

### Post by neon216 on 2012-03-03
> **critin said:**
> So you have an OS installed now that is giving you trouble with the keyring?

Have you run the live flash and used gparted to delete and format the disk?  You can also see if another partition is there somewhere taking up space.  Format the whole disk.

Gparted should clean the disk so you have the full 4g back, and then you can install from the desktop icon.

I will definitely check this out, thank you. My problem though seems to be the size of the installation being 4.4 gigs. I don't know why it's so large and how I can bring that down.

---

### Post by critin on 2012-03-04
> **critin said:**
> A fresh install from a live CD or flash drive should fit on a 4g drive.  Is the disk clean?

My 11.04 took 2.4 GIB
The install screen asks for at least 4 gib  The installation will format it.

[COLOR=Red]CORRECTION.  The install screen requires 4.4 GIB's.  [/COLOR]

---

### Post by neon216 on 2012-03-05
> **critin said:**
> [COLOR=Red]CORRECTION.  The install screen requires 4.4 GIB's.  [/COLOR]

Glad I'm not going crazy or doing things wrong. Last time I had installed 11.04 it took at most 3 gigs before, Im unsure why its install size has gone up.

---

