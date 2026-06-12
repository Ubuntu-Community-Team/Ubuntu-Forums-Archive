---
title: "Traversing directory requires read permission unnecessarily in Ubuntu."
date: 2011-10-17
forum: General Help
---

### Post by supratik on 2011-10-17
I am having two users in my Ubuntu system, both belong to one group.
If I want to traverse the folder inside home of one user after logged in from another user I need to provide "chmod g +rx" to the home folder recursively. In Redhat/Fedora/CentOS only "chmod g+x" is enough to traverse the folders inside $HOME directory of other users.

Can you please tell why +r is required? Is there any way I can only specify g+x in the home folder recursively and traverse the folders inside the $HOME.

---

