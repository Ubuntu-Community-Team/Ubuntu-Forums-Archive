---
title: "virtual box and video"
date: 2009-11-11
forum: General Help
---

### Post by dbowlin17 on 2009-11-11
I am trying to play a game using virtual box and windows xp. however each time i start, i get a message saying that direct draw couldn't initalize. I read somewhere i should replace the virtual box video driver but i dunno what to do...?

---

### Post by delcypher on 2009-11-11
> **dbowlin17 said:**
> I am trying to play a game using virtual box and windows xp. however each time i start, i get a message saying that direct draw couldn't initalize. I read somewhere i should replace the virtual box video driver but i dunno what to do...?

Have you installed the guest-additions? 

Whilst running a virtual machine click "Devices > Install Guest additions". This will mount the Guest additions CD in the virtual cd/dvd drive in your virtual machine and you can install from there.

Part of the installation has the virtualbox video driver. I'm not an expert on this but to my knowledge the VirtualBox video driver has very limited directx & openGL support. You may have better luck getting your game to work through wine. 

Look at the wine database to see if your game is known to work ( [http://appdb.winehq.org/]("http://appdb.winehq.org/") )

---

### Post by dbowlin17 on 2009-11-12
when i try to install guest additions, nothing happens. is there some special disk I need? also you said that the vbox video driver isnt good. but is there a way to install a better video driver for vbox?

---

