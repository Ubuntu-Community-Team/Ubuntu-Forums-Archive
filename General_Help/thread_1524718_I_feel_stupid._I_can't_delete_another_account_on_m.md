---
title: "I feel stupid. I can't delete another account on my latop."
date: 2010-07-05
forum: General Help
---

### Post by wauki on 2010-07-05
I have an account my friend made. I do not want, or need it on my laptop anymore. How can i delete it?

---

### Post by cj.surrusco on 2010-07-05
Go to **System>Administration>Users and Groups**.

Just choose the account and click delete.

---

### Post by mike555 on 2010-07-05
assuming it's in Ubuntu , go to System,Administration ,  users & groups , highlight the user and delete........

---

### Post by wauki on 2010-07-05
That didn't work. and i used the administrator account

---

### Post by cj.surrusco on 2010-07-05
> **wauki said:**
> That didn't work. and i used the administrator account

What do you mean it didn't work?

---

### Post by CannibalZerg on 2010-07-06
Open Terminal and run:
```

sudo deluser --remove-home friendusername

```
Where *friendusername* is account name which you want to delete.
And if there's any error messages, post them here.

---

### Post by wauki on 2010-07-06
> **CannibalZerg said:**
> Open Terminal and run:
```

sudo deluser --remove-home friendusername

```Where *friendusername* is account name which you want to delete.
And if there's any error messages, post them here.

It worked. Thank you.

---

