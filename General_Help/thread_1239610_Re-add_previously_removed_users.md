---
title: "Re-add previously removed users"
date: 2009-08-13
forum: General Help
---

### Post by mpsrig on 2009-08-13
How can I re-add previously removed users?

Any Ideas?

---

### Post by blueridgedog on 2009-08-13
Are you looking for some way that restores the user or help using System -> Administration -> Users and Groups?

I don't know of a way to restore a user account that was deleted other than simply recreating them.

---

### Post by mpsrig on 2009-08-13
> **blueridgedog said:**
> I don't know of a way to restore a user account that was deleted other than simply recreating them.

If it was that simple, I could do it.  However, when I try to re-create it, it says "this user already exists".

---

### Post by mpsrig on 2009-08-13
I found out how.  I had to remove the groups with the same name as the deleted user.

---

### Post by llamabr on 2009-08-13
This is the difference between the deluser command and the userdel command.  The former removes the user, and all files, whereas the latter just removes the uid.

Or did I get that backwards?

---

### Post by mpsrig on 2009-08-13
I used the gui so i couldnt tell u

---

### Post by blueridgedog on 2009-08-15
> **mpsrig said:**
> I found out how.  I had to remove the groups with the same name as the deleted user.

Thanks for noting this and posting it.  I use the command line and did not know that the GUI tool left the groups named for the removed users.

---

