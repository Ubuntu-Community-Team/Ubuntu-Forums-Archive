---
title: "Remove directory from $PATH"
date: 2011-04-19
forum: General Help
---

### Post by towheedm on 2011-04-19
I can add a directory to my $PATH variable with:
```
PATH=$PATH:/some/dir
```How do I remove a directory from my $PATH variable?

Thanks.

---

### Post by davetv on 2011-04-20
This link has a tutorial

[http://www.karakas-online.de/forum/viewtopic.php?t=722](http://www.karakas-online.de/forum/viewtopic.php?t=722)

---

### Post by towheedm on 2011-04-20
Thanks for the link.  For the average user, understanding sed could be a nightmare.  I have only just started learning regex's and sed.  There must be some simpler method for the average user.

---

### Post by wojox on 2011-04-20
If the folder is inside your /home directory reboot or edit .bashrc. Outside your /home look in /etc/profile

---

### Post by mcduck on 2011-04-21
> **towheedm said:**
> I can add a directory to my $PATH variable with:
```
PATH=$PATH:/some/dir
```How do I remove a directory from my $PATH variable?

Thanks.

Did you add that to some setting file, or did you just execute it?

If you added it to any file, remove it and log out & back again. 

And if you didn't add it anywhere but just executed it, it will disappear from your path automatically when you log out. I believe running "reset" to reset your shell might also work.

---

