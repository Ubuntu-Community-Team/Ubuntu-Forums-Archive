---
title: "File Association Issue"
date: 2009-10-07
forum: General Help
---

### Post by doggbat on 2009-10-07
I just updated to the Ubuntu 9.10 beta, and I am having a weird file association issue.  I attempted searching for similar issues on google with no luck.

All files, regardless of their extension, are recognized by Ubuntu as plain text documents.  Because of this, they all open in gedit, unless another program is specified.  I don't understand why Ubuntu is not recognizing the file extensions.  Any help is greatly appreciated.

Thanks,




doggbAT.

---

### Post by mc4man on 2009-10-07
While i have 2 karmic installs that haven't been affected see here 
( I'd say the best solution is in posts 23 -> 26

[http://ubuntuforums.org/showthread.php?t=1284510&page=3](http://ubuntuforums.org/showthread.php?t=1284510&page=3)

there is a link to bug report earlier in thread if interested

---

### Post by doggbat on 2009-10-07
Thank you very much for the link... Problem solved.

I used the command:

```
sudo update-mime-database.real -V ~/.local/share/mime/
```

Next time I'll search ubuntuforums.org instead of google.. Thank you.

---

### Post by mc4man on 2009-10-07
till it releases look/post in that forum for karmic stuff, could get lost here

---

### Post by nirax on 2009-10-07
thanks++ 
for command and information - had the same issue (also running 9.10 which you guys helped to fix through your posts.

---

### Post by DodgeV83 on 2009-10-07
> **doggbat said:**
> Thank you very much for the link... Problem solved.

I used the command:

```
sudo update-mime-database.real -V ~/.local/share/mime/
```

Next time I'll search ubuntuforums.org instead of google.. Thank you.

Thanks for the fix!  Happened to me too.

---

