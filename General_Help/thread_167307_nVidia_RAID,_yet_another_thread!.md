---
title: "nVidia RAID, yet another thread!"
date: 2006-04-28
forum: General Help
---

### Post by P-J on 2006-04-28
Hi all!

I have an nForce 3 based board in my desktop and am currently using Windows XP on a striped array using two SATA disks. Since it's nForce, I realise it's not true hardware RAID and relies on software to some extent.

I booted the Ubuntu Live CD (and the full install CD) and Ubuntu recognises two separate SATA disks (formatted NTFS) instead of the virtual striped disk. Obviously, I can't install Ubuntu here since it'll kill the RAID array. So, I have two questions...

1) Is there *any way whatsoever* that I could install Ubuntu on an existing striped RAID array on this controller? I realise this thread has been posted a million times but I haven't seen a conclusive 'no'.

2) Can anyone recommend a reasonably priced SATA raid controller card that would work in Ubuntu and present a stripe as a single disk?

Any help MUCH appreciated ;)

---

### Post by DexterBelgium on 2006-04-28
[http://forums.gentoo.org/viewtopic-t-258981-highlight-gen2dmraid.html](http://forums.gentoo.org/viewtopic-t-258981-highlight-gen2dmraid.html)

How about this? dmraid? I don't know what the status of this is under Ubuntu, but this seems to be your best bet for the "fakeraid" on an Nvidia board.

---

### Post by P-J on 2006-04-28
Cheers for the info, I'll look into that!

Thanks!

---

