---
title: "Veetle HD not working"
date: 2011-04-13
forum: General Help
---

### Post by ramkumarc on 2011-04-13
I am new to ubuntu. Is Veetle HD compatible in ubuntu because i am unable to see veetle HD streaming ??. any solution for this ??

---

### Post by searchfgold6789 on 2011-04-13
There is a linux installer on this page: [http://www.veetle.com/index.php/download](http://www.veetle.com/index.php/download)
Since Ubuntu is used by 50% of the linux users, I would assume it works well (and was probably even tested on) Ubuntu.

---

### Post by ramkumarc on 2011-04-13
I did install it. I am able to stream normal videos but unable to stream HD videos. should i do anything ??

---

### Post by mutley89 on 2011-04-13
I have it working fine.  Could you be more specific on what the problem is or any error messages you are getting.

---

### Post by Morderwurst on 2011-04-14
Do you have 64 bit OS?

---

### Post by ramkumarc on 2011-04-15
Its asking me to install veetle if it is a HD link.
Yeah i am using 64 bit OS.

---

### Post by mutley89 on 2011-04-16
If you have installed using the veetle install script you should have 5 shared object files in ~/.mozilla/plugins and a load under ~/.veetle_vlc, do you have these?
also close your browser restart from a terminal prompt, and see if there is any relevant output when you try to play a video.

---

### Post by Paper Bag on 2011-04-16
Not working here either.

In ~/.mozilla/plugins I have libveetle-broadcast-plugin.so, libveetle-core-plugin.so and libveetle-player-plugin.so. You said 5?

Nothing comes up in terminal. I never get to the play video part because "This channel is only available in HD. Upgrade to Veetle TV to watch". Non-HD streams do work.

I'm also using 64-bit and FF4.0 is also 64-bit.

---

### Post by mutley89 on 2011-04-16
I also have:
libveetle-core-plugin-x86_64.so
libveetle-player-plugin-x86_64.so
I have just downloaded the tarball from veetle's site but it only seems to have the 32 bit versions.
Thinking about it a bit more i think i got the 64 bit version from their forums which seems down at the minute.
Edit: try this:
[http://veetle.com/download.php/veetle-0.9.17plus.tgz](http://veetle.com/download.php/veetle-0.9.17plus.tgz)

---

### Post by Paper Bag on 2011-04-16
Reinstalled from that tarball - now works.

---

### Post by ramkumarc on 2011-04-16
Thanks mate. it works !!

---

### Post by PremiumG on 2012-09-08
Any idea how to get it working in Lubuntu 64-bit? These commands performed successfully in terminal, yet it Veetle still only plays in SD. HD just requests me to install the software that I have already installed.

BTW, Lubuntu uses Chromium, not Firefox.

---

### Post by oldos2er on 2012-09-09
Old thread closed; please start a new thread.

---

