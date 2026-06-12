---
title: "Root-User : Unset"
date: 2010-10-14
forum: General Help
---

### Post by TheAnachron on 2010-10-14
Hey guys, I've just read [this post]("http://ubuntuforums.org/showthread.php?t=1486138").
A friend of mine has told me to set a root password and use root (f.e. switching to su in terminal and work with root rights instead).

Is there any way to unset the root password? I know how to use sudo now.

---

### Post by sisco311 on 2010-10-14
Yep, you can lock the root account password with:
```
sudo usermod -p '!' root
```

---

### Post by TheAnachron on 2010-10-14
Is this the exact same thing as after the installation of Ubuntu?
Is there anything I should take care of?

---

### Post by sisco311 on 2010-10-14
> **TheAnachron said:**
> Is this the exact same thing as after the installation of Ubuntu?

Yes.

> **TheAnachron said:**
> 
Is there anything I should take care of?

Make sure that your user has full sudo rights. It's in the **admin** group & the sudoers file contains the following line: **%admin ALL=(ALL) ALL**.

```
groups
```
```
sudo cat /etc/sudoers
```

---

### Post by robert_pectol on 2010-10-14
The following will remove the root account password altogether, thereby making it like it was originally.
```

sudo passwd -d root

```

*** NOTE**
Nevermind this post.  While it disables logging in to root using su, it does allow local terminal access to root without a password so probably NOT what you're looking for.

---

### Post by sisco311 on 2010-10-14
> **robert_pectol said:**
> The following will remove the root account password altogether, thereby making it like it was originally.
```

sudo passwd -d root

```

Nope, that deletes the password. By default the root account password is locked. See:
```
man passwd
```

---

### Post by robert_pectol on 2010-10-14
Yeah, I just realized that my suggestion allows LOCAL terminal logins to root without a password so definitely **not** how it is by default!  I'll make a note on my post above.

---

### Post by TheAnachron on 2010-10-28
Thanks guys, this helped me.

---

### Post by sisco311 on 2010-10-28
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

### Post by TheAnachron on 2010-10-29
I did! Thanks again, really great help here.

---

