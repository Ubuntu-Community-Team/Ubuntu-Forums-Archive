---
title: "Fix home folder"
date: 2012-05-17
forum: General Help
---

### Post by t-hawk on 2012-05-17
I'm in a pickle. I've been trying to get something working with Wine and I ended up screwing up my Wine install. I removed it and then proceeded to delete all of the associated folders using the command line for ease of use.

Long story short, I hit "rm-rf" on all of the contents of my home folder and not the one folder I wanted to nuke, so everything is gone. The actual files aren't very important, I can replace them, but I notice that things like my power settings and such are not remembered. I'm guessing there was a config file in there somewhere that got obliterated with everything else.

Is there any way to "repopulate" the folder without completely re-installing Ubuntu?

---

### Post by idoitprone on 2012-05-18
> **t-hawk said:**
> I'm in a pickle. I've been trying to get something working with Wine and I ended up screwing up my Wine install. I removed it and then proceeded to delete all of the associated folders using the command line for ease of use.

Long story short, I hit "rm-rf" on all of the contents of my home folder and not the one folder I wanted to nuke, so everything is gone. The actual files aren't very important, I can replace them, but I notice that things like my power settings and such are not remembered. I'm guessing there was a config file in there somewhere that got obliterated with everything else.

Is there any way to "repopulate" the folder without completely re-installing Ubuntu?

It does it all by itself, but you would want to make your basic folders and .bashrc

In fact I the idoit that does it all the times. My computer is muted, time to do rm r
```
mkdir Videos Documents Pictures Public Desktop Downloads Music
``````
cp /etc/skel/.bashrc ~/ 
```

---

