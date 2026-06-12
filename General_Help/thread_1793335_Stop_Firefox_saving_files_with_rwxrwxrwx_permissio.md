---
title: "Stop Firefox saving files with rwxrwxrwx permissions?"
date: 2011-06-29
forum: General Help
---

### Post by gencon on 2011-06-29
Can I somehow stop Firefox from saving files with rwxrwxrwx permissions?

If so how do I set just user rw?

Thanks.

---

### Post by Vaphell on 2011-06-29
how do you save files and where to?

---

### Post by gencon on 2011-06-29
> **Vaphell said:**
> how do you save files and where to?
Typically I right-click and save-link-as to a dir called ~/Downloads by manually selecting that dir. Sometimes I will save a file directly within my dir hierarchy rather than moving it after saving it to ~/Downloads if I'll be keeping the file.

Why would how I save files make a difference?

Cheers.

---

### Post by Vaphell on 2011-06-29
every file gets rwxrwxrwx? i suspected that the target is some external partition not supporting linux permissions or something.

---

### Post by guzjd on 2011-06-29
type in umask in a shell as the user that spawns the firefox process and let me know what that is set to, just to ensure this value hasn't been changed.

---

### Post by Morbius1 on 2011-06-29
What an odd problem.

Even if the umask was set at 000 for some strange reason it would set files to 666 not 777. I don't know of any way to have linux set files to be executable by default.

I'm betting Vaphell is correct in his observation. If there is a mounted ntfs partition and Downloads is symlinked or perhaps bind-ed to that ntfs partition then it would save as 777.

---

### Post by guzjd on 2011-06-29
Right on Morbius! Had to check man page to make sure.  Initially the calculation worked out to 777 :)

---

### Post by guzjd on 2011-06-29
He did state he is saving to ~/Downloads.  Can /home be on a ntfs file system?

---

### Post by guzjd on 2011-06-29
I would also want to know what is the permissions on the ~/Downloads and whatever he meant by directory hierarcy (either root or ~) dir.

---

