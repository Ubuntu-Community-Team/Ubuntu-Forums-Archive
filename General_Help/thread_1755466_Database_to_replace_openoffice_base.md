---
title: "Database to replace openoffice base?"
date: 2011-05-11
forum: General Help
---

### Post by Karen Forrest on 2011-05-11
I am currently learning an African language. As I have been learning it, I have put together a dictionary, which I made as an openoffice database, so I could search and edit as necessary. Unfortunately, it now has several thousand entries and grinds to a complete halt if I try and search it. For now I have exported the data into a pdf which means I can look words up, but it doesn't help me make changes. Any suggestions for an alternative programme which would cope better with this much data and be easy to set up? Ideally one I can export my current data into. Thanks for your help, Karen

---

### Post by SeijiSensei on 2011-05-11
If the database isn't very large, you could consider copying it to the "shared memory" device, /dev/shm, which would keep the entire database in memory.  On my machine /dev/shm is 2 GB in size, which should be plenty to store a database with a few thousand words.  

You'll have to remember to copy the database back from /dev/shm before shutting down to save any changes.  Perhaps the easiest solution is to wrap OO Base in a simple script like this:

```

#!/bin/sh

DICTNAME=filename.of.dictionary.file
DICTPATH=/path/to/dictionary/

cp "$DICTPATH$DICTNAME" /dev/shm

[command to run OOBase with dictionary on /dev/shm]

cp /dev/shm/$DICTNAME $DICTPATH

exit 0

```

If it's just a few thousand words, a spreadsheet might be a simpler and faster solution.

---

