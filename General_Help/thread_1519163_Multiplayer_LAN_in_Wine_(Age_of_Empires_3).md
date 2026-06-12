---
title: "Multiplayer LAN in Wine (Age of Empires 3)"
date: 2010-06-27
forum: General Help
---

### Post by boaty on 2010-06-27
Hey everyone,

I'm trying to play a LAN game of Age of Empires 3 (AD expansion) in Wine, but alas...it does not work.

I'm running Asian Dynasties from PlayOnLinux (if that's important).

I can't think of any information to give you, although I've seen various post around the internet about people inquiring about LAN/multiplayer games running under Wine (with few of them providing any relevant information).

So, I'm wondering, does anybody know anything about running multiplayer/LAN games in Wine?  Let me know if there is some kind of information I can provide.

Thank you in advance.

---

### Post by boaty on 2010-06-28
Bump...I really would like this working.  If anyone could help, it would be appreciated :D

---

### Post by boaty on 2010-07-02
Bump...

Okay, so I found a page on google.  I might need DirectPlay installed.  I'm going this route through winetricks, but currently AOE is failing for some other reason, wine related.  Was there a recent update...?

Edit:

Yeah, I see what you're saying.  In any case, I have everything straightened out.  I did a kernal update and didn't know that I needed to reinstalled proprietary drivers.  I did that (my ati driver), fixed the AOE not starting, now going to try the actual LAN.

---

### Post by 3Miro on 2010-07-02
You can try either the wine subforum or better yet winehq forum. This is not specific to Ubuntu, but rather wine and AoE.

I have done Starcraft I and Diablo II in multilayer mode on local LAN, but those did not require any tweaking, they just ran. Every wine game is specific and the best is to just find someone who has done this before to give you specific instructions. That is why winehq is a better place.

---

### Post by boaty on 2010-07-07
Okay, I forgot about this thread, but now it's all good.  I needed to install DirectPlay via winetricks.  Then in PlayOnLinux, I edited my wine configuration and included dplayx, dpnet, dpnhpast, dpwsockx.  That is also with devenum, msxml4, and quartz which were put there automatically by PlayOnLinux.

---

