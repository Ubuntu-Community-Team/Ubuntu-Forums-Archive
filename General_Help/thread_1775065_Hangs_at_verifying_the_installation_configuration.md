---
title: "Hangs at verifying the installation configuration"
date: 2011-06-04
forum: General Help
---

### Post by Letterbomb05 on 2011-06-04
Hi,

I'm trying to install Ubuntu 11.04 inside windows using Wubi. However, when I reboot the computer and select ubuntu, I'm faced with an installation popup box which sys "Verifying the installation configuration...". The progress bar becomes full and then it just hangs and does not progress any further into the installation. 

The console within the install window shows:

```

Jun 4 09:54:09 ubuntu kernel: [ 1 502.631621] ata4: EH complete
```

However, I've noticed that it does occasionally change, as this appeared earlier:

```
Jun 4 09:54:46 ubuntu kernel: [ 1 501.867289] ata4: SError: { PHYRdy Chg Dispar LinkSeq TrtaTrns }
```

Then it pretty much just returned to the previous message. Anyone help? :confused:

Much appreciated

Edit:
Now stuck on the following
```

Jun 4 10:17:01 ubuntu CRON[5893]: (root) CMD (   cd . && run-parts --reports /etc/cron.hourly)

```

Been on the "verifying the installation configuration" bit for over an hour now.

---

