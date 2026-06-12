---
title: "Unable to use screen after su'ing to another user"
date: 2011-07-21
forum: General Help
---

### Post by CharlesA on 2011-07-21
Hi,

I'm trying to use screen as another user and it spits back the error:

```
Cannot open your terminal &#8216;/dev/pts/0&#8242; &#8211; please check.
```

I found a couple solutions to this, but [one in the archives]("http://ubuntuforums.org/showthread.php?t=90491") mentioned changing permissions or adding the user you are su'ing to to the tty group.

[Another one]("http://blog.hbcom.info/archives/430") mentioned something about using script /dev/null then using screen -r.

Which is the correct way to do this?

Thanks,
Charles

---

### Post by TeoBigusGeekus on 2011-07-21
I don't know the answer, but have you tried tmux? Just saying...

---

### Post by CharlesA on 2011-07-21
> **TeoBigusGeekus said:**
> I don't know the answer, but have you tried tmux? Just saying...
Hadn't heard of that one. Thanks.

---

### Post by TeoBigusGeekus on 2011-07-21
> **CharlesA said:**
> Hadn't heard of that one. Thanks.

I recently discovered it and it is absolutely amazing.
Try it; perhaps it won't give you the error screen does.

---

### Post by CharlesA on 2011-07-23
Bump.

EDIT: I tried tmux but couldn't get it to start detached. Could have been doing something wrong tho.

---

### Post by CharlesA on 2011-07-25
I tried adding the other user to the tty group, but with the permissions to /dev/pts/0 set to 600, that won't do anything.

I decided to just use the [script "work around"]("http://blog.hbcom.info/archives/430") instead of messing around with permissions.

---

