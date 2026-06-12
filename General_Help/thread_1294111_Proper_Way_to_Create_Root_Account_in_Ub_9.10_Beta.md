---
title: "Proper Way to Create Root Account in Ub 9.10 Beta?"
date: 2009-10-17
forum: General Help
---

### Post by kilowattradio on 2009-10-17
Press Alt+F2 keys enter 
xterm
in the box
In Xterm:
```

sudo su-
passwd: *****
passwd
(current) UNIX password:
Enter new UNIX password: 
Retype new UNIX password: 
exit

```

Is this procedure correct?
:KS

---

### Post by Ocxic on 2009-10-17
It looks like that would work yes; 
However, enabling the root account can be a security risk, you should use "sudo -i" to get a root prompt, this will give you all the features of the root account without actually enabling the account on your system.

---

### Post by iMisspell on 2009-10-17
> **Ocxic said:**
> ...However, enabling the root account can be a security risk...
When people say that, is it because someone can physically walk by the computer and start doing what they want in root, or is there a "remote" security risk and it leaves the computer more vunible across the network/internet ?

_

---

### Post by mike555 on 2009-10-17
> **iMisspell said:**
> When people say that, is it because someone can physically walk by the computer and start doing what they want in root, or is there a "remote" security risk and it leaves the computer more vunible across the network/internet ?

_

-- both --

---

### Post by mike555 on 2009-10-17
If you don't like using the terminal you can install " nautilus-gksu " , then just rt. click on a file to open as root.

---

