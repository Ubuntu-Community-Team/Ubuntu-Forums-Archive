---
title: "Setting up user privileges from the command line?"
date: 2009-09-22
forum: General Help
---

### Post by wulf on 2009-09-22
How do I set up user privileges from the command line? Specifically, I want to enable "Share Files with the Local Network" via the script I use to create new user accounts rather than having to manually open the user dialog box in the GUI (Xubuntu 8.04 although, as I want a CLI solution, I suspect it applies to all variants).

I've tried lots of searching here and on Google as well as looking round my local system but haven't hit on the right combination of words to unlock that knowledge!

Thanks,

Wulf

---

### Post by badger_fruit on 2009-09-22
```

useradd new_username
chown xxx /folder/to/chown
chgrp yyy /folder/to/chgrp

```

That should get you started in the right direction (I think!)

---

### Post by P4man on 2009-09-22
I think the users have to be member of the "sambashare" group. To add a user to that group, use "adduser username sambashare"

---

### Post by wulf on 2009-09-22
Thanks for those suggestions. I'm still not sure what the "Share Files with the Local Network" checkbox in the GUI is affecting though.

Wulf

---

### Post by P4man on 2009-09-22
> **wulf said:**
> Thanks for those suggestions. I'm still not sure what the "Share Files with the Local Network" checkbox in the GUI is affecting though.

Wulf

I just told you :)
Checking it makes them member of the "sambashare"  group (and lets them create.. you guessed it, samba shares :)

adduser username sambashare

does the same as checking that box.

---

### Post by wulf on 2009-09-22
I didn't think that would work based on what I'd observed earlier but I've tried it again and confirmed that it acts as you say.

Thanks,

Wulf

---

