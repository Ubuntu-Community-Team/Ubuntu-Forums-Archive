---
title: "System unbootable probably due to permissions"
date: 2011-04-02
forum: General Help
---

### Post by groonrix on 2011-04-02
I rebooted my machine after a normal session.
After trying to boot with kernel 2.6.35-28, the system froze at a textual screen (ubuntu 10.10 with 4 dots under it, "checking battery... [OK]"). The same problem happened when trying to boot with 2.6.35-27.

Then I booted with 2.6.35-28 (Recovery), got netroot shell, and startx-ed with root.
Trying to log out and log in as my user gets me back to the shell, and I can't startx with my user (obviously...).

I think the problem has something to do with permissions:
After copying some files & folders from an external FAT drive, I:
```
usr@mac:~$
``````
find . -type f \( ! -regex ".*/\..*" \) -exec chmod 644 {} \;
``````
find . -type d \( ! -regex ".*/\..*" \) -exec chmod 755 {} \;
```I thought the problem is the fact that .. (which is \home) appears in \home\usr,
but looking at it I saw that since the owner is root, nothing has changed there.

Any help?
Thanks in advance.

---

