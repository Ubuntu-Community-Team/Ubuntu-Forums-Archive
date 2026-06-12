---
title: "Need help with diff command"
date: 2010-04-03
forum: General Help
---

### Post by RubenK on 2010-04-03
Dear people.

I have a large music collection that I recently back up and reorganised. However, I want to know if I got all of it backed up (so far the file count says I'm a couple hundred files off, but I also removed some double songs...). The problem is that the path of the files has changed due the reorganising. I have a feeling diff is not noticing this. Example:
When I do diff ~/Music/ /media/drive/Music/
given that /Metallica/ is not under /Music/Metallica/ as it was in ~/Music but under /media/drive/Music/M-N-O/Metallica/ . So diff tells me that the dir Metallica is only in ~/Music/ and not in /media/drive/Music/ . 

Question: how can I let diff search only for filenames, no matter what their path after the input dir is?

I hope my question is clear enough, if not, please ask me to clarify. Thanks in advance!

---

### Post by Barriehie on 2010-04-08
How about a bash script something like this:
```

#!/bin/bash
#
firstdir='some_path1'
2nddir='some_path2'
#
find $firstdir -iname * > $firstdir/filez1 && sort $firstdir/filez1 > $firstdir/filez1.s
#
find $2nddir -iname * > $2nddir/filez2 && sort $2nddir/filez2 > $2nddir/filez2.s
#
diff -i -a -y $firstdir/filez1.s $2nddir/filez2.s
#
exit 0

```

---

