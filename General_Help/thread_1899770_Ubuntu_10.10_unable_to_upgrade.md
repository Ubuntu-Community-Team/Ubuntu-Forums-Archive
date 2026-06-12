---
title: "Ubuntu 10.10 unable to upgrade"
date: 2011-12-24
forum: General Help
---

### Post by KK329 on 2011-12-24
I realized that I was not able to upgrade my ubuntu via the update manager recently. Whenever I tried to use the manager it popped up something to stop me from doing it. I've attached a print-screen file with the thread. Can I get your help?

P.S. Merry Christmas!

---

### Post by plucky on 2011-12-24
> **KK329 said:**
> I realized that I was not able to upgrade my ubuntu via the update manager recently. Whenever I tried to use the manager it popped up something to stop me from doing it. I've attached a print-screen file with the thread. Can I get your help?

P.S. Merry Christmas!

From a terminal ```
sudo rm /var/lib/apt/lists/* -vf
``` to delete the list files and then run ```
sudo apt-get update
``` to reload them.

Good Luck

---

### Post by KK329 on 2011-12-25
Thanks very much for the help.

I successfully  had the update once. But then I realize that when I clicked the update button, the system stopped me and "Failed to download repository information", with the following > W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B6C6326781C0BE11, W:Failed to fetch [http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

What can I do for the further update? Many thanks!

---

### Post by pretty_whistle on 2011-12-25
You probably could upgrade without a problem if you got the iso online and bypass using the update manager.

---

### Post by Lars Noodén on 2011-12-25
It looks like you are missing the [PGP key](http://wiki.debian.org/SecureApt) for one of the PPAs.  You can try adding it like this:

```

gpg --keyserver pgp.mit.edu --recv-key B6C6326781C0BE11
gpg --export B6C6326781C0BE11 | sudo apt-key add -

```

---

### Post by Frogs Hair on 2011-12-25
Make sure the PPA is compatible with 11,04 also and disable it if it is not .

---

### Post by KK329 on 2011-12-25
> **Lars Noodén said:**
> It looks like you are missing the [PGP key](http://wiki.debian.org/SecureApt) for one of the PPAs.  You can try adding it like this:

```

gpg --keyserver pgp.mit.edu --recv-key B6C6326781C0BE11
gpg --export B6C6326781C0BE11 | sudo apt-key add -

```

I tried but it turned that 

> 
gpg: keyserver timed out
gpg: keysever receive failed: keyserver error


what should I do now?

---

### Post by plucky on 2011-12-25
> **KK329 said:**
> I tried but it turned that 



what should I do now?

[http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/binary-i386/Packages.gz)

That doesn't seem to be a valid PPA.Try disabling it in Software Sources and then see if you get the same error.

Good Luck

---

### Post by KK329 on 2011-12-25
> **plucky said:**
> [http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/killian/f.lux/ubuntu/dists/maverick/main/binary-i386/Packages.gz)

That doesn't seem to be a valid PPA.Try disabling it in Software Sources and then see if you get the same error.

Good Luck

Thanks, but how to do it?

---

### Post by plucky on 2011-12-25
> **KK329 said:**
> Thanks, but how to do it?

**System > Administration > Software Sources** and un-tick the box that points to that PPA under the **Other Software** Tab.

Good Luck

---

### Post by West201 on 2011-12-25
I usually prefer to follow  the Linux mint's method, just do a clean install.

Cons:

Slow: APT will download the new version of all the packages installed on your system. Assuming you installed nothing at all, that's about 3GB of data.... using a fresh upgrade you could have downloaded all that data by simply getting the 700MB ISO.
Unreliable: Depending on your modifications, your sources, your added software and your configuration you could end up with a system that acts and feels really different than a brand new version of the newer Linux Mint release. You're far from the beaten track and the added features might not work as well on your system as they were designed to.
Risky: The temptation when you upgrade with APT is not to perform backups... since your partitions aren't overwritten, nothing "forces" you to make backups... think about the risk though.
Complicated: Packages conflict with each others, they can bring complex dependencies and put you in situations that are difficult to solve.

Pros:

Automated: APT does everything for you (well, until something goes wrong of course)
Real upgrade: A "fresh" upgrade is kind of like the new Linux Mint with your data on it... this in comparison feels more like "your system" running the newer version underneath.


Linux Mint is based on Ubuntu. 
[http://community.linuxmint.com/tutorial/view/2](http://community.linuxmint.com/tutorial/view/2)

---

### Post by KK329 on 2011-12-26
Problem Solved, Thanks very much.

Merry Christmas to everyone here!

---

### Post by West201 on 2011-12-26
> **KK329 said:**
> Problem Solved, Thanks very much.

Merry Christmas to everyone here!

What did you do to fix ?

---

### Post by KK329 on 2011-12-27
> **jessejj89 said:**
> What did you do to fix ?

Yes basically I just tried to remove those packages from Software sources, and then I upgrade my system to 11.10 using the APT. The problem solved that I can update the system without difficulty now.

---

