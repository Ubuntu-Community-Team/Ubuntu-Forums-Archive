---
title: "Distro/DE neutral method of changing someone's UserID"
date: 2010-09-08
forum: General Help
---

### Post by beastrace91 on 2010-09-08
Howdy There,

Is there a DE/distro neutral (I guess CLI) method of changing a given user's user ID on a Linux system? I want to set all my systems to have the same UserID so my external hard drive stops giving permission errors when moving between them.

Regards,
~Jeff

---

### Post by ubulal on 2010-09-08
> **beastrace91 said:**
> 
Is there a DE/distro neutral (I guess CLI) method of changing a given user's user ID on a Linux system?

Change the id in /etc/passwd and /etc/group and do
chown -R user:group /home/user
replacing "user:group" by actual user and group name.

---

