---
title: "Custom groups do not work"
date: 2009-11-02
forum: General Help
---

### Post by |Porsche on 2009-11-02
Hey, I am not sure if this is a bug, or I am missing something. I have added a group called media and assigned users to it. The group shows in /etc/group with the proper users assigned to it. However when I do an id I do not see the group for that user, neither can the user access files that are own by that group.

Any clues?

---

### Post by sisco311 on 2009-11-02
After adding the user to the group you have to log out the user and log it back in.

---

### Post by |Porsche on 2009-11-02
Sure enough! Thanks!

---

