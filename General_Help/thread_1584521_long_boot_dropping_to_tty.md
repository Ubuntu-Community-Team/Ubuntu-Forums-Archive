---
title: "long boot dropping to tty?"
date: 2010-09-29
forum: General Help
---

### Post by garyed on 2010-09-29
Lately about half the time I boot up on 9.10 it stays at the tty & asks for my login & password. It will just stay there for about a minute or so & then
boot up normally whether I enter anything or not. I have it set for auto-login & it never was a problem before. Some times it boots up normally without going into the login screen at all. The only thing that is different is one of the 5 year old kids I let use the computer for the internet & the computer doesn't always get shut down right(turn the power off). I suspect that has caused the problem but it happens now even when I know its been shut down right.
Any ideas?

---

### Post by Rubi1200 on 2010-09-30
Try running fsck from the LiveCD; if there are problems, it should pick up on them and repair any issues.

Hope this helps.

For example: 

```
e2fsck -f /dev/sdax
``` (where x represents the partition if you have more than 1 OS installed or just sda if Ubuntu resides on the whole drive) 

Note: this is for ext2/3 file-systems.

You can also run ```
fsck -f /dev/sdax
``` (comments as above)

---

