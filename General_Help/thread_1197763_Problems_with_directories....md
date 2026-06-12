---
title: "Problems with directories..."
date: 2009-06-26
forum: General Help
---

### Post by MonikerX on 2009-06-26
Alright; so basically I installed the dj program Mixxx.
When I attempt to run the program it says that the skins directory is missing.
I've been trying to move the directory.... but to no avail.
I think my problem is directories... I have the folder I need to move on my desktop. For example. I have...

Desktop/mixxx/skins ( A bunch of files in said skins folder )
and I need to move THAT to...
/usr/share/mixxx

But for some reason when I try to use the sudo mv command it claims there is no such directory as where skins is. I cannot drag and drop as I am not logged in as root.

Can someone help me? I'd love to just drag and drop the thing. I'm a semi experience computer user and nobody else has access to my computer... I just want to have the ease of drag and dropping folders this one rare time. :P

Anyways; assistance is greatly appreciated. :confused:

---

### Post by MonikerX on 2009-06-26
bump... A lot of replies to other posts...
I'd figure this is a relatively SIMPLE question to answer. 
If someone can help me; I'll know how to move any folder/directory at any time.
Thank you.

---

### Post by michy99 on 2009-06-26
You can open nautilus as root with```
gksudo nautilus
```Then you should be able to drag and drop. Just be sure to close it when you're done so you don't accidentally mess anything up.

---

### Post by MonikerX on 2009-06-26
Thanks. When I use that command a window popped up for my password. I put it in but then nothing happened... What was supposed to take place?

EDIT: I'm a moron. Nautilus was not installed. Installing now.

---

### Post by michy99 on 2009-06-26
Actually, that was my fault for not noticing that you are running Xubuntu. Nautilus is the file manager in Ubuntu. I'm sure that same thing will work for whatever file manager Xubuntu uses.

---

