---
title: "Is it possible to clean out an installation?"
date: 2006-03-17
forum: General Help
---

### Post by nchase on 2006-03-17
Hi, I have some problems with Ubuntu, not real problems but just me wanting to get things done and I have a lot of programs with settings installed (many were installed with Automatix) and I just want to get back to the "bare bones" installation and build everything up the way I want to. Is this possible in any way?

---

### Post by FizDev on 2006-03-17
I suppose you could do
```
sudo apt-get remove nameoftheprogram
```
Then you can re-install it the way you want.

---

### Post by nchase on 2006-03-17
Yeah, I was thinking of just going through Synaptic and removing a bunch of stuff...

If I do complete removals, will it leave any "residue"?

---

### Post by aysiu on 2006-03-17
[QUOTE=nchase]Yeah, I was thinking of just going through Synaptic and removing a bunch of stuff...[/quote] You could do that, but it may actually be easier and cleaner to just reinstall Ubuntu, believe it or not.

> 
If I do complete removals, will it leave any "residue"? Yes, but not much--your user config files for that application.

---

### Post by Barrakketh on 2006-03-17
If you remember what time you ran Automatix, it should be quite easy.

```
cat /var/log/dpkg.log | grep ' installed'
```

Will return a list of all packages that have been installed.  If you know what day/time you ran it, then it should be quite easy to take the packages within that range.

If you just want the package names (say, you know which package was the first one installed) you can get the list with:

```
cat /var/log/dpkg.log | grep ' installed' | awk '{print $5}' | uniq
```

If you run apt-get with the --purge switch (needs to be before remove) it'll remove configuration files unless they are in your home directory.

---

