---
title: "How do I access a samba share without mounting?"
date: 2011-05-31
forum: General Help
---

### Post by CrazeDIzzleD on 2011-05-31
So if you haven't seen my other thread, go here. [http://ubuntuforums.org/showthread.php?t=1771576](http://ubuntuforums.org/showthread.php?t=1771576)

I realized the problem was likely because I am working from a mount rather than the network source. So, how can I access the network source directly with Eclipse, or any other IDE?

With nautilus I can access the share like this: smb://scott-desktop/www/, but my IDE programs tell me that is not a valid location. Why not?

---

### Post by Morbius1 on 2011-05-31
Eclipse is probably looking for a mount point. You have one, it's located here:
> /home/your-user-name/.gvfs/www on scott-desktopYou will have to enable "show hidden files" both in nautilus and in at least one other application to see it because of the ".gvfs" location.

---

