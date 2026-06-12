---
title: "Internet won't work?"
date: 2010-10-17
forum: General Help
---

### Post by Mohammad17 on 2010-10-17
Hi guys, before i go on, i'd like to apologize if this is the wrong section.

I'm trying to connect to the internet on ubuntu, but what ever i do fails. I've tried every thing i possibly can, and when all else failed, i had to come and ask. When i try to connect to the internet, it always says "unable to connect". I have no clue why. I'm choosing the default wired setting. To the side of it, it says never, so that might be the problem? 

I know what i just said sounded terrible, but ill post more if you guys can help me out. Thanks

---

### Post by Yarui on 2010-10-17
I'm not really sure what could cause this sort of problem in Ubuntu, but the first thing I would do if this happened to me is check out my networking equipment.  Make sure the modem and router are running properly, make sure none of the cables are bad and that they are all making a good connection.

---

### Post by Mohammad17 on 2010-10-17
> **Yarui said:**
> I'm not really sure what could cause this sort of problem in Ubuntu, but the first thing I would do if this happened to me is check out my networking equipment.  Make sure the modem and router are running properly, make sure none of the cables are bad and that they are all making a good connection.

Im 100% sure my modem and all works fine. Im using same one at the moment. I'm getting so frustrated, i have no clue what to do anymore. I really don't want to use my crappy vista any more =(

---

### Post by jv2112 on 2010-10-17
Is it detecting your nic ?

Type ifconfig in a terminal & see if it is there.

If you left click on the network icon on the tray is the connection there ?

Can you ping your router (192.168.1.1 Most cases) ?

Type mtr [www.google.com](www.google.com) in a terminal. --> Does it show a path ?


I have never seen any distro not pick up on a nic since most chipsets are in the kernel. 

Maybe a bad nic ?

---

