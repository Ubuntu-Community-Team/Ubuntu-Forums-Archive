---
title: "failed to fetch cdrom, how bad is it?"
date: 2010-04-25
forum: General Help
---

### Post by hihihi100 on 2010-04-25
Hi there:

when installing tor, after typing the command:

```
sudo apt-get update
```I always get a line reading:

```
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

```what do I have to do?

cheers

---

### Post by 3rdalbum on 2010-04-25
How bad is it? Well, the "W" at the start of the error message stands for "Warning". In other words, it's not really an error message, just some information.

If you don't want to let Apt use your Karmic CD as a source for packages, just untick the CD on the first tab of System > Administration > Software Sources.

---

### Post by hihihi100 on 2010-04-25
I think this is related to the thread:

I get a warning reading:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

and the same window reads:

```
W: Skipping non-exisiting file /cdrom/dists/karmic/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/karmic/restricted/binary-i386/Packages

```

How do I install those packages? synaptic?

---

### Post by dcstar on 2010-04-26
> **hihihi100 said:**
> 
.........
How do I install those packages? synaptic?

Either follow the instructions given to you previously or put the Ubuntu install CD back into the PC.

---

