---
title: "Way to Compare Folder Sizes by Bytes?"
date: 2010-12-05
forum: General Help
---

### Post by zeldarocks on 2010-12-05
As a recent migrant to Ubuntu from Windows, I was expecting to be able to compare the sizes of two folders or set of folders by Bytes (as in windows). I'm slightly OCD when it comes to my personal files and folders, and I like to maintain identical backups in various pen-drives; as such, I was hoping to be able to track the file sizes of each folder set, but I can only do so in Kilobytes... Is there any application or other means by which to compare sizes in bytes --as is the case in windows?...

---

### Post by Boondoklife on 2010-12-05
you could try diff
```

diff -r -N folder1/ folder2/

```

---

