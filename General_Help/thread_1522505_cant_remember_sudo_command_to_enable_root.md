---
title: "cant remember sudo command to enable root?"
date: 2010-07-02
forum: General Help
---

### Post by gareth40 on 2010-07-02
I have done this before and its driving me insane, i just cant remember what command it was and google isnt revealing anything either.

i usually type:

"sudo command" and it asks my password which is ok, but i have a bunch of commands to issue as root and dont want to have to type sudo each time

this is what I want to see:

root@localhost:

instead of

username@computername:

I know i have to type sudo, but what else?

---

### Post by SoFl W on 2010-07-02
This might help you remember next time.
Sudo = "su do"
SuperUser DO

To become root you need to type "su"

---

### Post by philinux on 2010-07-02
The preferred method of obtaining a root shell is :

```
sudo -i
```

---

### Post by celldweller1591 on 2010-07-02
use this :-
> sudo bash

---

