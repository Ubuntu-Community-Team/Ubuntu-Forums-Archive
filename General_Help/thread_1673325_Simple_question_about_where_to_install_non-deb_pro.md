---
title: "Simple question about where to install non-deb programs"
date: 2011-01-22
forum: General Help
---

### Post by Rackstar on 2011-01-22
Hey,

I've been wondering about this for so long. For example, I want to install Netbeans from netbeans.org (I need different versions than in the repositories).

This comes with an installer and asks me where to install netbeans. It proposes installing it into "~/netbeans-6.9.1". The home-folder does not seem to be the place to install programs, am I correct?

I used to make a folder in /opt/ and changing the owner of that folder to match my currect user (not root). But this seems like a bit too far fetched.

Is there a folder dedicated for installing user software like this?

Thanks!

---

### Post by Smart Viking on 2011-01-22
It doesn't really matter where you install programs, it runs the same.

---

### Post by Rackstar on 2011-01-22
> 1.13. /opt
This directory is reserved for all the software and add-on packages that are not part of the default installation.
From [http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html](http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html)

I'll keep on making dirs in /opt/ I guess. (Otherwise it will always be in my backups)

To bad installers always ask to install inside the home-folder, as this is cluttery

---

