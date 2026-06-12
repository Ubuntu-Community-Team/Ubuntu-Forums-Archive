---
title: "flash update troubles"
date: 2010-02-16
forum: General Help
---

### Post by dog-soldier on 2010-02-16
yesterday there was a adobe update that messed everything up. i got the update and when i went to facebook i couldnt play a couple of the games. i kept getting a link to update flash player. i would do that and still nothing. i had to uninstall and go to the repos and get it there before it would work. 
now today i got the same update for adobe and im scared to get it since i had problems with it already.

did anyone else have problems with the adobe update?

im using 8.04LTS

---

### Post by dco1 on 2010-02-16
Same problem.  I'm using 8.04, 64-bit.

---

### Post by Elktro on 2010-02-17
I can confirm this adobe flash problem with 32-bit 8.04 Ubuntu.

---

### Post by Elktro on 2010-02-17
I could fix the adobe flash plugin by first removing it:

```

#sudo apt-get remove adobe-flashplugin

```

And then installing it again.

```
#sudo apt-get install adobe-flashplugin
```

---

