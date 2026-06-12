---
title: "Cannot install .deb packages no matter what"
date: 2010-02-15
forum: General Help
---

### Post by Objekt on 2010-02-15
Something is very wrong with my system.  Any time I try to run a .deb to install something, I get the following error: 

```
1: Syntax error: newline unexpected
```

What does that mean, and how do I fix it?

---

### Post by audiomick on 2010-02-15
How are you trying to install them? 
I might add, the only way I have used is right click> install with gdebi.

---

### Post by bodhi.zazen on 2010-02-15
What command did you run exactly ? What .deb are you trying to install, where did you get it, and why are you not using apt-get ?

---

### Post by spiderbatdad on 2010-02-15
This was a bug in 9.04. It should have been fixed. Is your installation an upgrade or clean install?
See here for bug report and possible fix. [https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/353117)

---

### Post by Objekt on 2010-02-16
Here are a couple of examples:
```
objekt@objekt-desktop:~/bin$ ls *.deb
acetoneiso_2.1.1-1~getdeb1_amd64.deb     install_flash_player_10_linux.deb
getdeb-repository_0.1-1~getdeb1_all.deb
objekt@objekt-desktop:~/bin$ sudo ./getdeb-repository_0.1-1~getdeb1_all.deb 
[sudo] password for objekt: 
./getdeb-repository_0.1-1~getdeb1_all.deb: 1: Syntax error: newline unexpected
```

Again, with a different *.deb:
```
objekt@objekt-desktop:~/bin$ sudo ./acetoneiso_2.1.1-1~getdeb1_amd64.deb 
./acetoneiso_2.1.1-1~getdeb1_amd64.deb: 1: Syntax error: newline unexpected
```

So it appears I've lost the ability to use .deb packages.  WTF?

---

### Post by mcduck on 2010-02-16
.deb packages are not executable files.

```
sudo dpkg -i nameofyourpackage.deb
```

---

### Post by Objekt on 2010-02-16
Oops.  Could have sworn I ran them that way before.

---

### Post by philinux on 2010-02-16
> **Objekt said:**
> Something is very wrong with my system.  Any time I try to run a .deb to install something, I get the following error: 

```
1: Syntax error: newline unexpected
```

What does that mean, and how do I fix it?

Just double click the deb file.

---

### Post by bodhi.zazen on 2010-02-16
> **Objekt said:**
> Oops.  Could have sworn I ran them that way before.

That is why you need to post the command you run, not just the error message.

---

### Post by Objekt on 2010-02-16
> **philinux said:**
> Just double click the deb file.

Doesn't work.  Of course, I have to right-click and change the downloaded .deb file's properties to "executable," but that apparently is not enough.  Here's how it goes down:

-I double-click.
-Mouse pointer changes to the "spinning wheel"
-A box appears on the taskbar with the name of the package
-After some delay, usually less than a minute, both things disappear, with no apparent result.

That's what happened with both of the .deb packages I mention above, to be specific.  That is why I needed to do it at the command line.

So I guess something else is still broken?

---

### Post by mcduck on 2010-02-16
> **Objekt said:**
> Doesn't work.  Of course, I have to right-click and change the downloaded .deb file's properties to "executable," but that apparently is not enough.  Here's how it goes down:

-I double-click.
-Mouse pointer changes to the "spinning wheel"
-A box appears on the taskbar with the name of the package
-After some delay, usually less than a minute, both things disappear, with no apparent result.

That's what happened with both of the .deb packages I mention above, to be specific.  That is why I needed to do it at the command line.

So I guess something else is still broken?

Don't try setting the executable permission on the packages, like I said they are not executable files. Think of them more as Zip archives (which really isn't that far from the reality). You can't run the .deb package no  matter what you do, you can only open them with other programs (like dpkg or Gdebi).

---

