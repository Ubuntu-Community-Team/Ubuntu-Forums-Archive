---
title: "Setting permissions"
date: 2010-10-23
forum: General Help
---

### Post by Phildough on 2010-10-23
Before you read any further- know that I'm a total ubuntu newbie :P

**tl;dr at bottom!**

Anyways-
I just set up my first ubuntu server (following several tutorials on the web...) for me 'n my roommates. I have a "Public" folder in the /home/ directory, that I want to be completely accessible to anyone. (Everyone has their own folder also in the /home/ directory that is private to the individual user). So I used "chmod +rwx /home/Public" in terminal to give everyone read, write, and execute privelages (I'm stating what everything does so if I'm wrong one of you ubuntu gurus can correct me) and that works- but everything IN that folder is still only accessible to the admin account. 

For example, if someone wanted to upload a directory of music to that folder (/home/Public/music), they could, but then they could not access the directory they just made. IE, anything created in that folder automatically gets its permissions set to only be accessed by the admin account. How can I change that?

tl;dr: How can I set the default permissions for the newly added contents of a folder to be open to anyone?

---

### Post by perspectoff on 2010-10-23
chmod -R rwx

-R means recursive

If using a file manager (such as Nautilus or Dolphin), you can also right-click on a folder (or file) and set permissions that way. There is a box to tick to include all folders and files within that folder.

---

### Post by cavh on 2010-10-23
I think what you need is the ```
chgrp
``` command:

See this thread [http://ubuntuforums.org/showthread.php?t=511280]("http://ubuntuforums.org/showthread.php?t=511280")

and view the help for this command by typing

```
man chgrp
```

in a terminal.

Welcome to Ubuntu - a smart move.

---

### Post by Morbius1 on 2010-10-23
Are you talking about different login users on the box or different remote users connecting to the box?

If you're using Samba please post the output of the following command:
```
testparm -s
```

---

### Post by Phildough on 2010-10-23
Thanks- worked perfectly!

Ended up using the command:

chmod -R a+rwx /home/Public

and it fixed everything!

---

### Post by Phildough on 2010-10-23
> **Morbius1 said:**
> Are you talking about different login users on the box or different remote users connecting to the box?

If you're using Samba please post the output of the following command:
```
testparm -s
```

Not using Samba. But yeah, talking about both login users on the box AND via remote login with SFTP. 

Anyway, it's fixed, so thanks again :) Now how do I set this thread to "SOLVED"....?

---

