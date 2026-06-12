---
title: "System Halted on shutdown"
date: 2009-07-01
forum: General Help
---

### Post by 1868ccMGB on 2009-07-01
Thank in advance for your help. When I try to shut down my IBM T20 laptop the computer will shut down almost all the way and then display a message:

[1278.112331] System Halted.

When I just tell the computer to restart it does fine, it just won't shut down.
Any suggestions?
Thanks,
Rob
Ubuntu 9.04

---

### Post by 1868ccMGB on 2009-07-02
Any suggestions?

---

### Post by madnessjack on 2009-07-30
Same problem on a Compaq Presario P4 desktop

---

### Post by armagedonc on 2009-08-23
same problem here amd "piece of crap" sempron

---

### Post by P4man on 2009-08-23
try this: in the grub menu (press Esc to show it if needed), press "e" to edit the first, normal grub entry. Then select the line starting with kernel, and press "e" again. At the end add this switch:

```
acpi=force
```

Press enter to confirm, then "b" to boot.

This switch will only be active for 1 boot, but see if it shuts down properly then, and no other problems occur. If so, you can make it permanent by modifying grub's menu.lst. Also feel free to submit a bug report so the kernel guys can fix this.

---

