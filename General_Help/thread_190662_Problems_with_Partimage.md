---
title: "Problems with Partimage"
date: 2006-06-06
forum: General Help
---

### Post by Shoriminimoe on 2006-06-06
I'm trying to make an image of my current ubuntu partition so I have a backup in case something goes wrong when I install Dapper. However, whenever I begin the backup it only makes it to 4 GB and then quits and says all of the space has been used up. I'm backing it up to an external HD that I have. After checking and rechecking I still have plenty of room for the entire image. Anyone know how to fix this problem?

---

### Post by ifokkema on 2006-06-06
[QUOTE=Shoriminimoe]I'm trying to make an image of my current ubuntu partition so I have a backup in case something goes wrong when I install Dapper. However, whenever I begin the backup it only makes it to 4 GB and then quits and says all of the space has been used up. I'm backing it up to an external HD that I have. After checking and rechecking I still have plenty of room for the entire image. Anyone know how to fix this problem?[/QUOTE]

This may be a filesize limit you're reaching. What filesystem are you using on that external drive?

Ivo

---

### Post by Shoriminimoe on 2006-06-06
fat32

---

### Post by ifokkema on 2006-06-06
[QUOTE=Shoriminimoe]fat32[/QUOTE]
That's the problem. FAT32 won't support files larger than 4 GB. I would consider a different filesystem, or a different drive.

Ivo

---

### Post by Shoriminimoe on 2006-06-06
Ok thank you that helped.

---

### Post by jeremy on 2006-06-07
Or you could tell partimage to make multiple files of, say 1.5GB.

---

