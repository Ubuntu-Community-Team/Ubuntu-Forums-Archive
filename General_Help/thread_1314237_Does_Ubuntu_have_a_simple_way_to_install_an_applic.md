---
title: "Does Ubuntu have a simple way to install an application just for your own user?"
date: 2009-11-04
forum: General Help
---

### Post by hoppipolla on 2009-11-04
I mean, I know there are WAYS to do this... but are any worked into the package handling system? This might be a good addition for future, as as far as I can tell the only way (for your average user) is to install it as admin (root).

What do you think? In Windows you can select only for the current user, and if we allowed this through GUI tools more in Ubuntu we would stop people having to put in their password for every installation...

is this in the works? or?

Hoppi :)

---

### Post by Pasdar on 2009-11-04
how about change owner of folder its installed in and chmod only flags for that owner.

---

### Post by Tibuda on 2009-11-04
I don't think there are plans for this, and I see no reason for.

How it would improve for the avg user instead of what usc/gdebi/synaptic/apt-get does now?

---

### Post by Xbehave on 2009-11-04
if you don't have noex set on your /home partition, then anything in ~/bin will be available to user (assuming it's in your $PATH (it's not on fedora ,it may be on ubuntu, if it's not then add it in /etc/profile)

alternatively, the system administrator can install it globally then use chgrp & chmod to allow only members of certain groups (such as a users individul group) to execute it (if security matters then take care to find the actual binary and chgrp & chmod it too)

---

### Post by hoppipolla on 2009-11-04
> **Xbehave said:**
> if you don't have noex set on your /home partition, then anything in ~/bin will be available to user (assuming it's in your $PATH (it's not on fedora ,it may be on ubuntu, if it's not then add it in /etc/profile)

alternatively, the system administrator can install it globally then use chgrp & chmod to allow only members of certain groups (such as a users individul group) to execute it (if security matters then take care to find the actual binary and chgrp & chmod it too)

Yeah but I meant a friendly way, you know? Just like a tick box during program installation :)

If you install it as root you would need to sudo/gksu, but if not you don't :)

---

### Post by ssam on 2009-11-04
with a bit of magic with fuse and chroot it must be possible to install a deb into a users home.

it probably can't work for system/server stuff, but to let non admin users install applications it would be handy.

its no different securitywise to people compiling things with --prifix=~

---

### Post by 3rdalbum on 2009-11-04
How do dependencies get resolved if things are running non-root? Would they be resolved for just that user?

---

### Post by hoppipolla on 2009-11-04
> **3rdalbum said:**
> How do dependencies get resolved if things are running non-root? Would they be resolved for just that user?

well it can still READ the required libraries etc, it just couldn't edit them, but it wouldn't do that anyway :)

---

### Post by soapBAR2 on 2009-11-04
I'm not entirely sure why it would be commonly useful to deny certain users access to programs, but there are a number of ways (permission flags using group owner, mountable partition, etc). The problem is that firstly, it's not useful to many people, and secondly, such a feature SHOULDN'T be easy to trigger, as it would likely resolve in either redundant copies of the same file, or even dependency hell (where one user installs one package and the next installs a different version of the same package, which confuses anything depending on it).

---

