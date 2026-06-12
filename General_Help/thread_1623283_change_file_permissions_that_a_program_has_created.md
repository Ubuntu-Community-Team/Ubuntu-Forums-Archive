---
title: "change file permissions that a program has created"
date: 2010-11-16
forum: General Help
---

### Post by thgis05 on 2010-11-16
Hi.

I have a program what creates files with a certain user and group as owner.
How do I make files created by this program belong to a group I specify myself (I know I can chown and chgrp and chmod but I want the files to have a certain group from the beginning). Also I like to be able to specify permissions for these files.

Btw. it's not my own program so cant change the source code of the program to solve my problem.

Hope my question is clear.

Regards,
Thomas

---

### Post by WorMzy on 2010-11-16
Unless the program has an option for that, you're more or less out of luck. Check in /etc/ for a config file for the program (I'm assuming you run it as a daemon), and see if it lists an option to set the group.

Check the man page too (if it came with one) to see if it says anything about this sort of option.

If the program is an open source program, then you can edit the code yourself and recompile it (if necessary).

If all else fails, try contacting the developer and asking whether they could implement a way to set the group.

---

### Post by thgis05 on 2010-11-16
Thank you for your response.

I will try the things you mentioned.

regards,
Thomas

---

### Post by TSJason on 2010-11-16
You could try setting the sticky bit on the folder where the files are being created?

```
chmod g+s /path/to/data
```

---

### Post by nothingspecial on 2010-11-16
> **thgis05 said:**
> 

Btw. it's not my own program so cant change the source code of the program to solve my problem.



Hi Thomas :)

Yes you can.

That is the whole point of opensource :)

---

