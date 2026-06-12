---
title: "Terminal password help."
date: 2011-05-07
forum: General Help
---

### Post by Thatguyi445 on 2011-05-07
I'm trying to install java and I've been following the instructions it gives me. It says to type 'su' and enter your password. Well every time I type my password it just says "Authentication Failure". Am I doing something wrong or is something wrong with the terminal? Also I am using 11.04.

---

### Post by mikewhatever on 2011-05-07
Type **sudo -i** instead, then your password. When you are done type **exit**.
PS: Why don't you install java from the Software Center?

---

### Post by spikoley on 2011-05-07
Use *sudo* instead.  Sudo will give you admin rights.

```
sudo command
```

More on [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Thatguyi445 on 2011-05-07
> **mikewhatever said:**
> Type **sudo -i** instead, then your password. When you are done type **exit**.
PS: Why don't you install java from the Software Center?

For some reason I couldn't find java in the software center. At least not when I searched "java". Also thank you.

---

