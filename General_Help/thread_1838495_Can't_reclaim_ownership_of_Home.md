---
title: "Can't reclaim ownership of Home"
date: 2011-09-03
forum: General Help
---

### Post by Xtensity on 2011-09-03
I had to remount my home folder on a different partition because the partition I initially installed to only had 5gig and quickly became full.

After remounting the folder successfully I lost all ownership of everything in the home folder. Many commands didn't work at all.

I finally got $sudo chown -hvR $USERNAME /home/* to work. 

It said all ownerships of everything in Home were set to my username. So success is what I'm thinking. Though when I right click any file in the home folder it says they are all stilled owned my root. Even changing the ownerships while in root does nothing. Why is it telling me things like "changed ownership of `/home/xtensity' to xtensity" for every file in home, but actually not changing any ownerships.

---

### Post by cgroza on 2011-09-03
Please post the output of this command:
```

ls -lh /home/xtensity 

```

---

