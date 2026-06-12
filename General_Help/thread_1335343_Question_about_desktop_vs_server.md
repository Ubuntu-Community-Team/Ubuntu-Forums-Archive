---
title: "Question about desktop vs server"
date: 2009-11-23
forum: General Help
---

### Post by magnus85 on 2009-11-23
Hi,
 
I am upgrading from windows. Here is my setup:
 
I have one main computer that I used as a windows server. Then in our four offices, I used Neoware Thin Clients (RDP)
 
TO MERGE OVER TO UBUNTU, do I need to just install the Server version of Ubuntu on the dedicated computer then configure my thin clients?
 
Of what do I need to do to set this up??
 
Thanks!

---

### Post by audiomick on 2009-11-23
Hi. I would suggest asking this question in the server platforms section of the forum ;)

---

### Post by lykwydchykyn on 2009-11-23
It's a little frightening the way you use terms like "upgrading from" and "merge over", which imply the idea that this is going to be a seamless operation.  You need to be thinking more along the lines of "complete overhaul from scratch".

Your thin clients are currently using RDP, but Ubuntu does not have a server that supports RDP.  You're either going to have to find another protocol that the thin clients support, or PXE boot them.

The easiest setup for thin clients in my experience is LTSP with PXE on the thin client side.  A good guide for this is here:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

EDIT: this is probably a better starting point:

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by Cheesemill on 2009-11-23
Ubuntu Server doesn't come with a GUI, and so there would be nothing to RDP to (I'm not even sure if it can act as an RDP server).

I think what your looking for would be a LTSP setup (Linux Terminal Server Project) which can be installed using the Ubuntu alternate install CD.
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

Bear in mind that this is designed to work over a LAN, not a WAN so you'll have to check if there is enough bandwidth between your offices and the server to make this feasible.

---

