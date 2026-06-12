---
title: "could not delete files"
date: 2010-05-02
forum: General Help
---

### Post by MughalShahzad on 2010-05-02
how delete files from /var/www

when I try to delete file from system gives following messages

"There was an error deleting orderorderform.html."

"Error removing file: Permission denied"

how to solve this please suggest me

Thanks & Regards
Shahzad

---

### Post by Seti on 2010-05-02
All that is telling you is that you don't have permission to remove (delete) those files.

Just do:```
sudo rm 'files'
```

Don't forget to substitute 'files' with whatever files you want to delete from there.

---

### Post by lisati on 2010-05-02
Moved to "General help" (could've gone to "Server platforms")

---

