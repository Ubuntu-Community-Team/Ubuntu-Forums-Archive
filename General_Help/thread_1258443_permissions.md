---
title: "permissions?"
date: 2009-09-05
forum: General Help
---

### Post by Kristofer Van Orton on 2009-09-05
Okay I read in a forum post here to download Storage Device Manager and it gave me the command to do so. The forum post was about mounting drives when you boot up the system. And it worked! my drives mount when i start up
but now for some reason i dont have permissions to either delete or install anything into either drives...
any ideas?

---

### Post by shwallace on 2009-09-05
> **Kristofer Van Orton said:**
> Okay I read in a forum post here to download Storage Device Manager and it gave me the command to do so. The forum post was about mounting drives when you boot up the system. And it worked! my drives mount when i start up
but now for some reason i dont have permissions to either delete or install anything into either drives...
any ideas?
Do you have the storage device manager installed?

---

### Post by shwallace on 2009-09-05
> **shwallace said:**
> Do you have the storage device manager installed?
Sorry, quit too soon! Open your SDM and select the partition you want to automount. Use the Assistant buton and check every item on the list. Where is say's group, enter your group name. UID=1000, UMASK=077. GID=1000. This set everything just fine for me.

---

