---
title: "update-manager enforcing apps ?"
date: 2010-05-19
forum: General Help
---

### Post by jissouille on 2010-05-19
I'm a happy Karmic/64 user. Today, update-manager wants to (re)install evolution, empathy and ubuntuone though I have (deliberately) removed them from my system.
I have seen, when upgrading other computers to Lucid, that these programs are reinstalled during the process and I thought it was "part of the big process", no big deal to remove them afterwards.
I don't understand why I have to let apt* install things I don't want and of course remove them afterwards. I thought Debian-derived distros had something called "alternatives" that would let the USER choose his mail user agent once for all.
So I have 2 questions :
- why is this happening ?
- can I prevent installation of these programs by blacklisting them somewhere in apt (a bit like the "hold" feature) ?

Thanks for your help,

---

### Post by dcstar on 2010-05-19
> **jissouille said:**
> I'm a happy Karmic/64 user. Today, update-manager wants to (re)install evolution, empathy and ubuntuone though I have (deliberately) removed them from my system.
I have seen, when upgrading other computers to Lucid, that these programs are reinstalled during the process and I thought it was "part of the big process", no big deal to remove them afterwards.
I don't understand why I have to let apt* install things I don't want and of course remove them afterwards. I thought Debian-derived distros had something called "alternatives" that would let the USER choose his mail user agent once for all.
So I have 2 questions :
- why is this happening ?
- can I prevent installation of these programs by blacklisting them somewhere in apt (a bit like the "hold" feature) ?

Thanks for your help,

All these apps are part of meta-packages that Ubuntu installs because components of them give functionality.

You are not **forced** to use them, just leave them be and use whatever you want to.

---

### Post by jissouille on 2010-05-19
> **dcstar said:**
> All these apps are part of meta-packages that Ubuntu installs because components of them give functionality.

I thought "functionalities" were dependant on alternatives rather than enforced programs. Also, it seems that evolution is "Recommended" by the ubuntu-desktop task/meta-package, not "Depends" on it. I'm a bit confused...

> **dcstar said:**
> You are not **forced** to use them, just leave them be and use whatever you want to.

This reminds me of my ancient "OS"... Apart from taking up some disk space, upgrade time, etc., I will have to cleanup/reconfigure indicator-applet after each upgrade of the unwanted packages (since indicator-applet requires changes in /usr/share, these will be overwritten -- see [https://bugs.launchpad.net/indicator-applet/+bug/540953](https://bugs.launchpad.net/indicator-applet/+bug/540953)).

*I* can deal with the extra hassle (though I consider it a design bug). But the persons I help installing/using Ubuntu can't. And you can imagine repeating this on every computer will become tedious.

Thanks for your help.

---

