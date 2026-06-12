---
title: "Won't Boot Vista After Expanded Ubuntu Partition"
date: 2012-08-03
forum: General Help
---

### Post by purplebetterone on 2012-08-03
Hello, I am computer ignorant and impatient so  in an attempt to expand my Ubuntu partition, I messed up my ability to boot Windows Vista. Running Ubuntu 10.04 and grub 2, unfortunately I no longer have the Windows Repair Disk. Can this be helped by someone with very little expertise?

I know the Windows partition is on SDA/3 . I ran the bootinfoscript and am attaching the resulting text file. Thanks for anyone who  can help.

---

### Post by zombifier25 on 2012-08-03
Before you attempt to resize your Windows partition, you should defrag it thoroughly first. Repartitioning a Windows machine is prone to problems.

The first thing you can do is buy/borrow a Vista installation disk, boot from it, choose Repair > Command Prompt, and run
```
chkdsk /r
```

If you can't get an install disk, you can get a Windows-based recovery live CD/USB (The only I know is Hiren's Boot)

---

