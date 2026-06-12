---
title: "Grub causing grief after using Eee PC 1000HA System Recovery to XP"
date: 2009-11-15
forum: General Help
---

### Post by Akavashi on 2009-11-15
Hey guys,
Have a small little problem... On my Eee PC 1000HA, I have used the Windows XP Recovery Partition (Sorry guys, shame on me lol, but don't worry, still have 9.10 on my Desktop :D) and installed XP.
But my only issue now is that since the recovery overwrote only the Ubuntu Netbook Remix partition, it has left the Grub2 boot loader hanging. The boot loader now gives me a statement saying:
```
GRUB loading.
error: no such partition
grub rescue>
```
Now, from what I understand is that the Eee PC's Quick Boot functionality is stored on the EFI partition and I'm very adverse to formatting it or to using this command to get rid of Grub2:
```
dd if=/dev/null of=/dev/sdX bs=446 count=1
```

So is there any way to remove grub2 without erasing this EFI partition?

Cheers guys! Gonna cry if I can't fix this without erasing that partition :( haha

---

