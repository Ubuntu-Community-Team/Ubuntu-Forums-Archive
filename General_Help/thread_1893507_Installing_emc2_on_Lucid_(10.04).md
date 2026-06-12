---
title: "Installing emc2 on Lucid (10.04)"
date: 2011-12-10
forum: General Help
---

### Post by fester225 on 2011-12-10
I'm trying to install emc2 on a Lucid machine. I tried the LiveCD, but it keeps wanting to install another copy of 10.04 on top of what I already have.

I tried doing the installation from the repository, but the repository seems to be down.

There is no one on the IRC chat channel at the moment, and I have to wait for the administrator to OK my registration before I can post to the forum.

It seems like I should be able to install EMC2 from the LiveCD without the Lucid over-install, how would I do it?

---

### Post by lechien73 on 2011-12-10
Have you tried using the installation script from here: [http://linuxcnc.org/lucid/emc2-install.sh](http://linuxcnc.org/lucid/emc2-install.sh)

---

### Post by fester225 on 2011-12-10
Yes, I have tried using the installation script. At the end it tells me it can't find emc2 in the repository.

<<Package emc2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emc2 has no installation candidate>>


I've been referred to the installation page about 15 times, so far it hasn't helped.

---

### Post by lechien73 on 2011-12-10
Are you running 64-bit or 32-bit Ubuntu? From what I can see in the repository, there is no 64-bit package.

According to the instructions, you need to download and compile the 64-bit version from source.

---

### Post by fester225 on 2011-12-10
> **lechien73 said:**
> 

According to the instructions, you need to download and compile the 64-bit version from source.


Thank you. I'll bet this helps a lot. I hope this process doesn't prove to be as big a learning curve as I'm thinking it's going to be....

---

