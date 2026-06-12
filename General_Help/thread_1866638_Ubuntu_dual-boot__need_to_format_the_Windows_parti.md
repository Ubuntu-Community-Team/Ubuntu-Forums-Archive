---
title: "Ubuntu dual-boot : need to format the Windows partiton"
date: 2011-10-21
forum: General Help
---

### Post by mailforbiz on 2011-10-21
Hi

I have a Windows 7 and Ubuntu dual boot configuration on my Dell Latitude (there is also the Recovery partition which I'm leaving intact for now for warranty reasons). For a variety of reasons, I have decided to reinstall my Windows 7 install and I want to format the partition when I do.

Partition 1,2: Windows 7
Partition 2-5: Ubuntu 10.4 (separate /,/home/ and swap)
Partition 6: Dell Recovery partition

Will I have problem reinstalling grub or using boot-repair with LiveCD should work? If that method doesn't work, what do I need to do - backup the MBR somehow?

Thanks in advance!
HT

---

### Post by zvacet on 2011-10-22
Boot-repair should work.

---

### Post by mailforbiz on 2011-10-23
Thanks, just confirmed. Was able to reformat/reinstall and use boot-repair to get back grub using LiveCD.

---

