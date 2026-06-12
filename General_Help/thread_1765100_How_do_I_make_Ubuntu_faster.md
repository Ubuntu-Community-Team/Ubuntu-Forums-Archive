---
title: "How do I make Ubuntu faster?"
date: 2011-05-22
forum: General Help
---

### Post by 0Io1 on 2011-05-22
I installed preload, I unchecked all startup applications, I uninstalled programs I wouldn't use.

Any other tips for a faster Ubuntu?

---

### Post by wojox on 2011-05-22
Which version?

---

### Post by tgm4883 on 2011-05-22
> **0Io1 said:**
> I installed preload, I unchecked all startup applications, I uninstalled programs I wouldn't use.

Any other tips for a faster Ubuntu?

Define faster. What I mean is, what do you want to be faster?

---

### Post by linuxinstalledfromhdd on 2011-05-22
Minimal installation of Lubuntu using pure Openbox/XFCE environment.  You can't get much faster than that.

---

### Post by 0Io1 on 2011-05-22
I'm using Ubuntu 11.04. 

What do I want to be faster? The whole system I suppose. I want programs to launch faster, etc.

---

### Post by tgm4883 on 2011-05-22
> **0Io1 said:**
> I'm using Ubuntu 11.04. 

What do I want to be faster? The whole system I suppose. I want programs to launch faster, etc.

IIRC, If you want applications to load faster than unchecking system startup items is the opposite of what you want to do. If you have certain items load at startup then when you want to use them they are quick to load.

On the flip side, maybe you are seeing not normal performance. For instance, on a default install it only takes 1-1.5 seconds for Firefox to load for me. I don't feel the need for it to be any faster than that.

Then of course if you really want to look at performance, you could always go the route of Gentoo.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Crunchbang Statler flies. It's in alpha though.  Pure Debian too.

---

### Post by lithopsian on 2011-05-22
Statler is no longer alpha.  It went live in February shortly after Debian Squeeze was released.  The previous version of Crunchbang was based on Ubuntu, but Jaunty so no longer supported in any way.

---

### Post by linuxinstalledfromhdd on 2011-05-22
that's true.  They have wonderful support just like here. :)

---

### Post by 0Io1 on 2011-05-22
> **tgm4883 said:**
> If you want applications to load faster than unchecking system startup items is the opposite of what you want to do. If you have certain items load at startup then when you want to use them they are quick to load.

How do I make Google Chrome launch on startup? I only use Google Chrome.

---

### Post by tgalati4 on 2011-05-22
Recompile your kernel--take out stuff that you don't use.

---

### Post by Rasa1111 on 2011-05-22
Ubuntu works super fast, and things work instantaneously for me when i click them..
\ I can;t imagine needing to make it faster.
(how do you even get faster than instantaneous?) lol
:P

---

### Post by oldos2er on 2011-05-22
> **0Io1 said:**
> I installed preload, I unchecked all startup applications, I uninstalled programs I wouldn't use.

Any other tips for a faster Ubuntu?

What are your hardware specs?

---

### Post by wojox on 2011-05-22
> **0Io1 said:**
> How do I make Google Chrome launch on startup? I only use Google Chrome.

Add it to the Start Up GUI you had edited. For Execute put in 

```
google-chrome %U
```

---

