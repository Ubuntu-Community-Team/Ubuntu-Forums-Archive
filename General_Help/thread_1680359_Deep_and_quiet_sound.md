---
title: "Deep and quiet sound"
date: 2011-02-02
forum: General Help
---

### Post by dwigyit on 2011-02-02
I've just installed Ubuntu 10.10 on an MSI GX660 laptop and the sound is doing strange things. It plays and all that when it's supposed to, but it is incredibly deep and vibrates the speakers, it also plays much quieter than usual (though it could just sound quieter because it's deeper). I was wondering if anyone else has encountered this problem and if they have a fix for it - as Google advises only to upgrade ALSA, which I don't know how to do. :(

EDIT - I don't even know if it's deeper. It almost sounds like it's a sub speaker or something, you know, a third one - as it vibrates when the pitch gets higher, despite it actually being pretty deep.

---

### Post by dwigyit on 2011-02-16
There's a thread on the MSI support forums here

[http://forum-en.msi.com/index.php?topic=144941.0](http://forum-en.msi.com/index.php?topic=144941.0)

but it hasn't been successful yet in finding a solution. I imagine most of their people are Windows users, though.

---

### Post by dwigyit on 2011-03-12
Someone there suggested adding 

options snd_hda_intel model=targa-8ch-dig

to etc/modprobe.d/alsa-config but doing so simply stops the sound working at all until I remove it. Someone else said it worked for them, so perhaps I added it to the wrong file or in the wrong way. Any ideas?

---

### Post by DaH-RaT on 2011-03-13
hey whats up im also having the same issue. when i turn the sound up all the way i hear a static pop in my left speaker as well. I researched and edited that as well and no fix here. I guess we will have to wait and/or even hope it gets resolved.. in the meantime i guess we will have to rely on another OS for music. But you are not alone, im going to assume everyone with a gx660 is have this problem. my friend and i purchased the gx660-260us and both reformatted to ubuntu. same issue.

---

### Post by dwigyit on 2011-08-23
I found a sort-of-fix, DaH-RaT:

A thread about how it sort-of-works is here:
[http://ubuntuforums.org/showthread.php?t=1830213](http://ubuntuforums.org/showthread.php?t=1830213)

alsa-base is a .config (text) file in your etc/modprobe.d directory - which you need to edit as root if you want to save changes

---

