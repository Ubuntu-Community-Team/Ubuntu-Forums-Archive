---
title: "Is my Kernel crashing?"
date: 2011-07-19
forum: General Help
---

### Post by CastilleV on 2011-07-19
I installed Ubuntu 11.04 on my old acer aspire 5610, and then after a few minutes of surfing the web this happens.

[http://imageshack.us/photo/my-images/842/image074m.jpg/](http://imageshack.us/photo/my-images/842/image074m.jpg/)

[http://imageshack.us/photo/my-images/694/image075s.jpg/](http://imageshack.us/photo/my-images/694/image075s.jpg/)

Can anyone help me out here?

I DL'ed it on a DVD+RW, so I can install a more stable version of Ubuntu if need be.

---

### Post by CastilleV on 2011-07-19
> **CastilleV said:**
> I installed Ubuntu 11.04 on my old acer aspire 5610, and then after a few minutes of surfing the web this happens.

[http://imageshack.us/photo/my-images/842/image074m.jpg/](http://imageshack.us/photo/my-images/842/image074m.jpg/)

[http://imageshack.us/photo/my-images/694/image075s.jpg/](http://imageshack.us/photo/my-images/694/image075s.jpg/)

Can anyone help me out here?

I DL'ed it on a DVD+RW, so I can install a more stable version of Ubuntu if need be.

If anyone needs the specs to my laptop, they're right here.
[http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire5610/Aspire5610sp2.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire5610/Aspire5610sp2.shtml)

Can anyone help me out here?

---

### Post by 2F4U on 2011-07-20
That is definitely a kernel crash but the pictures are difficult to read. I was able to read something about iwl3945, which could be the wireless module. Do you need wireless or is it possible to switch it off and use a wired connection?

---

### Post by foxmulder881 on 2011-07-20
Yeah stuff like that is usually a kernel crash of some sort.

Perhaps have a poke around in /var/log/kern.log and see what's going on. That might give you a better idea of what's causing the crash.

---

### Post by CastilleV on 2011-07-20
> **foxmulder881 said:**
> Yeah stuff like that is usually a kernel crash of some sort.

Perhaps have a poke around in /var/log/kern.log and see what's going on. That might give you a better idea of what's causing the crash.

I was afraid of this.

Well, thankfully I have an old shipit CD with 9.0.4 and working internet, so i'm gonna install that version and upgrade it manually to either 11.04 or an older more stable version.

---

