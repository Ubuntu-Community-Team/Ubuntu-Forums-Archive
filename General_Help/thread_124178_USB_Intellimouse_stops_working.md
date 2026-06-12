---
title: "USB Intellimouse stops working"
date: 2006-01-31
forum: General Help
---

### Post by MrNamjama on 2006-01-31
Hi

My USB Intellimouse (plugged into Dell 510m running Breezy with latest updates as of last night) randomly stops working - the light on it goes out and it's gone. Plugging it out and then back in wakes it up, but it may or may not stop again soon.

Has anyone experienced this before? Any common causes? I don't know where to start to look for causes, I'm not very handy with Linux logs yet...

---

### Post by o_fortuna on 2006-01-31
[QUOTE=MrNamjama]Hi

My USB Intellimouse (plugged into Dell 510m running Breezy with latest updates as of last night) randomly stops working - the light on it goes out and it's gone. Plugging it out and then back in wakes it up, but it may or may not stop again soon.

Has anyone experienced this before? Any common causes? I don't know where to start to look for causes, I'm not very handy with Linux logs yet...[/QUOTE]
In fact, I have experienced it. I had to unplug the mouse reciever and plug it back in. Mysteriously, however, I haven't had to fix it in awhile. I have no idea what causes it or how I fixed it. I'm guessing that it has something to do with the X server, but I have no clue. I'm also using a different linux-kernel package than before. You could try to upgrade to a newer kernel (ie, if you have an Athlon 64 get the linux-kernel-k7 package, if you have a Pentium 4 get the linux-kernel-686 package, and if you have a dual core (Athlon 64-X2), make sure to get the linux-kernel-blahblahblah-smp). I don't know if that will work, but it seemed to do it for me...

---

### Post by MrNamjama on 2006-02-01
I've been running a different kernel for a while now - i believe it's the 686 one, off the top of my head (for a Pentium M). Perhaps this problem would be a fairly regular occurence, but I actually only use the mouse on the laptop reasonably rarely... I'll try having it plugged in more often to guage the frequency of this problem

---

### Post by cri on 2006-10-16
This happens to me too with my M$ optical USB Intellimouse connected to a Dell e1405 running SMP kernel 2.6.15-23-686. I can go a whole week and never have to replug the thing, other days I may have to replug 4-5 times. I have no idea how to fix it.

---

