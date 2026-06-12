---
title: "Lucid Lynx unable to remove package"
date: 2010-05-17
forum: General Help
---

### Post by aust77 on 2010-05-17
Hello,

I recently ran "sudo apt-get autoremove" in the terminal and I was given an error message citing the following:

```
E: libtaglib2.0-cil: subprocess installed pre-removal script returned error exit status 2

```I believe this is a result of a failed Banshee Media Player installation that left the specific package installed. I ended up removing Banshee entirely. I have tried using Synaptic Package Manager and Computer Janitor to remove the package, but neither has worked, both returned the error exit status 2 message. Computer stats are in my signature.

Thanks in advance,


aust77

---

### Post by dcstar on 2010-05-18
> **aust77 said:**
> Hello,

I recently ran "sudo apt-get autoremove" in the terminal and I was given an error message citing the following:

```
E: libtaglib2.0-cil: subprocess installed pre-removal script returned error exit status 2

```I believe this is a result of a failed Banshee Media Player installation that left the specific package installed. I ended up removing Banshee entirely. I have tried using Synaptic Package Manager and Computer Janitor to remove the package, but neither has worked, both returned the error exit status 2 message. Computer stats are in my signature.


If you have improperly installed packages then delete the cache file of the package, install it again and then uninstall it.

---

### Post by ndstate on 2010-05-18
I am having a similar problem.  How do you delete the cache file of the package?

---

### Post by ndstate on 2010-05-18
I dont know if its applicable to your situation or not, but I had similar problems and [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096) fixed it for me.

Good luck

---

