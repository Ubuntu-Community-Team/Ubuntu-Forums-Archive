---
title: "Get current use name in terminal?"
date: 2012-07-25
forum: General Help
---

### Post by ltwinner on 2012-07-25
Is there a terminal command that will show the current user name?

---

### Post by Statia on 2012-07-25
> **ltwinner said:**
> Is there a terminal command that will show the current user name?

The aptly named command:

whoami

---

### Post by hakermania on 2012-07-25
Another way:
```

echo $(logname)

```
It will output the name of the user who is logged in. Even if you are root, for example, but you have signed in as 'alex', then it will output 'alex', instead of 'whoami' which will output 'root'.

---

### Post by Vaphell on 2012-07-25
it is also stored in an environment variable
```
echo $USER
echo $HOME
```

---

### Post by sisco311 on 2012-07-25
whoami is not standard. I'd use **id -un**.

---

