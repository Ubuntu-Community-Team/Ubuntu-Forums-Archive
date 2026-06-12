---
title: "Can't uninstall zsnes emulator?"
date: 2010-03-03
forum: General Help
---

### Post by typofreak183 on 2010-03-03
I'm running Ubuntu 9.10 on a Dell Inspiron 1501. The other day I installed a super nintendo emulator (ZSNES) to play around, but decided I didn't like it and cannot unistall it.

I am an administrator on this machine. I have tried uninstalling from the synaptic package manager (crash) and the ubuntu software center. In the ubuntu software center, the error I get is:

```
installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/available' near line 2 package 'xserver-xorg-input-vmmouse': 
 value for `status' field not allowed in this context
```Is there something I'm not doing right? Forgive the newbieness, as always:)

Thanks!
typofreak

---

### Post by Agent ME on 2010-03-03
Can you give us a link to the package you installed?

---

### Post by typofreak183 on 2010-03-04
Sorry my reply has taken so long, I just found out I had a corrupt filesystem:)

I don't know what you want exactly, I just found the package in the ubuntu software center after searching for ZSNES.

---

### Post by typofreak183 on 2010-03-04
The version I appear to have on my machine can be downloaded here:
[http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2](http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2)

[B]EDIT: I appear to be having a TON of problems caused by this stupid *xserver-xorg-input-vmmouse*.
Can you help me uninstall it?[/B]

```
sudo apt-get remove xserver-xorg-input-vmmouse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-xorg-input-all xserver-xorg-input-vmmouse
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 176kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/available' near line 2 package 'xserver-xorg-input-vmmouse':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by lykwydchykyn on 2010-03-04
Type this into a terminal and post the full output here:

```

sudo apt-get remove zsnes

```

Sounds like corrupt packaging script is preventing APT from working properly, could be related to the corrupt filesystem.

---

### Post by typofreak183 on 2010-03-04
> **lykwydchykyn said:**
> Type this into a terminal and post the full output here:

```

sudo apt-get remove zsnes

```Sounds like corrupt packaging script is preventing APT from working properly, could be related to the corrupt filesystem.
```
ethan@ethan-laptop:~$ sudo apt-get remove zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libao2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  zsnes
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,260kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/available' near line 2 package 'xserver-xorg-input-vmmouse':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

```I can no longer install or uninstall ANYTHING.:evil:

While I was away, my dad said he fixed the filesystem by running some kind of filecheck. Is it still corrupt?

---

### Post by typofreak183 on 2010-03-04
I've just run across a guide to using the fsck utility. Would this solve the problem?

---

### Post by lykwydchykyn on 2010-03-04
> **typofreak183 said:**
> I've just run across a guide to using the fsck utility. Would this solve the problem?

fsck can fix filesystem corruption and work around bad sectors on the hard drive.  I don't *think* it will fix corrupted files, because it has no way to know what the data was to begin with.

Try these commands:
```

sudo dpkg --clear-avail
sudo apt-get update

```

---

### Post by typofreak183 on 2010-03-04
> **lykwydchykyn said:**
> fsck can fix filesystem corruption and work around bad sectors on the hard drive.  I don't *think* it will fix corrupted files, because it has no way to know what the data was to begin with.

Try these commands:
```

sudo dpkg --clear-avail
sudo apt-get update

```
sudo dpkg --clear-avail && sudo apt-get update

worked. Thanks!:D

---

