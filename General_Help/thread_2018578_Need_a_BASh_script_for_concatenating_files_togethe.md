---
title: "Need a BASh script for concatenating files together by name-order"
date: 2012-07-06
forum: General Help
---

### Post by wheel_walker on 2012-07-06
ISSUE RESOLVED

I have 256 files, named sequentially, as such:
```
M000.ARC_file8.bin
M001.ARC_file8.bin
M002.ARC_file8.bin
M003.ARC_file8.bin
...
M***.ARC_file8.bin
...
M255.ARC_file8.bin
```Each file is 64 bytes long.  I need to concatenate them together into one big file, in the same sequence as they are named (M000.ARC_file8.bin is first, M001.ARC_file8.bin is second, M002.ARC_file8.bin is third, and so on, until it's done with M255.ARC_file8.bin).

---

### Post by diesch on 2012-07-06
```
cat M*.ARC_file8.bin > one_big_file
```

---

### Post by GreatDanton on 2012-07-06
I don't exactly understand what you wanted to do, but when I want something to sort by name (for example names in tekst) I usually use this command:
```
cat #name of the file# | sort > #name of the file you want to output#
```

I hope this will help you.

Edit: diesch was faster :)

---

### Post by wheel_walker on 2012-07-06
I want to past all these little files together into one big file, in the order by which they are named.

---

### Post by aromo on 2012-07-06
> **GreatDanton said:**
> I don't exactly understand what you wanted to do, but when I want something to sort by name (for example names in tekst) I usually use this command:
```
cat #name of the file# | sort > #name of the file you want to output#
```

I hope this will help you.

Edit: diesch was faster :)

This wouldn't do what the OP intends.  This would sort the CONTENTS of #name of the file# and save the sorted contents in #name of the file you want to output#

diesch's answer is the right one.

---

### Post by wheel_walker on 2012-07-06
It worked, thanks diesch!

---

### Post by GreatDanton on 2012-07-06
> **aromo said:**
> This wouldn't do what the OP intends.  This would sort the CONTENTS of #name of the file# and save the sorted contents in #name of the file you want to output#

diesch's answer is the right one.

That's right, since I thought he would like to sort Content by name into one directory.

I am glad you solved your problem wheel_walker

---

