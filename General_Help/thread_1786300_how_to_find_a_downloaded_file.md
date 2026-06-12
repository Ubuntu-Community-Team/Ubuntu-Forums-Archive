---
title: "how to find a downloaded file"
date: 2011-06-19
forum: General Help
---

### Post by fuzzflyer on 2011-06-19
just downloaded a deb file for Picasa  but cant seem to find the actual program  I see icons  but they lead to other files  :(I managed to download skype  and found it/moved it to desktop

 I have just loaded ubuntu onto my laptop  so complete beginner

---

### Post by oldos2er on 2011-06-19
If you downloaded it with Firefox, chances are it's in your Downloads folder (/home/user/Downloads/).

---

### Post by fuzzflyer on 2011-06-19
> **oldos2er said:**
> If you downloaded it with Firefox, chances are it's in your Downloads folder (/home/user/Downloads/).  Yes  I see the folder but can't seem to get it to do anything:( I right click  and tried all the various options   open  /open with etc..  nothing seems to work

---

### Post by nothingspecial on 2011-06-19
Try double clicking it.

If that doesn't work, open a terminal and type

```
sudo dpkg -i ~/Downloads/*.deb
```

That'll install it.

You will have to type your password, which you won't see.

---

