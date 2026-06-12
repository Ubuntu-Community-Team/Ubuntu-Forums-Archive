---
title: "Format a mp3-player"
date: 2006-02-14
forum: General Help
---

### Post by IronToad on 2006-02-14
Hi! 
Is there anyway to format my mp3-player?
/Thanks

---

### Post by gremlin hunter on 2006-02-14
It depends on the MP3 player.

---

### Post by IronToad on 2006-02-14
I meant someway to format it from ubuntu, like you could click on it on windows and then select format.

---

### Post by gremlin hunter on 2006-02-14
Firstly MP3 players work in all sorts of ways. This could screw it up, make it explode or cause an apocalypse. It is just as likely that my instructions are incorrect.

A model name would be nice.

If possible could you just not delete all songs?

Install gparted (sudo apt-get install gparted or via Synaptic). Then choose the device from the drop down list on the right (likely to be /dev/sd*). Then right click on the partition and if necessary unmount it. Take note of the filesystem. Then right click and choose Format to > and choose the correct filesystem. Voila.

---

### Post by IronToad on 2006-02-14
thanks for ur answer:D The reason that I wanted to format my mp3 player was that a lot of mb is suddenly missing. The mp3-player is a 128 mb and when i emptied the mp3-player it said that I only had 69 mb left.

---

### Post by IronToad on 2006-02-15
yay!!! it's working again, my mp3-player is working properly when i formatted it.'
Thanks very much for ur help:D

---

### Post by gremlin hunter on 2006-02-15
No problem. Glad to help.

---

