---
title: "configurations on minimal ubuntu install"
date: 2009-08-02
forum: General Help
---

### Post by david sousa on 2009-08-02
Hey

I've just downloaded, installed and configured ubuntu minimal 9.04.

I've put xorg and xfce4 into it and now i'm able to navigate on desktop through folders and so on...

But there also a few things i want to do now and I need your help:

- I want to configure sound to.
- I want to be able to connect to wireless networks
- I want to access other partitions

And I want to understand more about what i'm doing (some kind of OS for my own use based on ubuntu). So if you know toturials post them please.

Thanks

PS: I'm using toshiba NB100 netbook

---

### Post by paul_in_london on 2009-08-02
Try these:

[http://ubuntuforums.org/showthread.php?t=869659](http://ubuntuforums.org/showthread.php?t=869659)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
[http://ubuntuforums.org/showthread.php?t=968738](http://ubuntuforums.org/showthread.php?t=968738)


You'll want to add yourself to the audio group:

```
sudo usermod -a -G audio [user]
```

Don't know anything about wireless I'm afraid.

Not quite sure what you're asking about accessing partitions. Just mount them from your minimal install?!

---

### Post by david sousa on 2009-08-02
thanks for your reply.

Already configured wireless with wicd

---

### Post by david sousa on 2009-08-02
already know how to access partitions to. 

But still dont know how do i get sound.

O installed alsa but it doesnt work.

Does anyone knows how to solve this?

---

### Post by PhoHammer on 2009-08-02
> **david sousa said:**
> already know how to access partitions to. 

But still dont know how do i get sound.

O installed alsa but it doesnt work.

Does anyone knows how to solve this?

Is it showing the speaker icon in your panel?

---

### Post by david sousa on 2009-08-02
now it is'nt but i can change the volume in  terminal with alsamixer

---

### Post by PhoHammer on 2009-08-02
hmm...
I remember when I did a minimal install with xfce4, it complained of gstreamer plugins
when I attempted to open the volume control in the panel. I installed gstreamer plugins
in synaptic until it worked....

Not exactly a clean fix, but you might try it.

---

### Post by david sousa on 2009-08-02
solved! just needed to 'apt-get install xfce4-mixer'

---

