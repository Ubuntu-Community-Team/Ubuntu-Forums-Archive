---
title: "Segmentation fault when trying to mount NTFS partition"
date: 2010-12-17
forum: General Help
---

### Post by Asmodai on 2010-12-17
I have a small NTFS partition with a Windows 7 setup.
I haven't used it for a long time, but today I booted into Windows 7, which worked fine. However, after a reboot I can no longer boot from the W7 partition (leads to an almost immediate reboot) and what's worse, I cannot mount the partition in Ubuntu either (tried both 9.10 and 10.10).
When trying it in Nautilus or manually using[FONT=Courier New] mount.ntfs /dev/sda2 /tmp/ntest, [/FONT]I get messages like the following:

[FONT=Courier New][  123.590083] mount.ntfs[5120]: segfault at 7fff3f1e0ff8 ip 00007ffb6bb820a9 sp 00007fff3f1e1000 error 6 in libntfs-3g.so.79.0.0[7ffb6bb5a000+42000]
[  243.869668] mount.ntfs[7248]: segfault at 7fff6c180ff0 ip 00007f0caada5ce0 sp 00007fff6c181018 error 6 in libc-2.12.1.so[7f0caad2b000+17a000]

[/FONT]Any idea what's wrong and if/how I can get it back working?

---

### Post by Asmodai on 2010-12-18
Update: after trying to view the contents of the partition using WinXP, the partition can be mounted, however it is empty besides the folder "System Volume Information". It shows that only about 60 MB disk space are used (it was >50 GB before that).
It seems like this issue is actually completely unrelated to Ubuntu...
still, is there a data rescue tool for NTFS partitions?

---

