---
title: "Gnome 3 application not launching because of path environment variable"
date: 2011-04-26
forum: General Help
---

### Post by wolfen69 on 2011-04-26
I am using gnome 3 and I installed neverputt from the repos, and when I click the icon in applications, it doesn't launch. Running it from the terminal gives:
```
Command 'neverputt' is available in '/usr/games/neverputt'
The command could not be located because '/usr/games' is not included in the PATH environment variable.

```
I know what this means, but I'm not real familiar with gnome 3 yet, and just need to know where to go to fix this. Btw, running:
```
/usr/games/neverputt
```
the game starts up just fine.

---

### Post by Krytarik on 2011-04-26
Check the PATH variable in "/etc/environment", mine indeed includes "/usr/games", I didn't modify it:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
[https://help.ubuntu.com/community/EnvironmentVariables#System-wide%20environment%20variables](https://help.ubuntu.com/community/EnvironmentVariables#System-wide%20environment%20variables)

Greetings.

---

### Post by wolfen69 on 2011-04-26
Thanks for the reply. My /etc/environment looks the same as yours.

---

### Post by Krytarik on 2011-04-26
Do you have any of the other files mentioned in the guide I linked to at your system/user profile, that may be overriding the variable set in "/etc/environment"?

---

### Post by wolfen69 on 2011-04-26
To be honest, I wouldn't know what to look for as far as anything overriding. 

But it's obvious when clicking the icon, it's not linking to /usr/games/neverputt

In gnome2, I could change the path, but I'm not sure about gnome3.

---

### Post by Krytarik on 2011-04-27
Just check if any of the files mentioned are present at your system, and if so, if it, too, states a PATH variable.

A simple workaround would be just to symlink the files/dirs in "/usr/games" to "/usr/bin", for example, at my system there are just 7 files. You can use Nautilus for that, just mark them all and drag them over while holding down the Alt key, when you release the mouse button, choose "Link Here", of course, you need to run Nautilus with 'gksu' therefore.

You can also try to set a user specific PATH variable by setting up a "~/.profile", thus overriding whatever overrides "/etc/environment" in the first place.

---

### Post by wolfen69 on 2011-04-27
Creating a symlink didn't work, but I thought I would just try to cut and paste the neverputt file into /usr/bin/ and it worked. Thanks a lot for your help!

---

