---
title: "Find by type from terminal?"
date: 2010-06-27
forum: General Help
---

### Post by pmooney78 on 2010-06-27
I'd like to find all files of a specific type (as determined by the terminal "file" command) from the command line ... and haven't been able to figure out a way to do so. For instance, I'd like to be able to find all JPEG files in my filesystem, even if their names don't end in .jp*. It would be helpful to be able to combine this with other tests in find, so that I could type something like "sudo find / -atime 0 -size +1M -type adobeflash" or something like that.

I've looked for ways to hook find up to file and tinkered around with a few ideas involving pipes, but nothing seems to get what I want. Any suggestions?

---

### Post by prodigy_ on 2010-06-27
Hmm. Well, something like ```
find / -type f -print0|xargs -0 file|grep 'JPEG'
``` should theoretically find all JPEG files regardless of their extensions.

---

### Post by pmooney78 on 2010-06-27
Perfect! Exactly what I was looking for. Thank you!

---

