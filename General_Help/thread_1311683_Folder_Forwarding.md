---
title: "Folder Forwarding"
date: 2009-11-02
forum: General Help
---

### Post by bernardo06 on 2009-11-02
I was wondering if it is possible to set a folder up so that it automatically forwards certain types of files to another folder.

I have an eeepc 900 with a 4gb and a 16gb flash drive. I was wondering if it would be possible to set the default music and video folders to forward files over a certain size to the 16gb drive. If this is not possible is it possible to have every file put in the folder to move automatically to another? or is it possible to change the location of the default music, video, docs etc folders?

---

### Post by alphaniner on 2009-11-02
> If this is not possible is it possible to have every file put in the folder to move automatically to another?

This sounds a bit like symbolic linking.

For example, I have a 200GB partition (ext3) mounted at /mnt/bucket.  On that partition I have, for example, a Documents folder.  I deleted the Documents folder in ~ and created a symbolic link as follows:

```
ln -s /mnt/bucket/Documents ~
```

Of course, you'll want to copy any files already in ~/Documents to the folder you're linking to.

---

