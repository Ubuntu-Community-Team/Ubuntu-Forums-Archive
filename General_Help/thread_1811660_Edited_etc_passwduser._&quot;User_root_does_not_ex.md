---
title: "Edited etc/ passwduser. &quot;User root does not exist&quot;"
date: 2011-07-25
forum: General Help
---

### Post by Unknown Frequency on 2011-07-25
Oki that was stupid. I edited the passwd file and accidently connected the lines I wanted to add to the root user code. Now I can't use sudo command to change it back. Is there any way to recover from this increditably stupid mistake?

Thanks alot!

---

### Post by nothingspecial on 2011-07-25
If you boot a live cd on your system, you will be able to access the file and change it back.

---

### Post by Wayne_V on 2011-07-25
you'll need to boot recovery mode and vi the passwd file again:  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

you'll probably have to do it from the live cd given the state the passwd file is in ....

---

### Post by Unknown Frequency on 2011-07-25
Sorry for the spam guys. I figured it out myself. Hope it will help someone else!

I just booted up backtrack 5 live CD /etc/passwd back to: root:x:0:0:root:/root:/bin/bash

ps. I coud not do it from the live ubuntu CD. Don't know why

---

