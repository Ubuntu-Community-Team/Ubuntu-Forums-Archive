---
title: "how to cope with this notification"
date: 2009-11-17
forum: General Help
---

### Post by Xihui on 2009-11-17
Hello, guys,
After having installed Chinese input methods, I got a line of warning when I opened terminal:
bash: export: `xmodifie...@im=ibus': not a valid identifier

How can I solve this problem?

---

### Post by Aubergines on 2009-11-17
Don't know for sure since I don't have ibus installed. It could be a problem in your .bashrc (or .bash_profile), the ibus daemon not running, or maybe some other bug.

There's some discussion

[http://ubuntuforums.org/showthread.php?t=1322888&highlight=ibus](http://ubuntuforums.org/showthread.php?t=1322888&highlight=ibus)
[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/464060](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/464060)

Just do a forum search for ibus and you'll get more info. But I think the general jist of it is to check your .bashrc (or post it up) and start / restart the ibus daemon.

It looks like it should be "export XMODIFIERS=@im=ibus" rather than "xmodifie...@im=ibus" but I'm guessing that might be just the bash terminal truncating the output. Check anyway.

---

