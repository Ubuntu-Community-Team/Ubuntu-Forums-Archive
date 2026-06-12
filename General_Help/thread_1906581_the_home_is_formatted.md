---
title: "the home is formatted"
date: 2012-01-09
forum: General Help
---

### Post by ihsan on 2012-01-09
Hi
I found after installing ubuntu 10.04.2 and impich2 that home with 80 Gb is unmounted so I mounted it by using storage manager, so the home is formatted, my question can I reinstall the files that were exist in home without reinstalling ubuntu and impich2 again.
Thank you for any help
Ihsan

---

### Post by ajgreeny on 2012-01-09
I am not sure I fully understand your question, but it sounds as if you have a separate /home partition but did not set /home as the mountpoint for that partition when you installed Ubuntu.

If that is the situation you will need to edit /etc/fstab to make sure that the partition mounts at /home every time you boot the machine.

Can you therefore show us the output of the command ```
cat /etc/fstab
``` in terminal and copy it back here.

---

### Post by Double.J on 2012-01-09
Hi there, in addition to ajgreeny, would you be able to provide the output of 
```

sudo parted
p

```

Are you able to read the old home partition from nautilus (the file browser) it should be in the list on the left?

Thank you

---

