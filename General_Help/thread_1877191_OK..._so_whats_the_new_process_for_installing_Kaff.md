---
title: "OK... so whats the new process for installing Kaffeine  in ubuntu?"
date: 2011-11-07
forum: General Help
---

### Post by cptrohn on 2011-11-07
I went to the Kaffeine Community documentation using these commands..

```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo apt-get install kaffeine libxine1 libxine1-all-plugins phonon-backend-xine
```

Used to work no problems at all... (need it for my TV Tuner)

Now when I apply the 2nd line of code I get this error..

```
Package phonon-backend-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'phonon-backend-xine' has no installation candidate

```

So, what did the 'phonon-backend-xine' change to or where can I get it?

---

### Post by searchfgold6789 on 2011-11-07
Works for me.
I attached the .deb if you need it.
 - search
EDIT: The uploader is not working. Will try again later.

---

### Post by cptrohn on 2011-12-15
Doesn't work for me at all in 11.10 no matter what...  get the same message about the phonon backend. :(

---

### Post by lykwydchykyn on 2011-12-15
Have you tried just installing kaffeine by itself and letting the package work out its own dependencies?

---

### Post by oldos2er on 2011-12-15
[http://packages.ubuntu.com/lucid/phonon-backend-xine](http://packages.ubuntu.com/lucid/phonon-backend-xine)

---

### Post by cptrohn on 2011-12-15
> **oldos2er said:**
> [http://packages.ubuntu.com/lucid/phonon-backend-xine](http://packages.ubuntu.com/lucid/phonon-backend-xine)

Thanks so much!  Will have to give it a go again!

---

