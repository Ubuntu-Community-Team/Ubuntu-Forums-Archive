---
title: "Cannot install any packages"
date: 2011-07-29
forum: General Help
---

### Post by Hatsune Miku on 2011-07-29
Alright everyone; more bugs for you, was trying to install skype 64bit, using dpkg; i got an error saying that i needed to install 32bit libraries. I went to try to install these for this not to work, so i gave up and tried to install something else today and the apt-get system will not let me install anything complaining i need to install the dependencies for skype first... I am at wits end. Any help please?

Here is the error:

```
You might want to run apt-get -f install to correct these:

The following packages have unmet dependencies:
Conky : Depends: conky-all but its not going to be installed
Skype : Depends: lib32astdc++6 but its is not going to be installed
depend: lib32asound2 but its not going to be installed
depends: ia32-libs but it is not going to be installed
depends: lib32gcc1 but it is not going to be installed
depends: ia32-libs-gtk but it is not going to be installed
E: unmet dependencies. Try 'apt-get 0f install with no packages (or specify a solution)
```

Tried doing apt-get install -f, gave me the same output as this.

EDIT: Now it works, sorry to waste another thread guys... :/

If a moderator could please delete this.

---

