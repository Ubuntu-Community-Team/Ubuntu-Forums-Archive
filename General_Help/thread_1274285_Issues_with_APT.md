---
title: "Issues with APT"
date: 2009-09-24
forum: General Help
---

### Post by chemicalfan on 2009-09-24
I've got a problem with APT/Synaptic, as it always reports errors whenever I try to do install anything. It was working fine, but has broken at some point, and now will report errors when anything is installed. It doesn't matter what the package is, it will error anyway. The error appeared to be with gnome-terminal, but trying to install gnome-terminal again doesn't work, as it tells me I've got the latest version already! From what I can gather, it isn't a fatal error - the packages do get installed, but I'm a bit worried about what the system *isn't* doing as part of the install process. Below is a dump of the terminal screen when trying to autoremove from APT (doesn't matter whether I'm installing or removing):

```
mike@mike-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-terminal-data (2.26.0-0ubuntu2.1) ...
Segmentation fault
dpkg: error processing gnome-terminal-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on gnome-terminal-data (>= 2.26); however:
  Package gnome-terminal-data is not configured yet.
 gnome-terminal depends on gnome-terminal-data (<< 2.27); however:
  Package gnome-terminal-data is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for menu ...
Errors were encountered while processing:
 gnome-terminal-data
 gnome-terminal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm fairly noob at Linux to be honest, so please accept my apologies if I've missed something obvious! It was working, and now it's not! I did think about removing the gnome-terminal package, and then reinstalling it through Synaptic, but last time I tried to remove something (old version of Python), I wrecked my entire install!

---

### Post by raptor386 on 2009-09-25
Try
```

sudo apt-get install --reinstall scrollkeeper

```

It'll probably take a long time (especially if you've got a SSD like I do) but let it run. When it finishes, it should hopefully solve your problem.

I think what happened is scrollkeeper had an update, but it fudged up it's database, so it starts segfaulting. gnome-terminal's configure scripts need it for whatever reason, so it never gets configured properly.

If that doesn't fix your problem, then you'll need to track down what's segfaulting:

```

$ sudo su
# ulimit -c unlimited
# cd /
# apt-get install --reinstall gnome-terminal-data
# file core

```

The last line should return information about the core file generated from the failed configure, including what executable caused it. From there you should be able to reinstall whatever package that executable is a part of (in my case, it was scrollkeeper-update that was crashing, so I reinstalled scrollkeeper).

Hope that helps!

---

### Post by KiLaHuRtZ on 2009-09-25
Try this...

```
sudo apt-get purge gnome-terminal gnome-terminal-data
sudo apt-get update
sudo apt-get install gnome-terminal gnome-terminal-data
```

If it still errors, try this...

```
sudo dpkg --configure gnome-terminal
```

And/or...

```
sudo dpkg --configure gnome-terminal-data
```

---

### Post by chemicalfan on 2009-09-27
Thanks for the replies guys (apologies for the delay in posting back!) - will give them a try in a bit, and post back with the results

---

### Post by chemicalfan on 2009-09-27
Well, that seems to have done the job Raptor - thanks very much!! I'd never heard of scrollkeeper up till now, will have to give it a read up as it's clearly pretty important!

---

### Post by mcopeland@pobox.com on 2009-09-27
I am having the same problem in Jaunty/KDE. I tried to substitute KDE for Gnome but that didn't work. Can you pls post the fix using KDE?
Thx
Mike

---

### Post by raptor386 on 2009-09-27
> **mcopeland@pobox.com said:**
> I am having the same problem in Jaunty/KDE. I tried to substitute KDE for Gnome but that didn't work. Can you pls post the fix using KDE?
Thx
Mike

This was a pretty specific problem that occurs with the ubuntu netbook remix, so I suspect you are having a different problem entirely. I had the same problem as the OP, so that's how I knew how to fix it.

If the following didn't work for you, then it's a different probem:
```

sudo apt-get install --reinstall scrollkeeper

```

Can you post the exact command you are running as well as it's output?

---

### Post by mcopeland@pobox.com on 2009-09-27
using the above command 
(got to type this all in)
first trouble is when setting up openafs-modules-dkms(1.4.9.dfsg1-0+ubuntu3).../var/lig/dpkg/info/openafs-modules-dkms.spotinst:10:dkms not found
dpkg: error processing openafs-modules-dkms (--configure)
subprocess post-installation script returned error exit status 127

errors encountered while processing 
openafs-modules-dkms 
E: sub-process /usr/bin/dpkg/ returned error code (1)

---

### Post by raptor386 on 2009-09-27
Try
```

sudo apt-get install --reinstall dkms

```

---

### Post by mcopeland@pobox.com on 2009-09-27
that seems to have worked, thanx!  Can you tell me what broke and maybe why?

---

### Post by raptor386 on 2009-09-28
```
/var/lig/dpkg/info/openafs-modules-dkms.spotinst:10:dkms not found
```

Suggested that 'dkms' was not installed properly. Why or how this happened, I have no idea.

---

### Post by fluffman86 on 2009-09-28
> **raptor386 said:**
> ```
/var/lig/dpkg/info/openafs-modules-dkms.spotinst:10:dkms not found
```

Suggested that 'dkms' was not installed properly. Why or how this happened, I have no idea.

In my experience, things like that happen when you cancel an upgrade, either manually for some reason, or accidentally, or maybe you lose power or your computer shuts off without finishing the upgrade.

---

