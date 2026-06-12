---
title: "upgrading from beta?"
date: 2010-04-30
forum: General Help
---

### Post by gordong11 on 2010-04-30
I donwloaded Lucid beta 2, and have been doing updates, but have not done any updates for about a week. This may be a dumb question, but when i do update-manager -d, no new distribution is being detected, is this right? I was expecting to have to upgrade, like I did from beta 1 to beta 2. I feel like I"m missing something. Lol

---

### Post by philinux on 2010-04-30
> **gordong11 said:**
> I donwloaded Lucid beta 2, and have been doing updates, but have not done any updates for about a week. This may be a dumb question, but when i do update-manager -d, no new distribution is being detected, is this right? I was expecting to have to upgrade, like I did from beta 1 to beta 2. I feel like I"m missing something. Lol

Either just use update manager or the code below.

```
sudo apt-get update && sudo apt-get upgrade
```

update-manager -d upgrades to the **next release**. Seeing as that would be 10.10 maverick meerkat, it doesn't exist yet.

---

### Post by gordong11 on 2010-04-30
Thanks. I guess I have all the final packagaes from my last update over a week ago. Nothing new.

I still have the ugly ubuntu splash screen and start-up/shutdown. That can't be right? LOL. Usually they clean this up for final release.

---

### Post by gordong11 on 2010-04-30
Still didn't work. I guess i have the final version afterall. I find it difficult to believe the they would aweful startup/shutdown Ubuntu splashscreen the way it is. I suppose i can change the resolution, but it's still ugly and unfinished looking.

---

### Post by DawieS on 2010-04-30
I read somewhere on the forums that the updates will be stalled for a day or two, to allow most of the downloading traffic to get back to normal. The servers and various mirrors must have taken a lot of strain today...:smile::smile:

---

