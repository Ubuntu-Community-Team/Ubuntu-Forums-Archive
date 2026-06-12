---
title: "I deleted a file and now I need it back!"
date: 2010-11-10
forum: General Help
---

### Post by DaveGiant on 2010-11-10
Hi,

Pretty dumb really.

I deleted a folder called cms. It isn't in my recycle bin.

One of two things happened.

1) I already have a folder in the bin called cms. Thus... I don't know.. it didn't make it to the bin?

2) The folder was in the /opt folder so I don't know, maybe the bin only catches things deleted from the home folder.

Either way. Has this folder really gone?

---

### Post by Ancanus on 2010-11-10
If you used rm, it never reached the trash.

---

### Post by DaveGiant on 2010-11-10
I used left click to select folder -> del

---

### Post by DaveGiant on 2010-11-11
So do I need to re-program the class I deleted or can be retrieved?

---

### Post by Elfy on 2010-11-11
If you did it as root - then it will be in root's trash not your's.

---

### Post by DaveGiant on 2010-11-11
I don't know what I did it as, where is the roots trash?

---

### Post by Elfy on 2010-11-11
```
gksudo nautilus /root/.local/share/Trash
```

---

