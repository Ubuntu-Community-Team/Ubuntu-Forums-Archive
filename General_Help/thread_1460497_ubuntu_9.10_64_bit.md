---
title: "ubuntu 9.10 64 bit"
date: 2010-04-22
forum: General Help
---

### Post by aravel on 2010-04-22
Hey everyone,

Forgive my grand Ubuntu ignorance, but I am a really new user.  The 64 bit version I download from the website says amd64 bit, does that mean I need to have an amd processor?  I am currently running Windows 7 64 bit on my intel quad core processor, so I know my system can run a 64 bit OS, but will it work with 9.10 64 bit?  Any input would be greatly appreciated!

---

### Post by jaco223 on 2010-04-22
> **aravel said:**
> Hey everyone,

Forgive my grand Ubuntu ignorance, but I am a really new user.  The 64 bit version I download from the website says amd64 bit, does that mean I need to have an amd processor?  I am currently running Windows 7 64 bit on my intel quad core processor, so I know my system can run a 64 bit OS, but will it work with 9.10 64 bit?  Any input would be greatly appreciated!

No you don't need an amd processor, if you have 64bit win7 then you're good to go with Ubuntu 9.10 64bit.

Hope this helps.
Jaco

---

### Post by _0R10N on 2010-04-22
nop, AMD64 is only an architecture naming convention, not a processor brand restriction. I'm running Karmic AMD64 on my i5 as I write these lines.:lolflag:

Kind regards!

_0R10N >>

---

### Post by The Thunder Chimp on 2010-04-22
That's right, as far as I know (better underline that: _as far as I know_) there is only three architectures possible in Ubuntu:

1: 32-bit (i3886) (works on almost all computers)
2: 64-bit (amd64) (works on every 64-bit machines)
3: Power PC (PPC) (works on Mac Power PCs and Playstation 3s)

By the way, you don't have to say you're a newbie. We'll try to resolve your question no matter how hard or easy it is, and above all we'll never laugh at anyone's ignorance as (to quote Debian Forums) "no one is born knowing these things".

---

### Post by MButterman on 2010-04-23
Using lucid lynx RC, I am running the 64 bit and have a AMD Phenom II 945, do I need to update the kernel to take advantage of the quad core or to speed up the system.

Thanks

---

### Post by 3rdalbum on 2010-04-23
> **MButterman said:**
> Using lucid lynx RC, I am running the 64 bit and have a AMD Phenom II 945, do I need to update the kernel to take advantage of the quad core or to speed up the system.

Thanks

No, Linux supports multiple cores out-of-the-box. Go to System > Administration > System Monitor and you'll see four cores being monitored.

---

### Post by ambdeep on 2010-04-23
is it possible to upgrade from 32 bit to 64 bit without having to format?

---

### Post by klemes on 2010-04-23
No as far as I know.You must perform a clean 64bit installation from the grounds up.

---

### Post by The Thunder Chimp on 2010-04-23
> **ambdeep said:**
> is it possible to upgrade from 32 bit to 64 bit without having to format?

No, I'm fairly sure that it's the way the Operating System is built. However, please make sure that your computer supports 64-bit before trying to reinstall it in a clean way. If there's no other way of doing it, you might want to make a 64-bit partition just to see if it's possible.

---

### Post by 3rdalbum on 2010-04-24
> **The Thunder Chimp said:**
> Yeah, I'm fairly sure that it's the way the Operating System is built. However, please make sure that your computer supports 64-bit before trying to reinstall it in a clean way.

That's odd advice. The Ubuntu 64-bit CD will not run, much less install, if your system doesn't support 64-bit; so it's physically impossible to install 64-bit Ubuntu on a 32-bit computer.

---

### Post by wardeworth on 2010-04-24
No I dont think it is possible but still not totally sure on this because I wouldnt try it. 
But i prefer you  would do  with a fresh install.All modern Intel chips support 64-bit.
As we know  64bit system uses 64bit compiled packages this is the reason why they are different to the 32bit packages. 
By trying to 64bit from 32 bit you could create many problems. So dont do it unless you want a unstable system.

---

### Post by MButterman on 2010-04-24
Thanks for the info and found it without a problem.

---

### Post by The Thunder Chimp on 2010-04-24
> **3rdalbum said:**
> That's odd advice. The Ubuntu 64-bit CD will not run, much less install, if your system doesn't support 64-bit; so it's physically impossible to install 64-bit Ubuntu on a 32-bit computer.

That's what I meant. If you want to get 64-bit on a 32-bit machine (a machine running a 32-bit OS, but that can run a 64-bit OS, I mean), then the only practical way of doing so would probably be a clean install. I can understand how my phrasing could of lead to confusion with the "Yeah" but that's my bad, I've edited it to "No".

---

