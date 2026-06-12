---
title: "Default /home and /username permissions"
date: 2009-06-27
forum: General Help
---

### Post by Flyingroof on 2009-06-27
I recently moved my home folder to its own partition. Everything worked fine but the permissions on the folders are all fudged up. Can someone give me what the default permissions should be for all of the folders?

---

### Post by dcstar on 2009-06-27
> **Flyingroof said:**
> I recently moved my home folder to its own partition. Everything worked fine but the permissions on the folders are all fudged up. Can someone give me what the default permissions should be for all of the folders?

The permissions will be the same as the source you copied them from.

Linix system folders (like /home) will only work correctly on Linux partitions, what is the partition type you are using?

---

### Post by Flyingroof on 2009-06-28
I'm using an ext3 partition. I did all of my mounting etc as super user so my folder ownership was fudged up. To load all my desktop data I did "su chmod 777 -R /home" as a quick fix but now I want to set everything back to normal.

---

