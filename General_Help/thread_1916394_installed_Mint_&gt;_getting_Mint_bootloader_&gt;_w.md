---
title: "installed Mint &gt; getting Mint bootloader &gt; want Ubuntu bootloader back"
date: 2012-01-27
forum: General Help
---

### Post by xianbei on 2012-01-27
As the title says, i've installed mint to give it a try; unfortunately now my computer is booting from the mint partition.

How can i change it back so i get the Ubuntu bootloader back?

Ubuntu 11.10

Thanks!

---

### Post by xianbei on 2012-01-27
OK. nevermind. i found it.

fyi...

i ran gparted to recall which device my version of ubuntu was installed.

i then re-installed(?) grub there using:

```
sudo grub-install /dev/XXX #where XXX was sda in my case
```

---

