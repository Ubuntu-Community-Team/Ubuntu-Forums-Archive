---
title: "Can't uninstall or install anything (dpkg error)."
date: 2011-06-26
forum: General Help
---

### Post by lucaryholt on 2011-06-26
I was having some problems with PlayOnLinux and decided to uninstall it.

I went to Software Center and tried to uninstall it there, no luck.
It just said: Package operation failed. The installation or removal of a software package failed.

So then I tried in Terminal: entering "sudo apt-get remove playonlinux" and I got this reply: > E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

I then tried to enter: "sudo dpkg --configure -a" and got this: > dpkg: error: parsing file '/var/lib/dpkg/updates/0005' near line 0:
 newline in field name `e)'

Ubuntu 11.04 (64x) installed from WUBI.

Hardware (I don't know if this is relevant):
Intel i5 M 450
ATI Mobility HD 5650
Others?

**Thank you in advance!**

---

### Post by nzjethro on 2011-06-26
Hi lucaryholt. From what I can see, this file was left behind in the interrupted installation, and needs to be removed. /var/lib/dpkg/updates/ is an empty folder over here, so I imagine that this is (part of) a temporary file that needs to be removed.

Run
```
sudo mv /var/lib/dpkg/updates/0005 ~/dpgk_update_0005
```

This way you can move it back if this goes horribly wrong. Then run:

```
sudo dpkg --configure -a
```

And if that works, run
```
sudo apt-get update
```

Then try to install PlayOnLinux again.

If this all goes to toast, run
```
sudo mv ~/dpgk_update_0005 /var/lib/dpkg/updates/0005 
```
to put the file back where it came from (hopefully you won't need to do this). :D

---

### Post by lucaryholt on 2011-06-27
> **nzjethro said:**
> Hi lucaryholt. From what I can see, this file was left behind in the interrupted installation, and needs to be removed. /var/lib/dpkg/updates/ is an empty folder over here, so I imagine that this is (part of) a temporary file that needs to be removed.

Run
```
sudo mv /var/lib/dpkg/updates/0005 ~/dpgk_update_0005
```

This way you can move it back if this goes horribly wrong. Then run:

```
sudo dpkg --configure -a
```

And if that works, run
```
sudo apt-get update
```

Then try to install PlayOnLinux again.

If this all goes to toast, run
```
sudo mv ~/dpgk_update_0005 /var/lib/dpkg/updates/0005 
```
to put the file back where it came from (hopefully you won't need to do this). :D

Thank you so much! This helped enormously!

---

