---
title: "Synpatic Package  Manager Error"
date: 2011-09-26
forum: General Help
---

### Post by Maz7006 on 2011-09-26
Hello

I did a fresh install of Ubuntu 11.04 via Wubi and i get the following error whilst trying to install anything via terminal using apt-get install and the same error occurs when i try opening the the Synaptic Package Manager

The error: 

E: Encountered a section with no package 
E: Problem With MergeList /var/lib/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E:_cache->open()failed,please report.

How can i fix this ? Thank you.

---

### Post by matt_symes on 2011-09-26
Hi
> 
/var/lib/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina  ry-i386_PackagesShouldn't that be 
```

/var/lib/**apt**/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
```?

Try deleting the files.
```

sudo rm -rf /var/lib/apt/lists/*
```

...then update...```
sudo apt-get update
```Kind regards

---

### Post by Maz7006 on 2011-09-26
> **matt_symes said:**
> Hi
Shouldn't that be 
```

/var/lib/**apt**/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
```?

Try deleting the files.


Yes you are correct.

I typed it out since it would be faster than uploading (yes my Internet is that bad) 

Thanks, that did the trick - seems the source list was screwed.

---

