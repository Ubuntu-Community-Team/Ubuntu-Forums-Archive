---
title: "How do I convert a text file into smaller files?"
date: 2010-12-03
forum: General Help
---

### Post by sanderella on 2010-12-03
I have a gedit text file 2.2MB. I want to convert it into two or three smaller files/volumes, so I can upload them seperately to web pages. Does anyone know a quick and easy way to do this?
(Please don't suggest select>cut>paste, it's too laborious.)

Thanks.

---

### Post by sisco311 on 2010-12-03
```
split -b 820K file sfile_
```

See:
```
man split
```

---

### Post by AlphaLexman on 2010-12-03
Sisco311 ALWAYS gives fantastic advice, so I'm not trying to diss him at all...

but, the command: 'head --lines=1000' or the command: 'tail --lines=1000' would give you more control on where to break the text file.

Change the number of lines (1000) to meet your needs.

---

### Post by sisco311 on 2010-12-03
> **AlphaLexman said:**
> but, the command: 'head --lines=1000' or the command: 'tail --lines=1000' would give you more control on where to break the text file.


Good point.

> **AlphaLexman said:**
> 
Change the number of lines (1000) to meet your needs.

One could use **grep -n** to find the line number:
```
grep -n -e "pattern" file
```

---

### Post by sanderella on 2010-12-06
Thanks guys.:p

---

