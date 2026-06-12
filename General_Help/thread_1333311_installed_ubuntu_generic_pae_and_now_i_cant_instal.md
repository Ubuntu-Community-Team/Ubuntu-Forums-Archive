---
title: "installed ubuntu generic pae and now i cant install my video driver"
date: 2009-11-21
forum: General Help
---

### Post by topsykretts on 2009-11-21
hey guys..i just installed the ubuntu generic pae on my laptop so that my 32bit ubuntu 9.10 can recognize my 4gb of ram.i cant switch to 64bit because for some reason the native linux 64bit driver for realtek 8192se isnt very stable so swtiching to 64bit isnt an option for me.anyway, installing the generic pae deactivates my video driver and when i go to hardware drivers to reactivate it does nothing..nothing happends.what do guys think could be the problem?i used this command                                   [FONT=DejaVu Sans Mono]sudo apt-get install linux-generic-pae[/FONT]
   
  
and my gfx card is a ATI Radeon 3100

---

### Post by Woody1987 on 2009-11-21
I had the same exact same problem but using an ATI radeon 4670. My solution was to just use the opensauce driver as i dont need 3D but it does 2D very well.

---

### Post by directhex on 2009-11-21
Proprietary 3D drivers cannot use PAE. There's no workaround.

---

### Post by topsykretts on 2009-11-21
> **Woody1987 said:**
> I had the same exact same problem but using an ATI radeon 4670. My solution was to just use the opensauce driver as i dont need 3D but it does 2D very well.

hhhmmm interesting...can you direct me to a tutorial on installing the ati radeon open source driver?or if its not too long can you post it here?will it work my model?thanks!

> Proprietary 3D drivers cannot use PAE. There's no workaround. 	 

i guess you cant have em all huh?if i down grade to 9.04 and use the linux server kernel(since 9.10 no longer has support for a 32bit server) will my proprietary 3D driver be compatible with a server kernel?

---

### Post by 3rdalbum on 2009-11-21
> **topsykretts said:**
> hhhmmm interesting...can you direct me to a tutorial on installing the ati radeon open source driver?or if its not too long can you post it here?will it work my model?thanks!

It comes preinstalled, just modify xorg.conf to use the "ati" driver rather than "fglrx".

> i guess you cant have em all huh?if i down grade to 9.04 and use the linux server kernel(since 9.10 no longer has support for a 32bit server) will my proprietary 3D driver be compatible with a server kernel?

If your server kernel has PAE (which I imagine is why you want it), then no.

I'm interested in why an open-source driver wouldn't work as well on 64-bit as on 32-bit. I have Realtek audio, no problems on 64-bit. When a driver's source code can run on eleven different architectures, it should be able to run on a 64-bit version of the most commonly-used architecture out there.

---

### Post by topsykretts on 2009-11-21
> I'm interested in why an open-source driver wouldn't work as well on 64-bit as on 32-bit. I have Realtek audio, no problems on 64-bit. When a driver's source code can run on eleven different architectures, it should be able to run on a 64-bit version of the most commonly-used architecture out there.sorry.i forgot to mention that its a realtek 8192se wifi driver.I have no idea why the native 64bit linux wifi driver doesnt work as well as the 32bit.when im using the 32bit ubuntu and 32bit driver the signal is fine and my wifi work great.but on the 64bit ubuntu usingthe 64bit driver after about 5 minutes i lose my connection.the signal bar is full alright and its showing 88-100% strength but im not connecting to websites or able to download anything.i have to reboot or disconnect/reconnect to my wifi to get it to work again.but after 5 minutes,its at it again.

what i havent tried is using the 32bit driver on a 64bit ubuntu but something tells me not to do that.or should i?*eyebrows raised*..hhaha

---

### Post by 73ckn797 on 2009-11-21
I installed the 32 bit, regular Ubuntu 9.10 and discovered PAE was enabled. Before I would of had to use the server edition, adding the Gnome stuff. It rather surprised me, actually. I only used it a few days and went back to 64 bit. I posted this realization several weeks back but received no feedback of others discovering this..

---

### Post by topsykretts on 2009-11-22
> **3rdalbum said:**
> It comes preinstalled, just modify xorg.conf to use the "ati" driver rather than "fglrx".

ok so i went 

sudo gedit /etc/X11/xorg.conf
and i get a blank page..so i manually go to /etc/X11/ and there is no xorg.conf  file for me to "sudo gedit /etc/X11/xorg.conf" haha...any ideas?i have a hunch i need to get something from synaptic..

---

### Post by topsykretts on 2009-11-22
ok nevermind i actually do have a "xorg.conf"


> It comes preinstalled, just modify xorg.conf to use the "ati" driver rather than "fglrx".i changed the "fglrx" to "ati"..now what?i went to appearance to change my visual effects to extra and it still says "cant enable desktop effects"...so i guess i have to do something else apart from a little fglrx/ati switcheroo on xorg.conf...

---

### Post by topsykretts on 2009-11-22
ok..nevermind again!! it was as simple as changing the "fglrx" to "ati" at the xorg.conf ..thanks 3rdalbum and thanks to everyone that posted.problem solved!

---

