---
title: "astah"
date: 2011-05-05
forum: General Help
---

### Post by diegompin on 2011-05-05
Good night, 

I'm trying to install astah througt .deb package from [http://members.change-vision.com/files/astah_community/6_4/astah-community_6.4_all.deb](http://members.change-vision.com/files/astah_community/6_4/astah-community_6.4_all.deb)

It's frozen in "Applying changes". I'm was waiting(and I'm still waiting).

Does anybody here know what's going on?

I`m using the 11.04 ubuntu 64 bits and I did the upgrade.

Anyway,

Thanks!!

:D

---

### Post by diegompin on 2011-05-05
Please, forgive my english, I`m brazilian :)

---

### Post by dulbirakan on 2011-09-19
Hey sorry for the late reply. 

Remove the lock ```

sudo rm /var/lib/dpkg/lock
```

Install through dpkg```

sudo dpkg -i astah-community....deb
```

You will need to type yes in the very end. Unless you do that installation is not completed.

I hope this will help someone.

---

