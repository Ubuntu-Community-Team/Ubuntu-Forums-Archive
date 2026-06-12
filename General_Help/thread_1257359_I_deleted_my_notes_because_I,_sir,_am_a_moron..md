---
title: "I deleted my notes because I, sir, am a moron."
date: 2009-09-03
forum: General Help
---

### Post by Bushido989 on 2009-09-03
I figured I'd delete kde, as I never use it. Little did I know that upon deleting itself and various accompanied software...it decided to take Basketnotepads with it. I is there a means of getting it back with notes intact? Are the notes themselves still left in some folder?

any help would be greatly appreciated.

---

### Post by sisco311 on 2009-09-03
> **Bushido989 said:**
> I is there a means of getting it back with notes intact? Are the notes themselves still left in some folder?

any help would be greatly appreciated.

just reinstall the application:
```
sudo apt-get install basket
```

the config files and data should be still somewhere in your home directory (perhaps in ~/.kde/basket)

---

### Post by Bushido989 on 2009-09-03
> **sisco311 said:**
> just reinstall the application:
```
sudo apt-get install basket
```

the config files and data should be still somewhere in your home directory (perhaps in ~/.kde/basket)

I totally came in my pants when I saw them there. Thanks.

---

### Post by sisco311 on 2009-09-03
Cool! You're welcome! 

Please mark your thread as solved (for instructions see the link in my signature).

---

### Post by BornTwisted on 2009-11-14
For anyone else looking for the location I found mine in:

~/.kde/share/apps/basket/baskets

---

