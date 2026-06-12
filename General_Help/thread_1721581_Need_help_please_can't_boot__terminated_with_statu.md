---
title: "Need help please: can't boot:  terminated with status 127"
date: 2011-04-04
forum: General Help
---

### Post by ester4 on 2011-04-04
boot fails with the following message:
/etc/default/locale: 5: d_fmt: not found
init: mountall main process (234) terminated with status 127


if I boot to Recovery, is there any way to edit this locale file or to delete it and replace it with a default one? How can I edit the Locale file to fix this problem without being able to boot?

I'd be really grateful if anyone could help me out. Thanks.

---

### Post by techunit on 2011-04-04
Can you attempt to boot into an old kernel?

---

### Post by ester4 on 2011-04-04
No, i couldn't boot from an older kernel either. But I solved the problem. I simply booted from a Live CD, mounted the installed partition, and gksu nautilus to modify the file. Rebooted and back and running.

Thanks for posting to try to help though techunit :)

---

