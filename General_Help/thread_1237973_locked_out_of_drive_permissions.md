---
title: "locked out of drive permissions"
date: 2009-08-12
forum: General Help
---

### Post by wirewrangler on 2009-08-12
Running 9.04. I have a partition from which I boot, and another for media. The media partition was consolidated with another I no longer need using Gparted. When I open media partition's permission dialog, i get that the owner is root and I cannot make changes. I am the only user on the machine, is there a way I ca open permissions with sudo?

---

### Post by wirewrangler on 2009-08-25
aha! on an unrelated post and topic on another website, I found 'sudo chown -R user:group target file or directory'

---

### Post by P4man on 2009-08-25
indeed. if you make or change a partition with gparted, you run gparted as root, and therefore root will own the partition. You just found the solution to take ownership from root again :)

---

