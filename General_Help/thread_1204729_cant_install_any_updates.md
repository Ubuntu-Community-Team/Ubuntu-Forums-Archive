---
title: "cant install any updates"
date: 2009-07-05
forum: General Help
---

### Post by spinonefan on 2009-07-05
I have just bought a used netbook, it is showing that there are 279, none of which will install, it says manually run dpkg--configure-a which I have tried but it just says bad command, can anyone help

---

### Post by 3rdalbum on 2009-07-05
That should be:

```
sudo dpkg --configure -a
```

There's a space in between the "g" and the first hyphen, and a space between the e and the third hyphen.

---

### Post by spinonefan on 2009-07-05
I have tried it with sudo and the correct spacing, still doesnt like it, any other suggestions please?

---

### Post by diablo75 on 2009-07-05
> **spinonefan said:**
> I have tried it with sudo and the correct spacing, still doesnt like it, any other suggestions please?

Could you please copy and paste the contents of your terminal window so we can see what you're typing in and what it's giving you in response?  Use the Edit>Select All and Edit>Copy then paste in here.

Alternatively you could try again by copying the command out of the "Code:" box above and use the Edit menu in Terminal to paste it in and run it.

---

### Post by spinonefan on 2009-07-05
Finally got all 279 updates installed, thanks

---

### Post by cycling-rod on 2009-07-05
spinonefan, Please tell what you did or how you solved your update problem - your solution (accidently or otherwise arrived at) could help others in the future.
Thanks
Rod

---

