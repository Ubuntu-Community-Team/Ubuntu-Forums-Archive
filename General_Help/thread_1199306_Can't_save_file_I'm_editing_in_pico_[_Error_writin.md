---
title: "Can't save file I'm editing in pico: [ Error writing smb.conf: Permission denied ]"
date: 2009-06-28
forum: General Help
---

### Post by Palu on 2009-06-28
I can't save my Samba config file. I can't exit Pico to look at permissions because I'd lose too much typing. However, I can't save the file as something new (using F3: write to disk) OR overwrite something old. If I can save it somehow, how? If I can't, why did this happen? Reading suggests lack of write permissions on the file, but since I can't write to a new file either, I'm confused.

Thanks! :popcorn:

---

### Post by mcallenSchmee on 2009-06-28
Maybe you are trying to save it in a folder that you do not have write permission in. Try saving it in your home folder then you can copy it and overwrite the old file.

---

### Post by lloyd_b on 2009-06-28
> **Palu said:**
> I can't save my Samba config file. I can't exit Pico to look at permissions because I'd lose too much typing. However, I can't save the file as something new (using F3: write to disk) OR overwrite something old. If I can save it somehow, how? If I can't, why did this happen? Reading suggests lack of write permissions on the file, but since I can't write to a new file either, I'm confused.

Thanks! :popcorn:

Whenever you're editing files outside of your home directory, you'll probably need to "sudo nano <filename>" to get root permissions for the task.  

The "/etc" directory, like many system directories, is set so that only root can create new files, and most files in it are set so that only root can write changes to them.

I don't know of any simple solution for this, other than to remember the "sudo".  Some editors (like vim) will explicitly tell you that you're editing a read-only file - I guess nano doesn't.

Lloyd B.

---

### Post by Palu on 2009-06-28
Thanks. You guys were completely correct.

---

