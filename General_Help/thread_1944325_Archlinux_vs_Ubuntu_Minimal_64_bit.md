---
title: "Archlinux vs Ubuntu Minimal 64 bit"
date: 2012-03-21
forum: General Help
---

### Post by melodosgr on 2012-03-21
Just wondering, since I'll be using a Minimal Openbox Config, what could be the difference between those two with the default kernel since I'll be using 64 bit? I know that Arch packages are optimised for i686 but I'm I'll go with 64 bit packages.

I am leaning a bit more on the minimal Ubuntu side, cause of variety of packages, But I am a bit hesitant about the way I have to do system upgrades on ubuntu.. I also develop android apps and I would prefer to go the Ubuntu way since it is preferred by Google.

Thanks.

---

### Post by Cheesemill on 2012-03-21
At the end it's all a matter of personal choice, but I'll try and give you a few things to think about.

**Packaging** - Where Ubuntu uses apt-get, Arch uses pacman for package management, they work in basically the same way but with slightly different syntax, for example:
```
pacman -Sy
```To update the package list.
```
pacman -S <packagename>
```To install a package.
Pacman takes care of all dependencies for you just like apt-get.

**Upgrading** - As Arch is a rolling release you avoid the 6 monthly (or 2 year for LTS) upgrade cycle. A simple 'pacman -Syu' updates all packages on your system to the very latest versions, your system is always using bleeding edge software.
This can occasionally lead to breakage so although I'd probably never use Arch on a production system, it's fine for workstation use though. As long as you keep an eye out for possible issues on their website and look at exactly what's being upgraded you should be fine (I've had this happen once in 12 months so far).
This can be a problem if you are trying to use arch as a development environment though, as you would usually want to target a specific version of MySQL, Python etc. but these are always being updated to the latest versions.

**Source Code** - As far as possible Arch uses unpatched source code directly from upstream. This means that any bugs are more likely to be able to be fixed by the software devs themselves instead of it being a patching issue (Ubuntu patches the code for a lot of it's packages to fit in with the Ubuntu way of doing things).


As you install Arch from the ground up only adding what you need then I feel it tends to be quicker than Ubuntu due to a lack of excess baggage. Openbox on Arch absolutely flies on modern hardware with everything happening pretty much instantly.

Installation can be tricky if you're only used to graphical installs, but follow the Beginners Guide to the letter and you can't really go wrong. Because of this you also start with a system on which you already know the configuration intimately.

Also pretty much anything you need to know how to do is given a detailed explanation in the wiki, it's one of the best I've ever seen. This does however lead to their forums being a bit hard on newbies, if the answer is in the wiki or already answered in the forums then you'll be told just that in no uncertain terms. Ask about a problem which you've already researched though and the forum members are very knowledgeable.

I've been running Arch 64 + Gnome Shell for 12 months now as the only install on my rig and am absolutely loving it. However I still prefer Ubuntu for business use because it is a lot easier to support, you can install an LTS and be done with it for 5 years

---

### Post by melodosgr on 2012-03-21
> **Cheesemill said:**
> At the end it's all a matter of personal choice, but I'll try and give you a few things to think about.

**Packaging** - Where Ubuntu uses apt-get, Arch uses pacman for package management, they work in basically the same way but with slightly different syntax, for example:
```
pacman -Sy
```To update the package list.
```
pacman -S <packagename>
```To install a package.
Pacman takes care of all dependencies for you just like apt-get.

**Upgrading** - As Arch is a rolling release you avoid the 6 monthly (or 2 year for LTS) upgrade cycle. A simple 'pacman -Syu' updates all packages on your system to the very latest versions, your system is always using bleeding edge software.
This can occasionally lead to breakage so although I'd probably never use Arch on a production system, it's fine for workstation use though. As long as you keep an eye out for possible issues on their website and look at exactly what's being upgraded you should be fine (I've had this happen once in 12 months so far).
This can be a problem if you are trying to use arch as a development environment though, as you would usually want to target a specific version of MySQL, Python etc. but these are always being updated to the latest versions.

**Source Code** - As far as possible Arch uses unpatched source code directly from upstream. This means that any bugs are more likely to be able to be fixed by the software devs themselves instead of it being a patching issue (Ubuntu patches the code for a lot of it's packages to fit in with the Ubuntu way of doing things).


As you install Arch from the ground up only adding what you need then I feel it tends to be quicker than Ubuntu due to a lack of excess baggage. Openbox on Arch absolutely flies on modern hardware with everything happening pretty much instantly.

Installation can be tricky if you're only used to graphical installs, but follow the Beginners Guide to the letter and you can't really go wrong. Because of this you also start with a system on which you already know the configuration intimately.

Also pretty much anything you need to know how to do is given a detailed explanation in the wiki, it's one of the best I've ever seen. This does however lead to their forums being a bit hard on newbies, if the answer is in the wiki or already answered in the forums then you'll be told just that in no uncertain terms. Ask about a problem which you've already researched though and the forum members are very knowledgeable.

I've been running Arch 64 + Gnome Shell for 12 months now as the only install on my rig and am absolutely loving it. However I still prefer Ubuntu for business use because it is a lot easier to support, you can install an LTS and be done with it for 5 years

I'm an Archlinux User myself. All I'm asking is if there are any crucial differences, performance wise, provided I use the Alternate Installation disk and install a minimal system without many deamons running, just like on Arch.

---

