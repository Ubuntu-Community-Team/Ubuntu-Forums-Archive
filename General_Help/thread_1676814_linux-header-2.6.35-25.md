---
title: "linux-header-2.6.35-25"
date: 2011-01-27
forum: General Help
---

### Post by shug0131 on 2011-01-27
When I originally set up my partitions I gave /boot a meagre 21.2MB, as per some poor advice I read somewhere.

Whenever the linux-header package is upgraded, it doesn't clean out older versions and quickly runs of space. So I have to manually move all but the current version files elsewhere. If I don't do this the update manager tells me it won't install until I've made the space

This worked OK, until the latest upgrade to 2.6.35-25, when even this didn't provide enough space. 

So I moved the current files ( > sudo mv /boot/*-24-* ~) and tried running the update manager. The installation failed :(

I was able to resurrect my PC by running a CD-boot version of ubuntu to access the hard disk and moving back the 2.6.35-24 files  into /boot. 

This allows the PC to start up and run again, but the boot-up time has more than doubled, and any attempts I make to reinstall the linux-header package, either version, fail. 

What can I do about this????

Thanks Simon

---

### Post by lukeiamyourfather on 2011-01-27
The partitions can be moved and resized from the live disc to make the boot partition bigger. Though be sure that everything is backed up just in case... :shock:

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

---

### Post by AlphaLexman on 2011-01-27
LifeHacker has a script [here]("http://www.lifehacker.com.au/2010/12/quickly-uninstall-old-linux-kernels-with-a-bash-script/") to remove all kernels except the two newest versions.

---

### Post by lukeiamyourfather on 2011-01-27
> **AlphaLexman said:**
> LifeHacker has a script [here]("http://www.lifehacker.com.au/2010/12/quickly-uninstall-old-linux-kernels-with-a-bash-script/") to remove all kernels except the two newest versions.

> **shug0131 said:**
> 
This worked OK, until the latest upgrade to 2.6.35-25, when even this didn't provide enough space.

Cool script, but no go in this situation. Generally speaking why is there even a boot partition? It serves no purpose in modern Linux distributions as far as I know.

---

### Post by AlphaLexman on 2011-01-27
> **lukeiamyourfather said:**
> Generally speaking why is there even a boot partition?
By default, ubuntu does NOT create a /boot partition, the OP did that on their own, and realized the size mistake...

I was just trying to help a user in a tough situation!

---

