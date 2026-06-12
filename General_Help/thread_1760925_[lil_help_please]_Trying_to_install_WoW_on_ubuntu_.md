---
title: "[lil help please] Trying to install WoW on ubuntu [natty] but the cd's wont show"
date: 2011-05-17
forum: General Help
---

### Post by KCSterling on 2011-05-17
Im trying to install WoW on my machine, but when iput the cd in the drive it doesn't even show up. No windows cd show up for that matter. for some background, i am trying to install it on a Virtual Machine, ( Virtual Box ) and have windows xp on said VM. if you can help, please do. thanks.

---

### Post by KCSterling on 2011-05-17
BuMp

---

### Post by seawolf167 on 2011-05-17
I suggest using Wine instead of a Virtual Machine.

```
sudo apt-get install wine
```

Then follow the instructions [here ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922")(or [here]("https://help.ubuntu.com/community/WorldofWarcraft"))

---

### Post by KCSterling on 2011-05-17
> **seawolf167 said:**
> I suggest using Wine instead of a Virtual Machine.

```
sudo apt-get install wine
```Then follow the instructions [here ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922")(or [here]("https://help.ubuntu.com/community/WorldofWarcraft"))
Thats a problem, when i put in the CD, it wont show up, if i could use wine, i would have, but it wont work for it. I would like to install it from the CD, but icant install something that the machine says isnt even there.

---

### Post by seawolf167 on 2011-05-17
I thought you meant that the Virtual Machine guest OS didn't recognize the cd. But you are saying that your host OS doesn't recognize any cd's either?

---

### Post by KCSterling on 2011-05-17
neither of them do, i got the VM to see if it was because im using ubuntu or not. The VM, nor the host machine recognize the CD's. Ive tried every variation of force mounting there is, and nothing works.

---

### Post by seawolf167 on 2011-05-17
Does the cd drive work when you are booted into Windows? Can you boot off a Live cd in the drive?

---

