---
title: "Can't delete WINE folder!"
date: 2009-08-02
forum: General Help
---

### Post by jars121 on 2009-08-02
G'day guys,

I installed Wine a while back, and uninstalled it pretty much straight away. Now, when I go to any folder or file and go to 'open with', every second application listed is 'a wine application', and I have no idea how to fix that.

I went into usr/share/ and I found a Wine folder, but I cannot delete it. I have tried sudo rm ~/usr/share/wine and I get the cannot delete file or folder: no such file or directory.

Any help on deleting that folder and completely cleansing my computer from this program would be very greatly appreciated!

Cheers,

jars121

---

### Post by credobyte on 2009-08-02
```
suro rm -r /usr/share/wine

```

---

### Post by Vaphell on 2009-08-02
you tried to delete /home/yournickname/usr/share/wine (~ = your home dir) no wonder there is no such dir.
But i don't think manually deleting it would solve your problem with file associations and such.

---

### Post by jars121 on 2009-08-02
> **credobyte said:**
> ```
suro rm -r /usr/share/wine

```

Thanks for that credobyte! That deleted the folder with no problems at all. 

I still have the annoying problem of having 50 'a wine application''s listed in open with.

Any idea how to get rid of them, or maybe refresh the open with program?

Thanks for your help so far guys.

Cheers

---

