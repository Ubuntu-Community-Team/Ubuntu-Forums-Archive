---
title: "How to know directory's size in terminal?"
date: 2011-01-04
forum: General Help
---

### Post by tranduyhung on 2011-01-04
Hello,

Is there any way we could display dicrectory's size in terminal? Because I need to copy directories to external devices like USB, so I need to know there is enough space left on my USB for those directories or not. I tried ls command but still couldn't find out.

Thank you for your replies :).

Regards,
Hung

---

### Post by artaxerxes on 2011-01-04
try using the du command.

 add -s to a summary value (without it you get each a value for each subdirectory)
 add -h to get rounded "human readable" values

as always check out the man pages for more info.

---

### Post by tranduyhung on 2011-01-04
Awesome!

Thank you so much! :)

---

