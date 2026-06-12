---
title: "Synaptic Package Manager Question"
date: 2006-01-24
forum: General Help
---

### Post by OPaul on 2006-01-24
Why does the Synaptic Package Manager not include the latest version of popular software titles like Thunderbird and Firefox?

---

### Post by aysiu on 2006-01-24
Because those need to be packaged.

Ubuntu gets updated every six months. Within those six months, you'll get only security updates.

The version that comes out in April (Dapper v. 6.04) will have Firefox 1.5.

---

### Post by OPaul on 2006-01-24
Is that a completly new install or can I update my current Ubuntu to that, when it comes out?

---

### Post by RAOF on 2006-01-24
[QUOTE=OPaul]Is that a completly new install or can I update my current Ubuntu to that, when it comes out?[/QUOTE]
You will be able to update (your current Ubuntu) to the new version.

---

### Post by OPaul on 2006-01-24
So if I go ahead and update my Firefox now and then later update Ubuntu will I run into trouble with Firefox? Will I have 2 versions installed?

---

### Post by RAOF on 2006-01-24
[QUOTE=OPaul]So if I go ahead and update my Firefox now and then later update Ubuntu will I run into trouble with Firefox? Will I have 2 versions installed?[/QUOTE]
That depends on how you update your Firefox (but even if you have 2 versions installed, it shouldn't cause trouble).  If you just download it from mozilla.org, the package manager (Synaptic) won't know about it, and so won't update it (but it will still update the Firefox that it knows about).  There's information about how to do it on the [FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion") wiki page.

---

### Post by tim15856 on 2006-01-25
Automatix will install Firefox 1.5. It's the EZ way to do it. [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by OPaul on 2006-01-25
I'm trying to install jre now and I'm choosing Java Web Start 1.4 from the list,  but when I go to install it I get the following message.

----
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
---

After that it seems to install fine. But I've seen messages like this before when I install things. What does it mean?

---

### Post by akiro.yamamoto on 2006-01-25
Try reloading/refreshing the package/repository list.

---

### Post by OPaul on 2006-01-25
[QUOTE=akiro.yamamoto]Try reloading/refreshing the package/repository list.[/QUOTE]
How do I do that?

---

### Post by OPaul on 2006-01-25
When I click the "Reload" button in Synaptic Package Manager I get the following.

----
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz:) 404 Not Found
----

and then it says

----
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
----

---

### Post by aysiu on 2006-01-25
Mirrormax is dead.
See the first link of my signature.

---

### Post by OPaul on 2006-01-25
Ah, cool, thanks.

---

