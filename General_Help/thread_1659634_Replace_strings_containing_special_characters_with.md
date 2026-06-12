---
title: "Replace strings containing special characters with sed"
date: 2011-01-04
forum: General Help
---

### Post by fluXXXion on 2011-01-04
Hi,
here's my newbie question - I want to change the following string in text files

```
E:\MP3\
```

with the following string using sed:

```
smb://N3200Pro/Music/MP3/
```

Under Windows OS I would put every regular expression in "
But how do I get this to work under Linux?

This command does not work of course:

```
sed -e 's/E:\MP3/smb://N3200Pro/Music/MP3//g' text1.txt > text2.txt
```

results in

> sed: -e expression #1, char 15: unknown option to `s'```

```

---

### Post by sisco311 on 2011-01-04
You have to escape the slashes and backslashes in the regexp and replacement:
```
sed -e 's/E:\\MP3\\/smb:\/\/N3200Pro\/Music\/MP3\//g' file
```

If you use a different separator (for example _), you don't have to escape the slashes: 
```
sed -e 's_E:\\MP3\\_smb://N3200Pro/Music/MP3/_g' file
```

---

### Post by fluXXXion on 2011-01-04
Great.

My script looks like this now:

```

#!/bin/bash
  sed -e 's_E:\\MP3\\_smb://N3200Pro/Music/MP3/_g' "Dub Techno.m3u" > "Dub Techno XBMC_temp.m3u"
  sed -e 's_\\_/_g' "Dub Techno XBMC_temp.m3u" > "Dub Techno XBMC.m3u"
  rm "Dub Techno XBMC_temp.m3u"

```

Works perfectly - thank you very much!

---

### Post by sisco311 on 2011-01-04
You're welcome!


Don't forget to mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

