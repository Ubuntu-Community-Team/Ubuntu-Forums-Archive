---
title: "&quot;Startup Applications&quot; changes not saved"
date: 2011-11-20
forum: General Help
---

### Post by tlee on 2011-11-20
Greetings,

I'm having some trouble with "Startup Applications" in Unity.  It doesn't save my changes.  Specifically, I'm trying to disable the login sound, but when I tried to change other items in the list, those changes also were not saved.

Any thoughts?

This is Unity in 11.10, running on a MacBookAir 4.2.


Cheers!

---

### Post by lechien73 on 2011-11-20
I had a similar problem with earlier editions of Ubuntu, and it came down to a permissions problem with the ~/.config/autostart directory.

I fixed it by opening a terminal window and running:

```
sudo chmod -R o+wrx /home/USERNAME/.config/autostart
```

Obviously replacing USERNAME with your current login name, which will be shown before the @ sign in the command prompt.

---

### Post by tlee on 2011-11-20
Yup, success.  Thanks!

---

