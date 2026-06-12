---
title: "Warning: Remote host identification has changed!"
date: 2009-07-10
forum: General Help
---

### Post by mrakesh85 on 2009-07-10
recently I have reinstalled ubuntu in my system. From that day I am getting above warning message, when I want to access my system from other systems using ssh

---

### Post by alien8tive on 2009-07-11
I think you are referring to the spoofing error. To resolve this:

```
cd .ssh
```

if you ls, you will see the known hosts file. Clear the text in it to resolve your probelm.

```
echo "" > known_hosts
```

---

### Post by mrakesh85 on 2009-07-11
> **alien8tive said:**
> I think you are referring to the spoofing error. To resolve this:

```
cd .ssh
```if you ls, you will see the known hosts file. Clear the text in it to resolve your probelm.

```
echo "" > known_hosts
```


Thank you very much it worked

---

