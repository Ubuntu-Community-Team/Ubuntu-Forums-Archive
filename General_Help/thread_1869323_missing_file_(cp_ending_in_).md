---
title: "missing file (cp ending in *)"
date: 2011-10-25
forum: General Help
---

### Post by The Cheat on 2011-10-25
Ok so i made a stupid error...

i was trying to move a file from my computer onto my phone and accidentally ended the copy command with a * (eg cp file.iso /media/BLACKBERRY1/*) so now the file is no where to be found on the phone but the 1gb of space is used and is now filled up somewhere with apparently no way to delete it. 

please help, i cant seem figure this one out, or google it away. 

much appreciated.

---

### Post by Lars Noodén on 2011-10-25
A backslash is needed.  And to make the program a little safer, we'll use -i
```

rm -i \*

```

Be careful

---

### Post by The Cheat on 2011-10-25
perfect thank you very much.

---

