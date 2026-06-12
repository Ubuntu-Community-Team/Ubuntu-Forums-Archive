---
title: "chromium cookie problem after upgrade to 12.04"
date: 2012-05-27
forum: General Help
---

### Post by Meijuh on 2012-05-27
I am having this weird problem with my notebook. Ever since I upgraded from 11.10 to 12.04 chromium does not log me in automatically for facebook and some other websites. However, for this website (ubuntuforums.org) chromium does remember me.
So, I have this strong feeling this happened directly after the upgrade. I sync my google account with two other pc's and on those pc's my login is remembered for each website, so I don't think it has to do with google sync. Also, I already tried purging chromium-browser with apt-get and deleted the temporary files in ~/.cache/chromium with no luck.

So, what is going on here?

---

### Post by eleftg on 2012-05-27
You can try:

```
rm ~/.gnome2/keyrings/*
```

This is where chromium stores its login info. But BE CAREFUL! Your passwords will be deleted and this is also where your passwords for wifi networks etc are stored!

---

### Post by Meijuh on 2012-05-27
I am using gnome 3 (so not unity). I do not have a gnome2 folder. Is it possible that it has anything to do with the new privacy functionality in ubuntu 12.04?

---

### Post by eleftg on 2012-05-27
Can you post the output of this command?

```

cd ~ && find . -iname '*keyring*'

```

---

### Post by Meijuh on 2012-05-27
It shows .gnome2 instead of gnome2.

Sidequestion, why is this folder present if I do not have gnome2?

I' ll try to remove the contents of this folder.

---

### Post by eleftg on 2012-05-27
Right... Sorry, I am editing the error in the previous post. I can't answer your sidequestion because it's my question too :-D

---

### Post by Meijuh on 2012-05-27
I removed the contents that folder, but it seems nothing has happened. Also, my wifi passwords were not forgotten, i.e. I did not have to reenter my wifi passwords.

Overall, it is very weird behaviour, because -- for example -- my iGoogle and facebook account are always forgotten when I close chromium, but -- for example -- ubuntuforums is not forgotten. So I have no idea why this behaviour is so selective.

---

