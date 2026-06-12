---
title: "Specifying Download Location"
date: 2011-01-03
forum: General Help
---

### Post by Sanchenzo on 2011-01-03
When I use wget, for a file online, it always downloads the file to my home folder.

Is there a way to specify where to download it to?

---

### Post by TeoBigusGeekus on 2011-01-03
```
wget -O /path/to/folder/nameoffile www.address.com/file
```

---

### Post by Sanchenzo on 2011-01-03
Thank You

---

### Post by matt_symes on 2011-01-03
Hi  

Try wget with the --directory-prefix=prefix switch as well

```
man wget
```

and look for section Directory Options. This will use a base directory for multiple downloads

Kind regards

---

### Post by anystupidname1 on 2011-01-03
```
man wget
```

It doesn't download to ~home no matter what, it downloads to the path you executed wget from. So you may prefer to just cd /path/ first and then run the wget command (less typing).

---

### Post by Sanchenzo on 2011-01-03
> **anystupidname1 said:**
> ```
man wget
```

It doesn't download to ~home no matter what, it downloads to the path you executed wget from. So you may prefer to just cd /path/ first and then run the wget command (less typing).

Thank You for that information!

---

