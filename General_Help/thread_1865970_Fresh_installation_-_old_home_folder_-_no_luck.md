---
title: "Fresh installation - old home folder - no luck"
date: 2011-10-20
forum: General Help
---

### Post by micheledm on 2011-10-20
hello guys, i just made a new Ubuntu 11.10 installation on my old laptop. As I've been doing for quite a long time I installed the OS on a partition and then mounted my old /home partition. 

In LightDM i can actually see my username, i try to login but after displaying for few seconds a black screen with a couple of messages which I suppose are from the tail of boot log, it falls back to the login screen.

I tried to reset .config, .gnome, .gnome2 and .compiz with no luck. Also I checked /var/log/lightdm but I don't see any particular error message.

it's not a graphic issue or installation problem because i can easily login with guest account.

What else can I check out?

Thank you

---

### Post by lovinglinux on 2011-10-20
Try to delete **~/.config/compiz-1/compizconfig/config**, this solved for me when I wasn't able to login properly into Unity 3D, but I don't get black screen like you.

BTW, can you login normally using Unity 2D?

---

### Post by micheledm on 2011-10-21
Yes, I forgot to mention that it happens with unity 2D.

I had already deleted the whole .config folder just to be sure together with .gnome, .gnome2, .compiz and .metacity

---

### Post by lovinglinux on 2011-10-21
> **micheledm said:**
> Yes, I forgot to mention that it happens with unity 2D.

I had already deleted the whole .config folder just to be sure together with .gnome, .gnome2, .compiz and .metacity

It didn't solve the problem?

Then delete again and run:

```
unity --reset
```

---

### Post by micheledm on 2011-10-21
No, it didn't solve the problem.

I also tried unity --reset but it says it can't find any display since there's no X running(i run it from admin shell)

---

### Post by AbtZ on 2011-10-21
If you create a new test account, does it login correctly?

I would try two things, if I were you:
1. Another WM/DE, with the same profile. Your choice, but I suggest doing it with Openbox.

2. Create a new login (with the same name, if you wish, but then you have to move/rename the old home folder), and put all the files you want to keep from the old home in the new directory. 

Even though I keep my /home over subsequent install I do this occasionally just to remove cruft.

---

