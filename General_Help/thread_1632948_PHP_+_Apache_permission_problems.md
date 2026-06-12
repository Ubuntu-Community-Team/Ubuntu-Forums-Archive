---
title: "PHP + Apache permission problems"
date: 2010-11-28
forum: General Help
---

### Post by CloudedVision on 2010-11-28
I set up the LAMP stack on my Ubuntu desktop, which I use for development.  I changed the Apache site root to /home/user/Sites, and changed the permissions to 777 so Apache could access it.  (Not the most secure thing, but it doesn't really need to be secure.)  However, my despite this, PHP still complains that it doesn't have write permissions.  How can I fix this?

---

### Post by CloudedVision on 2010-11-28
This was a new directory within Sites/, and it seems it didn't inherit the permissions of Sites/.  I set it as 777 and it works.  I feel silly now.

---

