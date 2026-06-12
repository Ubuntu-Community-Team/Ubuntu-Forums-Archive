---
title: "Set apt default manager"
date: 2012-06-22
forum: General Help
---

### Post by Philly Idol on 2012-06-22
Hey all,

I've searched, but as Pangolin is so new, I'm thinking this might not have been 'completely' address (my apologies of course if I'm dead wrong ;) ).

I just installed Pangolin and I don't like the Software Center, as it seems to chew up my system resources when it's running (RAM, CPU, etc.) , so I'm trying to open an 'apt' package and it's nicely prompting me to pick the application I want to use to open/install it.

The problem I'm having is how (or where to point it) to use the Synaptic Package Manager and set it as the default, so if someone can assist, it wold be much appreciated :D :D.

Thanks

---

### Post by cortman on 2012-06-22
> **Philly Idol said:**
> Hey all,

I've searched, but as Pangolin is so new, I'm thinking this might not have been 'completely' address (my apologies of course if I'm dead wrong ;) ).

I just installed Pangolin and I don't like the Software Center, as it seems to chew up my system resources when it's running (RAM, CPU, etc.) , so I'm trying to open an 'apt' package and it's nicely prompting me to pick the application I want to use to open/install it.

The problem I'm having is how (or where to point it) to use the Synaptic Package Manager and set it as the default, so if someone can assist, it wold be much appreciated :D :D.

Thanks

I assume you're talking about a .deb package.
You can right click and select "open with", and choose Synaptic.
Or you can open a terminal and run

```
sudo dpkg -i package_name
```

and run it that way.

---

### Post by LewisTM on 2012-06-22
Apt and Synaptic only install remote packages, not local .deb files.
For that you need gdebi
> **simple tool to install deb files - GNOME GUI**
gdebi lets you install local deb packages resolving and installing
its dependencies. apt does the same, but only for remote (http, ftp)located packages.
Then use Nautilus to associate .deb files with gdebi (I think this is done automatically as soon as you install gdebi).

Cheers!

---

### Post by jmore9 on 2012-06-22
You have to install it.  it is not installed by default.  That is the second thing i do when i intalled ubuntu 12.04.

sudo apt-get install Synaptic

---

