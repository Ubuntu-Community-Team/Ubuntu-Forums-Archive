---
title: "The cursed red triangle!"
date: 2011-08-16
forum: General Help
---

### Post by itz_speld_rong on 2011-08-16
It haunts me. It's up in the top "toolbar" of Natty and it has a red exclamation mark inside.

It tells me my "update information is outdated" and so, naturally, I clicked it. It opens my "Update Manager" which tells me "there are no updates to install" and "The package information was last updated 11 days ago."

So I click the "check" button and the following pops up in a window:

Failed to download repository information

Check your Internet connection.
```
W:Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

My internet connection, contrary to the information provided, is fantastic (I've also tried 2 different locations).

What in the world is wrong??!?! :confused:

Thanks Ubuntu Forum!

---

### Post by CatKiller on 2011-08-17
Possibly that PPA is down or doesn't exist any more. You can remove it with Software Sources or through Synaptic.

---

### Post by Elfy on 2011-08-17
[http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/)

Doesn't exist.

User's not been on here either for a few months so you can't ask them.

---

### Post by itz_speld_rong on 2011-08-17
> **CatKiller said:**
> Possibly that PPA is down or doesn't exist any more. You can remove it with Software Sources or through Synaptic.

I'm searching through the SPM and I honestly don't know what I should be removing. I can't really tell (from the error above) what it is what is not longer available to me. I searched "launchpad" and had about 10 matches that are already installed. (I'm not one to just start deleting stuff :P)

---

### Post by CatKiller on 2011-08-17
In Synaptic, Settings -> Repositories -> Other Software. Uncheck the PPA that's causing you problems.

---

### Post by Elfy on 2011-08-17
If you get really confused, run this from a terminal and paste the output and I'm sure someone will have a look. 

```
ls /etc/apt/sources.list.d/
```

---

### Post by itz_speld_rong on 2011-08-18
> **CatKiller said:**
> In Synaptic, Settings -> Repositories -> Other Software. Uncheck the PPA that's causing you problems.

Ah, thank you. Twas as easy as that. I just needed a little guidance. :D

---

