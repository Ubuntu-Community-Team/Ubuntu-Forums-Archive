---
title: "Sound Help"
date: 2006-06-21
forum: General Help
---

### Post by jw29 on 2006-06-21
Hello,

I run two student labs for the math/computer science network at a university.  We have 7 computers in one lab running just Ubuntu 5.10 and then 25 computers in the other lab dualbooting Ubuntu 5.10 and Windows 2000.  Our main server, which  is where all user logins go through, is running Gentoo.

The problem is we need to set up Ubuntu to allow the users to run sound.  The only way we know of to do it is to manually add people to /etc/groups, but as we're adding accounts to the network quite frequently, it's unrealistic to manually add them to about 35 different machines, and even if we could manage all 35, listing hundreds of users in /etc/groups itself is a tad unrealistic, also.

I've looked around a bit and I've seen that possibly pam-exec could be used, but we can't find any working download mirrors to get it at.  And from there, we can't find any documentation for it...the only information I've been able to find on it is a one sentence description "Changes device permissions on login/logout." or something to that effect.

Any ideas?

Thanks,
Jason

---

### Post by glotz on 2006-06-21
I wonder if you could use symlinks in the /etc/groups folder pointing to the gentoo box?

disclaimer: glotz is a clueless linux newbie.

---

