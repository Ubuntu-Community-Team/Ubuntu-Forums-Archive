---
title: "sound from display :1 redirected to :0 ???"
date: 2010-01-13
forum: General Help
---

### Post by jenkinbr on 2010-01-13
I'm having a small problem with sound on a different x server

I created an .xinitrc in my home directory with the following:
```
exec nexuiz
```

I then use the command ```
startx -- :1
``` and it starts up as it should, nexuiz ( a multiplayer first person shooter ) starts up on vt9, and displays fine. However, I do not hear the sound for the game when I am on that xserver, and I don't hear it until I switch back to vt7.

How do I go about fixing this so that my sound for the game plays when it should?

---

### Post by roadtripdave on 2010-01-13
Maybe try using
```
sudo startx -- :1
```

Or maybe try checking "Use audio devices" under User Privileges in User and Groups.

Regards

---

### Post by jenkinbr on 2010-01-13
> **roadtripdave said:**
> Maybe try using
```
sudo startx -- :1
```

In my honest opinion, bad idea.

I don't want to run the game as root, it could be a security issue

> **roadtripdave said:**
> Or maybe try checking "Use audio devices" under User Privileges in User and Groups.

Regards

I'll give this a try in a few minutes and see if that helps :)

[edit]No such luck :([/edit]

---

### Post by jenkinbr on 2010-01-14
~BUMP!~

Still no sound when I'm viewing vt9 (screen :1)...

---

### Post by jenkinbr on 2010-01-19
bump :(

---

