---
title: "install lucid to try and remove after?"
date: 2010-04-30
forum: General Help
---

### Post by Kaneda187 on 2010-04-30
Hey people I've out of the "loop" as you might call it for a while and im just wondering...

I want to install lucid on my dual boot system along side my current ubuntu and windows 7 on a 5gb partition to try it out.

My question is would ther be any risk to my ubuntu data of my windows data if i do this?

---

### Post by GSF1200S on 2010-04-30
> **Kaneda187 said:**
> Hey people I've out of the "loop" as you might call it for a while and im just wondering...

I want to install lucid on my dual boot system along side my current ubuntu and windows 7 on a 5gb partition to try it out.

My question is would ther be any risk to my ubuntu data of my windows data if i do this?

Well, the proper thing to say is always backup your data in case something goes wrong (and things can go wrong).

If things go right, as they usually do, then no- there is no risk to your data. Ubuntu 10.04 should pick up Windows 7 and your other version of Ubuntu and add them to Grub. Even if you have issues with this, a simple:
```
sudo update-grub2
```
should get all the other OS's on your grub screen. Good luck..

---

