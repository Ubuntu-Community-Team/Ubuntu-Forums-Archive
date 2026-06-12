---
title: "Changing user passwords via console"
date: 2010-09-07
forum: General Help
---

### Post by OpressedCalamity on 2010-09-07
What is the command to change other users passwords, as root?
Thanks.

---

### Post by Sabir_101 on 2010-09-07
sudo passwd user

---

### Post by surfer on 2010-09-07
```

$ sudo passwd $username

```
first, you will have to enter your sudo password, then the new user password (twice).

---

### Post by OpressedCalamity on 2010-09-07
> **Sabir_101 said:**
> sudo passwd user

Thanks!

---

### Post by OpressedCalamity on 2010-09-07
> **surfer said:**
> ```

$ sudo passwd $username

```
first, you will have to enter your sudo password, then the new user password (twice).

You to.

---

