---
title: "Swap-block doesn't mount/swapon automatically.."
date: 2010-12-06
forum: General Help
---

### Post by tajiknomi on 2010-12-06
[SIZE=2]Today i open up G-parted and see their that my ***swap-block*** is not mounting ***automatically*** on start-up, when i reboot my OS,Again open up to see ... but same problem, swap-block doesn't mount/Swapon automatically, Every time i had to do it ***manually***...

How to get rid of this....? [/SIZE]

[SIZE=2]Moreover, ***My FSTAB :-***
 ```
[SIZE=3]proc /proc proc nodev,noexec,nosuid 0 0
UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca / ext3 errors=remount-ro 0 1
UUID=32B4D35146D6CA5D /media/Extra ntfs-3g defaults,utf8,umask=007,uid=1000,gid=1000 0 1
UUID=71C9C32D0D73D38C /media/My_Data ntfs-3g defaults,utf8,umask=007,uid=1000,gid=1000 0 1
UUID=232D470307EF2C88 /media/My_Media ntfs-3g defaults,utf8,umask=007,uid=1000,gid=1000 0 1[/SIZE]
```Have a look at the ***Screen-shot*** also .. it  is attached herewith...
[/SIZE]

---

### Post by tajiknomi on 2010-12-06
[SIZE=2]I had told one of my friend to check his FSTAB, in his FSTAB, he told me that it contain a line for swap-drive,.....while in mine, i haven't...

therefore i find My UUID for swap and add that line in my FSTAB, but same problem..... :(
[/SIZE]

---

### Post by wojox on 2010-12-06
Have you looked at [SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by tajiknomi on 2010-12-06
[SIZE=2]Problem is solved :p, all i just add the line to My FSTAB ...

[/SIZE]```
[SIZE=2]/dev/sda7 none swap sw 0 0[/SIZE]
```

---

