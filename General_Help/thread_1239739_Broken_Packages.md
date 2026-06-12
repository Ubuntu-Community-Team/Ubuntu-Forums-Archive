---
title: "Broken Packages"
date: 2009-08-13
forum: General Help
---

### Post by xenogia on 2009-08-13
I got an error message recently, and I am wondering how to resolve this:

dean@dean-desktop:~$ sudo apt-get install libqt3-mt-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

---

### Post by hansdown on 2009-08-13
Hi xenogia.

I'm not familiar with using this, but some changes have been made.

You may need to add some other packages.

[http://packages.debian.org/sid/libqt3-mt-dev](http://packages.debian.org/sid/libqt3-mt-dev)

To fix broken packages, open synaptic, click custom packages> broken.

You can fix them there.

---

### Post by xenogia on 2009-08-13
> **hansdown said:**
> Hi xenogia.

I'm not familiar with using this, but some changes have been made.

You may need to add some other packages.

[http://packages.debian.org/sid/libqt3-mt-dev](http://packages.debian.org/sid/libqt3-mt-dev)

To fix broken packages, open synaptic, click custom packages> broken.

You can fix them there.

I didn't know that I was using it, but its there.   I was trying to upgrade my kernel and this popped up so I couldn't do it.  When I tried to uninstall qt3 a lot of packages wanted to be removed along with auducious plugins, compiz and other important things.

EDIT: I tried going into Synaptic, says there are no broken packages, but if I tried to add the package within Synaptic it still doesn't let me.  Truly odd indeed.

---

### Post by oldos2er on 2009-08-13
Check System, Administration, Software Sources, and make sure all repositories are enabled.

---

### Post by xenogia on 2009-08-13
> **oldos2er said:**
> Check System, Administration, Software Sources, and make sure all repositories are enabled.

No luck, everything was ticked. Truly weird and annoying.

---

### Post by hansdown on 2009-08-13
It may help to go to this link, and check the other packages that need to be added.

[http://packages.debian.org/sid/libqt3-mt-dev](http://packages.debian.org/sid/libqt3-mt-dev)

---

### Post by xenogia on 2009-08-13
> **hansdown said:**
> It may help to go to this link, and check the other packages that need to be added.

[http://packages.debian.org/sid/libqt3-mt-dev](http://packages.debian.org/sid/libqt3-mt-dev)

Well I went through it, but look at this.. Its saying that the dependency isn't there but it is.

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 7.4-0ubuntu3.1) but 7.4-0ubuntu3.2 is to be installed
E: Broken packages
dean@dean-desktop:~$ sudo apt-get install libglu1-mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglu1-mesa is already the newest version

EDIT: Truly annoying, that it wants an older version rather than the one I have on.  And I don't know how to resolve without remove a lot of essential packages.

---

### Post by xenogia on 2009-08-13
I should probably say that I am trying to upgrade my kernel, through this option

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

But damn qt3 dependencies

---

### Post by hansdown on 2009-08-13
That is strange.

I know I've been less than helpful, thus far.

I found a thread that is oddly exact.

**It's old, so please don't follow the instructions. It's also KDE.**

[http://ubuntuforums.org/showthread.php?t=227117](http://ubuntuforums.org/showthread.php?t=227117)

---

### Post by xenogia on 2009-08-13
> **hansdown said:**
> That is strange.

I know I've been less than helpful, thus far.

I found a thread that is oddly exact.

**It's old, so please don't follow the instructions. It's also KDE.**

[http://ubuntuforums.org/showthread.php?t=227117](http://ubuntuforums.org/showthread.php?t=227117)

I should also note that I am trying to use KernelCheck to upgrade the kernel manually, and it requires installing qt3 which is annoying.  I wish there was an easier way.

---

### Post by hansdown on 2009-08-13
Does```
 sudo apt-get update && sudo apt-get upgrade
``` help?

---

### Post by xenogia on 2009-08-13
> **hansdown said:**
> Does```
 sudo apt-get update && sudo apt-get upgrade
``` help?

Haha, no. I check updates everyday.. nice try though.

---

### Post by xenogia on 2009-08-13
Resolved the issue, just manually downgraded the package. Seems I using an unstable package from a while ago when I was testing the new X version.  Anyhow, its working now.. Thanks for your help anyway.

---

### Post by hansdown on 2009-08-13
Glad you fixed it xenogia.

---

