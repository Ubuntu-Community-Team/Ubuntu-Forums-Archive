---
title: "Default group permission"
date: 2009-10-30
forum: General Help
---

### Post by eks on 2009-10-30
Quick question,

I understand how permissions work but... how do I set the default group permission to "Create and delete files" instead of the usual "Access files"? I share this home desktop with my wife, it would be easier if the group permission would be set this way. I have my user added to her group and hers added to mine.

Thanks!

PS: I know that if someone hacks into her account will be able to mess with my files, and vice-versa, but really, it's just a home desktop and this computer is NATted at the ISP level.

---

### Post by alphaniner on 2009-10-30
This is controlled by the umask.  It is defined on the last line of /etc/profile.  The default is 022.  Change it to 002.  Users will have to log out for the change to take effect.

Then anyone belonging to the owning group will be able to write to *newly created* files and directories.  It won't change those that already exist.

I've never messed around with groups.  Are you sure both your and your wife's account log into the same group by default?  Because if you don't, I think this won't do any good.

---

### Post by eks on 2009-10-30
Thanks a lot for the quick replay!!! :D


> **alphaniner said:**
> Are you sure both your and your wife's account log into the same group by default?

No no, her account logs into a group with her name, but I added my user to her group. The same for my group (has her user inside it).

It works quite well. :)  (but you have to reboot or re-login after adding the users to the groups, something simple but made me waste some quite few minutes.)

Thanks again!

---

