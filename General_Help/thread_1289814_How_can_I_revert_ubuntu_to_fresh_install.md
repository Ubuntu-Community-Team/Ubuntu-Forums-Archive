---
title: "How can I revert ubuntu to fresh install"
date: 2009-10-12
forum: General Help
---

### Post by camrant on 2009-10-12
I am looking for a way to remove basically every package installed on a system and bring to a basic fresh install with virtually nothing but the basics.  I know the right way to do this would be to just wipe and reinstall.  The challenge that I am looking at here is that I am remote to this computer and do not have physical access? Is there an easy way? Can I see everything that has been installed or modified since OS's install and then manually remove each one?

---

### Post by Giblet5 on 2009-10-12
I know of no way to do this **now**, but what I do on a clean install is: ```
sudo dpkg -l | awk '{ print $2 }' | grep -ve '^$' | grep -v Status= | grep -ve '^Name$' | grep -ve '^Err?' > pkgs-vanilla.txt
```

Even that doesn't get around the fact that you'll have patches installed that you likely don't want to back out...

Save your /home filesystem to a USB stick and reinstall.

---

### Post by camrant on 2009-10-12
definitely helped find packages that I wanted to remove. Thankt

---

