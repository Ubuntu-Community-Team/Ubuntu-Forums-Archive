---
title: "kernel panic - not syncing : VFS: unable to mount root FS on unknown-block"
date: 2011-02-14
forum: General Help
---

### Post by sunil.gandhi007 on 2011-02-14
hey i compiled a kernel and am trying to boot from it...but it is giving me this error
kernel panic - not syncing : VFS: unable to mount root FS on unknown-block
i m using ubuntu 10.04 and my grub.cfg file is
[http://pastebin.com/BQqQy1hu](http://pastebin.com/BQqQy1hu)

i m still a newbie and need help...plz rply wth apropriate answer...


Thanks in advance...

---

### Post by anglican on 2011-02-14
> **sunil.gandhi007 said:**
> hey i compiled a kernel and am trying to boot from it...but it is giving me this error
kernel panic - not syncing : VFS: unable to mount root FS on unknown-block
i m using ubuntu 10.04 and my grub.cfg file is
[http://pastebin.com/BQqQy1hu](http://pastebin.com/BQqQy1hu)

i m still a newbie and need help...plz rply wth apropriate answer...


Thanks in advance...There's no initrd.img for your custom kernels. Make one with ```
update-initramfs -k 2.6.36.1 -c
``` then tell grub about it with ```
update-grub
```(or editing menu.lst if you're using grub-legacy). I'd recommend adding a suitable text to your kernel name to indicate that it is a custom one using the "--append-to-version" option when you make the kernel e.g. --append-to-version=custom

H

---

### Post by sunil.gandhi007 on 2011-02-17
thanks....
it ws of great help...

---

