---
title: "Use DD to Wipe Everything"
date: 2010-01-02
forum: General Help
---

### Post by Final Version on 2010-01-02
I'm trying to overwrite everything with plain old zero's so I can literally start from scratch then install Windows Xp Pro.

I'm currently entering
```
dd if=/dev/zero of=/dev/sda bs=4k conv=notrunc
```into terminal. But it just spits out ```
dd: opening `/dev/sda': Permission denied
```

How can I get around this, also I'm using the cd live.

---

### Post by HiImTye on 2010-01-02
try adding 'sudo' to the front of the command, to run it as root

---

### Post by Final Version on 2010-01-02
Now it's just a blinking black box,I assume that means it's working?

---

### Post by chewearn on 2010-01-02
Yes, unfortunately, dd does not provide progress update while in operation.  For future note, if you want to monitor the data transfer, you could use pv.

```
[FONT=monospace]
[/FONT]sudo dd if=/dev/zero | pv | sudo dd of=/dev/sda bs=4k conv=notrunc
```

---

