---
title: "No username or hostname on commandline"
date: 2010-06-14
forum: General Help
---

### Post by x-shaney-x on 2010-06-14
Due to some re-arranging, I deleted a user and created a new one.
Once everything was setup and that I rebooted but when I log in as the new user, the terminal shows no username or hostname.
I just get a "$" at the prompt and nothing else.

The user details and hostname are all setup correctly and I can't see any problems and everything seems to be working. It just seems odd and I don't like it.

---

### Post by sisco311 on 2010-06-14
Change your user's login shell to /bin/bash:
```
chsh
```

You may also need/want to copy the default .bashrc & .bash_logout file in your user's home directory:
```
cp /etc/skel/.bash* ~/
```

---

### Post by x-shaney-x on 2010-06-14
Ahh, many thanks.  Worked a treat :)

---

### Post by sisco311 on 2010-06-14
> **x-shaney-x said:**
> Ahh, many thanks.  Worked a treat :)

Cool!!!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

