---
title: "grub question"
date: 2010-06-11
forum: General Help
---

### Post by lunit2 on 2010-06-11
How can I change the selected drives to boot from. I want to set my windows drive first so I don't have to select it each time.

I have ubuntu 10.04.


Thanks.

---

### Post by QIII on 2010-06-11
Rather than trying to do some lengthy explanations, I'll point you to this one.

This guy really has put together a lot of stuff and put a lot of effort into it.  This will likely answer a lot of questions in the future, so it might be worth bookmarking it.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by wilee-nilee on 2010-06-11
> **lunit2 said:**
> How can I change the selected drives to boot from. I want to set my windows drive first so I don't have to select it each time.

I have ubuntu 10.04.


Thanks.

Are they truly dualboots=installed via booted cd.
And post ```
sudo fdisk -l
``` paste it if needed to the terminal it is not a 1 at the end but a small case L

---

### Post by garvinrick4 on 2010-06-11
If you have not done it already go to StartupManager in System/Administration 
and change to what ever OS you want to be highlighted at boot. If not installed yet
use this code.


```
sudo apt-get install startupmanager
```

---

### Post by lunit2 on 2010-06-12
Thanks that worked.

---

