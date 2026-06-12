---
title: "visudo: busy try again later"
date: 2009-12-23
forum: General Help
---

### Post by shariefbe on 2009-12-23
Hello
      I just want to edit the sudoers file but when i tries to open that its showing some error

```

root@ariem-desktop:/usr/local/etc# sudo visudo
visudo: /etc/sudoers busy, try again later
root@ariem-desktop:/usr/local/etc# 

```
i didnt find any sudoers.tmp file
Can anybody help me?

---

### Post by lmarmisa on 2009-12-23
If you are root, you should not use the sudo command.

Simply type:

```

visudo

```Check if the problem continues with this new syntax.

Best regards,

Luis

---

### Post by shariefbe on 2009-12-23
yes thanks. Now it works.
Thanks a lot

---

