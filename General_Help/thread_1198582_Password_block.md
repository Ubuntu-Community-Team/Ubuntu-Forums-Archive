---
title: "Password block"
date: 2009-06-27
forum: General Help
---

### Post by DGLA on 2009-06-27
Bought an IBM Think Pad laptop at a garage sale. Thought it had windows but ubuntu came up and asked for my password. No clue as to what it might be. Does ubuntu have a means of changing the password like windows? Thanks

---

### Post by mhgsys on 2009-06-27
reboot into recovery modes 

This will drop you in a root console.
There type:
```

 cd /home/

```
(this will take you to your home directory, once there type;

```

ls -a

```
to get a list 

You'll find your username there.
then type

```


passwd yourusername


```

Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

Reboot; and you can login again.

---

### Post by siryuhan on 2009-06-27
* never mind

---

