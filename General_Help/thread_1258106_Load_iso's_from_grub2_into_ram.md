---
title: "Load iso's from grub2 into ram"
date: 2009-09-04
forum: General Help
---

### Post by gavshouse on 2009-09-04
hi ive got grub 2 installed but im wanting to boot of some .iso's that load into my ram i have a few in mind but would want to add my own later i have this example, it does boot but when booting for example in slax it fails its not a grub error its a slax error though and it tells me to restart.

i have read alot about this but cant seem to get it right if anyone could correct this below it would help

example
```
menuentry "Slax ISO=slax-6.1.2.iso"{
loopback loop (hd0,1)/boot/slax/slax-6.1.2.iso
linux (loop)/boot/vmlinuz slax from=/boot/slax/slax-6.1.2.iso root=/dev/ram0 irqpool
initrd (loop)/boot/initrd.gz
}
```

Ive used the same example but with /bt3/bt3-final.iso which is backtrace 3

any idea's ?

---

