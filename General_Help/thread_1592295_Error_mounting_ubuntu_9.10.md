---
title: "Error mounting ubuntu 9.10"
date: 2010-10-10
forum: General Help
---

### Post by XxNocturnxX on 2010-10-10
Hi!

I've been using ubuntu 9.10 for a while but today when i tried to open it the system fails and gives me this error:

dev/sda6: Superblock last mount time (Thu Dec 9 14:26:35 2010 
[INDENT]now = Mon Oct 11 02:22:59 2010) is in the future[/INDENT]
fsck from util-linux-ng 216
unexpected inconsistency ; RUN fsck MANUALLY
mountall: fsck [482] terminated with status 4
mountall: filesystem failed

type root password for maintenance or type Ctrl-D for closing this shell and retrying.

That's basically what it says. Searching here and google I found the BIOS clock could be wrong but I already checked and that's not the problem. Besides, when I try to enter my root pswd in that shell gives me an error in the login, like Im typing a wrong password (evendoe I'm 100% sure I'm typing the right pswd!!)

I'll appreciate your help!!

Nocturn

---

### Post by Rubi1200 on 2010-10-10
Welcome to the forums :)

Please use the LiveCD and run the following commands:

```
sudo e2fsck -C0 -p -f -v /dev/sda6
```if this returns errors then run this:
```
sudo e2fsck -f -y -v /dev/sda6
```

I am assuming that sda6 is your Ubuntu partition? If it is not, substitute the correct partition number.

---

### Post by XxNocturnxX on 2010-10-17
Thank you so much!

Actually before trying with the livecd i just let it give me the error again to see if it accepted my root pswd and it did. So i ran fschk manually and restart the laptop. But it still gave me the same error so i ran fschk again and that time it worked!

Keep the good work!

Nocturn

---

