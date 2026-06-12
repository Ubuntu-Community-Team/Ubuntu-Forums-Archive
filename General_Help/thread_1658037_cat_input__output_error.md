---
title: "cat input / output error"
date: 2011-01-02
forum: General Help
---

### Post by flyingfishfinger on 2011-01-02
Hi-
I'm attempting to migrate my Windows 7 NTFS installation to a VirtualBox machine according to this guide:

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

but every time I try, cat crashes with an input / output error at exactly 28.3GB / 50GB of my Windows partition.
I know I have an old hard drive with some bad sectors, but so far chkdsk from the Windows Recovery Console fails to run on boot when I ask it to.
As far as I know, ntfsprogs reports no problems but a chkdsk scan from Windows still tells me about bad sectors.
I have a suspicion that cat is crashing because it's running into some of these bad sectors, but I could also be totally off on a wild goose chase.
I would be very grateful if anyone here could shed some light on this problem or point me in the right direction.
Thanks in advance

Rafael

---

### Post by dcstar on 2011-01-04
> **flyingfishfinger said:**
> Hi-
I'm attempting to migrate my Windows 7 NTFS installation to a VirtualBox machine according to this guide:

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

but every time I try, cat crashes with an input / output error at exactly 28.3GB / 50GB of my Windows partition.
**I know I have an old hard drive with some bad sectors**, but so far chkdsk from the Windows Recovery Console fails to run on boot when I ask it to.
As far as I know, ntfsprogs reports no problems but a chkdsk scan from Windows still tells me about bad sectors.
**I have a suspicion that cat is crashing because it's running into some of these bad sectors**, but I could also be totally off on a wild goose chase.
I would be very grateful if anyone here could shed some light on this problem or point me in the right direction.
Thanks in advance

Rafael

Don't use cat because it will stop on any bad blocks, try using **dd** instead set to ignore errors:

```
dd conv=noerror,notrunc,sync if=/dev/sdg | VBoxManage convertfromraw stdin blah blah blah....
```

---

