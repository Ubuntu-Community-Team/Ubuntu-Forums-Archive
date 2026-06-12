---
title: "Update Manager doesn't update mplayer"
date: 2011-04-12
forum: General Help
---

### Post by Rocket J Squirrel on 2011-04-12
I have GNOME mplayer installed. Update Manager offers an update for it, "movie player for Unix-like systems," with the following:
[INDENT]Changes for the versions:
2:1.0~rc4~try1.dsfg1-1ubuntu1
2:1.0~rc4~try1.dsfg1-1ubuntu1+medibuntu1
[/INDENT]But when I tell Update Manager to perform the update it says,
[INDENT]**Requires installation of untrusted packages**

The action would require the installation of packages from not authenticated sources.
[/INDENT]Under "details," I read: mplayer. 

And I have a "close" button. mplayer does not receive its update. 

It's a little puzzling. I don't use GNOME mplayer, maybe I should just uninstall it to get rid of this problem?

---

### Post by lithopsian on 2011-04-12
Try to see what the untrusted packages might be.  On the command line type:
```

sudo apt-get upgrade

```
Ideally this will show you mplayer and any dependencies which need to be upgraded with it and you will be able to see if any of them are just plain wrong.  You can also try answering yes if nothing dangerous is going to be upgraded.

Or if there seems to be too many packages that are nothing to do with mplayer:
```

sudo apt-get install mplayer

```

Also, since you have a Medibuntu repository (?), paste the output from:
```

apt-cache policy mplayer

```

---

### Post by Rocket J Squirrel on 2011-04-12
Thank you -- apt-get update solved the problem, Update Manager appears to be satisfied.

---

