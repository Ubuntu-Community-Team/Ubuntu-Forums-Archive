---
title: "Making a user an admin"
date: 2009-10-06
forum: General Help
---

### Post by OKKARE on 2009-10-06
I have tried

sudo usermod -g admin mark

but mark still isn't admin, has a different terminal when he signs in with SSH, and can't access some folders.

I am passing on the server to him, so he needs full control. What do I do?

Thanks.

---

### Post by zvacet on 2009-10-06
```
 sudo adduser mark admin
```

---

### Post by louieb on 2009-10-06
Just because a user is a member of the admin group it does not mean he has access to all folders. But he can use  sudo. And through using sudo he can go wherever he wants. 

look in /etc/group to see if he is a member of the admin group.

---

