---
title: "Booting using grub manually"
date: 2009-07-04
forum: General Help
---

### Post by 7raTEYdCql on 2009-07-04
I recently was trying to boot manually from grub. This is what i tried.

```
root (hd0,4)
kernel /boot/vmlinuz* ro root=hda3
initrd /boot/init*
boot

```

This is what i typed at boot time. It landed me to a "sh" shell. And a listing didn't have anything on my comp. 

The prompt for the shell was "initrmfs" if i recollect it correctly. Can someone help. This was anyway just a casual try, my system otherwise boots properly.

---

### Post by cariboo on 2009-07-04
You are using a wildcard eg: vmlinuz* if you have more than 1 vmlinuz Linux gets confused as to which one to use. You have to be specify which version you want to use.

---

### Post by 7raTEYdCql on 2009-07-04
Nope, i don't remember the fullname that is why i used it. I think it is 2.26-11 or something.

---

