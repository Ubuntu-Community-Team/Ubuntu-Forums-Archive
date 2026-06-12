---
title: "adding ext4 partition to fstab"
date: 2010-10-25
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-10-25
i am not sure not to finish this line
UUID=d283b277-5df4-4e83-80b1-6021f2fe8272 /media/Label ext4
it is for storage

---

### Post by TeoBigusGeekus on 2010-10-25
```
UUID=d283b277-5df4-4e83-80b1-6021f2fe8272 /media/Label ext4 relatime 0 2
```

---

### Post by WorMzy on 2010-10-25
You're just missing the final three columns. I recommend that you take a look at
```
man fstab
```
It'll explain the columns and their contents better than I'm about to.

The next thing you need is the options that the partition will be mounted with. Generally "defaults" will work fine with ext# partitions, though you can specify other options if you want, such as "auto", to have the partition mounted at boot time. Separate the options list with commas, not spaces; e.g. "defaults,auto,utf8"

The column after the options should be 0, and the final column should either be a "0", "1" or "2". Only the one mounted as / should have "1", the rest should have "2". This column is used by fsck to check the partition for errors. If it is 0, then fsck will skip it.

---

### Post by Morbius1 on 2010-10-25
> **WorMzy said:**
> The column after the options should be 0, and the final column should be a number which is one greater than the highest number in this column. e.g., if you have three ext# partitions, the one mounted as / should always have "1", the next one should have "2", **[COLOR=Blue]and so on[/COLOR]**. This column is used by fsck to check the partition for errors. If it is 0, then fsck will skip it.
Just in case anyone might misinterpret this, there is no "and so on". The available numbers are 0 (never), 1 ( the root partition ), and 2 ( check after root ). You can put a 3 in there but it won't do anything.

---

### Post by WorMzy on 2010-10-25
Ah, right you are. Let me edit that.

---

