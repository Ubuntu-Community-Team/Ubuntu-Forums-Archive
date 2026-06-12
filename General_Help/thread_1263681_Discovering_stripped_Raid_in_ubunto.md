---
title: "Discovering stripped Raid in ubunto"
date: 2009-09-11
forum: General Help
---

### Post by NetDevil89 on 2009-09-11
Hey guys

I have had 2 disks in a nas server(1tb and 500gb) these have been in stripped raid in the server. now i want these disks in my desktop pc, but i can't seem to get them mounted or even discover them as raid. i have used  Gparted where i cannot mount them, i get an error saying unknown filesystem Linux_Raid_member . 

There is data on them which i need, so i would very much prefere if i could recover them somehow but i don't now how. this is also due to that im a noob to ubunto (im using ubunto 9.04)

I have tried using mdadm but because im as sayd earlier a noob to this i diden't know how to do anything. 

All your help is greatly appriciated!

---

### Post by tgrimley on 2009-09-11
It's Ubunt**u**.

What is your NAS? Make model?  It's very likely it uses a proprietary file system and you won't be able to read it in your desktop.  It's doubly likely you won't be able to read the striping pattern it uses.

---

