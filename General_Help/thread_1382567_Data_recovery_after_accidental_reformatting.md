---
title: "Data recovery after accidental reformatting"
date: 2010-01-16
forum: General Help
---

### Post by pertti on 2010-01-16
Ok, so I just erased +200GB worth of photos, documents, music and videos on my external hard drive.

I wanted to try the new Ubuntu Lucid Lynx Alpha 2, so I downloaded the .iso, launched the live USB disk creator and tried to format my 1GB pendrive to make room for the OS. Somehow, I ended formatting my 320GB external USB hard drive. The hard drive had to partitions (one EXT3 and one NTFS), but now it only has a FAT partition that spans the whole drive.

So far I've only found solutions for deleted partitions, but not for reformatted ones (e.g. [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), [http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)).

I understand that the new FAT partition may have erased the EXT3 data structures at the beggining of the partition, making file recovery next to impossible, but still any help would be greatly appreciated.

PS: A confirmation dialog on the live USB disk creator wouldn't have hurted either...

---

### Post by mechro on 2010-01-16
Your links mention **Testdisk**. Have you tried that for partition table recovery?

---

### Post by pertti on 2010-01-16
> **mechro said:**
> Your links mention **Testdisk**. Have you tried that for partition table recovery?

I used Testdisk, but it only found the new FAT partition. Now I've looked into it again and I've seen a "Deeper search" besides the "Quick search" option I used, how silly of me... It's still running, but so far it seems to have found the EXT3 partition :D. I will report back if a make any progress.

Thanks a lot, mechro!!

---

### Post by mechro on 2010-01-16
If you get stuck this link may give you some guidance...

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by pertti on 2010-01-17
I haven't had much time this weekend to work on the hard drive, but at least I got all my photos back using [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") (from the maker of testdisk) :D. At first i tried running photorec with all the supported filetypes on, but it started recovering a lot of MP3s and some other files, but they were mostly garbage or incomplete. The I selected just JPEG files and it worked!

Testdisk was able to find both the EXT3 and the NTFS partitions. The NTFS partition seems fine, it was located at the end of the hard drive and it was untouched by the reformatting process. On the other hand, the EXT3 partition is corrupted to some degree, and testdisk is unable to show me its contents. I will look into it, but I don't think I will get much further.

Still, I got my photos back, which I missed the most.

---

### Post by mechro on 2010-01-18
If you have spare storage you could make an image of the drive and work on that with Testdisk i.e. delete the current partition table, reboot and rerun Testdisk.

I'm not saying it will work but it's worth a try if you've got plenty of storage to make images and back-ups.

I see you've found Photorec which is good for recovering lots of filetypes.

---

