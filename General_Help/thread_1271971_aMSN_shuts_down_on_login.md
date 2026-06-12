---
title: "aMSN shuts down on login"
date: 2009-09-21
forum: General Help
---

### Post by Skatespeare on 2009-09-21
As the title says, since a few days when I try to login to MSN using aMSN the program shuts down the second I hit the Sign In button. For no reason whatsoever. I can't think of anything I changed that could cause it and also I tried reinstalling. I use Jaunty. Does this sound familiar to anybody? Does anybody know how to fix it? Thanks in advance.

---

### Post by Claus7 on 2009-09-22
Hello,

it might be because of an update? Do you have any conflicts with the libraries in synaptic package manager? Have you tampered with anything else with your system? I have never faced such a problem before. 

How did you try to reinstall the package? Do you use svn or any stable version?

Regards!

---

### Post by Skatespeare on 2009-09-23
Hey!

The only updates I installed were the recommanded and required ones from the Update Manager. I think it only checks the standard updates from Canonical.

Changes I have recently made can not have anything to do with this issue I think. I installed this file- and webserver in my network which I access from my laptop (the one with the aMSN issue) using vnc. So I installed some vnc package if I remember correctly.

What type of conflicts with the libraries in Synaptic do you mean? I haven't changed much there.

I did reinstall the aMSN package using Synaptic but that didn't help. As far as I know I do not use svn. (Im still somewhat of a Linux-newbie)

---

### Post by 3rdalbum on 2009-09-23
> **Skatespeare said:**
> I did reinstall the aMSN package using Synaptic but that didn't help. As far as I know I do not use svn. (Im still somewhat of a Linux-newbie)

I do realise that you're a newbie, but reinstalling a package does not help in cases like this. The odds are greatly against the program being corrupted on disk (due to it only being writable by root), and if it isn't then reinstalling the package will replace a perfectly-clean copy with another perfectly-clean copy!

A corrupted preferences/configuration file is much more likely, because they are writable by your ordinary user account (and they get written to by the program). Clean out the program's per-user settings, which should be in a hidden folder in your home directory, and you may have some luck.

---

### Post by Claus7 on 2009-09-23
Hello,

there are some things that you could try instead of deleting files at random:

What I would advice you is to open amsn from terminal and see what errors it will produce.

Go to Accessories -> Terminal and in the command prompt type:
amsn

There it should produce some errors if it is crashing. Also it would be nice to know your version of ubuntu and most importantly the version of amsn you are using (you could easily see that from synaptic, since you install amsn from there).

> **3rdalbum said:**
> I do realise that you're a newbie, but reinstalling a package does not help in cases like this. The odds are greatly against the program being corrupted on disk (due to it only being writable by root), and if it isn't then reinstalling the package will replace a perfectly-clean copy with another perfectly-clean copy!

I have not understood the problem of corrupted disk. Sometimes if you mess with a package, reinstalling it from synaptic is an easy and not-conflicting process to bring the things back and running, as I think that you imply talking about the perfect-clean copies.

About deleting files, the only thing that I can think of at the moment, is cleaning a big size photo, that always makes amsn crashing. Other than that, I can not think something else for now.

Regards!

---

