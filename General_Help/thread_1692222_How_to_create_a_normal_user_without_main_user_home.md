---
title: "How to create a normal user without main user home folder access"
date: 2011-02-21
forum: General Help
---

### Post by vimal0212 on 2011-02-21
Dear Friends,

I want to create a normal user account in Ubuntu in addition to main user
(user created at the time of installation).

In normal case, the new user can access main user Home folder.
I want to restrict the access for new user.

How can I create a new user without access to main user Home folder?

Regards,

---

### Post by mastablasta on 2011-02-21
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
 
might be a bit different interface now, but it's easy enough to navigate through settings...

---

### Post by tredegar on 2011-02-21
To make your home directory unreadable by others:
```
chmod 700 /home/username
```

---

