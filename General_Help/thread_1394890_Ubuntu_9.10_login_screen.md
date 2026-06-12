---
title: "Ubuntu 9.10 login screen"
date: 2010-01-31
forum: General Help
---

### Post by frogbrains on 2010-01-31
Just when on the accessibility options on the login screen, to see what they were, and I ticked "Enhance contrast in colours".  After seeing what it was like, I unticked it, expecting the login screen to go back to normal, but it didn't.  Instead of the cool grey colours it was before, it's now the same colour as the top panels, and the icons have changed.  How can I restore it to it's former theme?

---

### Post by NightwishFan on 2010-01-31
I had this same problem as well, I have learned not to touch it, as I did not find a solution. I will keep my eyes open. There is a bug report, and a workaround.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/402017](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/402017)

Does the theme stay the same after a reboot?

---

### Post by jdtfk on 2010-02-03
On the same page that **NightwishFan** posted, there is a workaround:

```
This worked for me:
1 - copy file /var/lib/gdm/.gconf.defaults/%gconf-tree.xml to another place (just a backup)
2 - boot from a LiveCD or USB
3 - copy file /var/lib/gdm/.gconf.defaults/%gconf-tree.xml over the original
```

Did it myself succesfully.
Just in case, you need to copy the file from the USB or Live CD, to your installation as **root**.

---

