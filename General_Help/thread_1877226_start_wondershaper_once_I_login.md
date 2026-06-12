---
title: "start wondershaper once I login"
date: 2011-11-07
forum: General Help
---

### Post by nethero on 2011-11-07
I use wondershaper to limit my bandwidth and I would like it to start _when I login_, NOT when I boot linux.  How do I do this?  Normally I would run...

sudo wondershaper eth0 1200 1200

I have to use sudo because running the command otherwise does not work.  So my question is; how do I run this when I login?  Is this possible?

---

### Post by dcstar on 2011-11-08
> **nethero said:**
> I use wondershaper to limit my bandwidth and I would like it to start _when I login_, NOT when I boot linux.  How do I do this?  Normally I would run...

sudo wondershaper eth0 1200 1200

I have to use sudo because running the command otherwise does not work.  So my question is; how do I run this when I login?  Is this possible?

Make a script and put it in the Startup Applications.

---

### Post by nethero on 2011-11-09
Wouldn't the script have to contain my password since I run this as sudo?  I'd rather not reveal my password like that.

---

### Post by |{urse on 2011-11-09
Nope, most likely on login you'll be prompted to enter your password.

---

### Post by dcstar on 2011-11-10
> **|{urse said:**
> Nope, most likely on login you'll be prompted to enter your password.

Exactly, and if you really want to get fancy you use gksudo.

---

