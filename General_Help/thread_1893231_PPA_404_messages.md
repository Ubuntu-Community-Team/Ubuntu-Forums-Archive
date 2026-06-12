---
title: "PPA 404 messages"
date: 2011-12-09
forum: General Help
---

### Post by Kodeine on 2011-12-09
Hello!

So on our 11.04 ubuntu laptop every time we try to check for updates it gives the following message.
```
W:Failed to fetch http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

What is this PPA and should I be removing it to get updates? After it states this error message no updates are shown in update manager despite the last update was 59 days ago.

---

### Post by bluexrider on 2011-12-09
> **Kodeine said:**
> Hello!

So on our 11.04 ubuntu laptop every time we try to check for updates it gives the following message.
```
W:Failed to fetch http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```What is this PPA and should I be removing it to get updates? After it states this error message no updates are shown in update manager despite the last update was 59 days ago.

Sounds like you are unaware of what that is.

If you feel like not using the repository then open "software sources" and under the "other software" tab scroll until you find that entry that matches  and uncheck it, edit or remove it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by H_a_D_3_z on 2011-12-09
Yeah, I have this error also.  I have given up on it (for now), but there is a nice program called "y-ppa-manager" it allows you to add, manage & remove them using a gui; if you prefer that route.  If your a terminal type of person, then ppa-purge is probably better.  Good Luck

---

### Post by Kodeine on 2011-12-09
Okay I'll go ahead and remove it. I hesitated to do so before asking as I didn't know what it was. Didn't know if it was vital. What is it out of curiosity? It's not me who uses the laptop and I can't remember adding any additional PPA's.

---

