---
title: "Help needed to identify package"
date: 2009-09-10
forum: General Help
---

### Post by islander_810 on 2009-09-10
Hello all,
recently, I stumbled upon a package which configured the terminal by changing the bg colour, enabled colours, added a few scripts and other small tweaks.

However, as luck has it, I had to reinstall Ubuntu and I forgot which package it was. Now, though I know how to achieve the same effect by manually editing the .bashrc file, I'd really like it if I can get my hands on it thus, saving me hours of trouble to get it... just right

So, if anyone knows of any package that does the above, please let me know

Thanks

---

### Post by SoftwareExplorer on 2009-09-10
Maybe you can find it by putting 'site:packages.ubuntu.com (some words you think are in the packages description)' in google search.

---

### Post by akakingess on 2009-09-11
Also on this note, isn't there a directory that stores all of the downloaded tar's that are installed through synaptic, so that it would be possible to backup that directory in case of a crash or move to new computer, etc. that would have all of the packages that you have installed at least the downloaded (compressed) versions of them in one directory?

---

### Post by islander_810 on 2009-09-11
@SoftwareExplorer I tried searching for it in Synaptic itself but I couldn't come up with anything

@akakingess That's right, in fact that's the first thing I did. Changed the option to preserve all downloaded packages. But as I said earlier, I had to reinstall Ubuntu. I was fiddling around with the partition manager (in windows) and somehow managed to wipe out all the Linux partitions.

---

### Post by akakingess on 2009-09-11
I was actually half asking/half suggesting, but do you know what that directory is, that stores all of those packages that are downloaded for installed?

---

### Post by P4man on 2009-09-11
> **akakingess said:**
> I was actually half asking/half suggesting, but do you know what that directory is, that stores all of those packages that are downloaded for installed?

/var/cache/apt/archives

has a cache of .deb files that you installed.

---

### Post by akakingess on 2009-09-11
Thank you P4man, that's what I am going to be sure and back up this weekend!!!

---

