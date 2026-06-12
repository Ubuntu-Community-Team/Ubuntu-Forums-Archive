---
title: "Folder Permission Mistake"
date: 2012-02-02
forum: General Help
---

### Post by whatever555 on 2012-02-02
Hi guys,

I'm a complete noob to ubuntu so hopefully this is an easy fix..

I used the terminal to set the following for a folder:
sudo chmod 666 /home/username/Videos

Now all folders in that directory cannot be opened and seem to be read as an unrecognisable file type!

Anyway to fix this?


Thanks

---

### Post by sudodus on 2012-02-02
Try ```
sudo chmod [COLOR="Red"]775[/COLOR] /home/username/Videos
```

And browse the internet for linux file permissions and read the manual page
```
man chmod
```

---

### Post by whatever555 on 2012-02-02
Thanks for the reply,

I just manually went in and changed the emblem for each file to Video.

Probably not the best way to do it but solved the problem.



Cheers

---

