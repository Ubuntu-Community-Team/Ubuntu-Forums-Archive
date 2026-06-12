---
title: "bash script to rename (renumber) files"
date: 2010-01-27
forum: General Help
---

### Post by Jamesss on 2010-01-27
I'm trying to write a script to process some images and rename them, or more specifically, renumber them so that pg_0001.png becomes pg_0.png, pg_0002.png becomes pg_1.png, etc. I've looked at the rename command and sed, but I'm not really very familiar with these. It should also be part of a bash script that I've written for the processing of these files - this is what I have so far:

```
#!/bin/bash
pdftk 2012\ theatre\ Sep\ 2009.pdf burst
mogrify -format png -resize 1200 -negate pg_00**.pdf
rm pg_00**.pdf
```

So I just need the the next line to renumber the png's - any ideas?

---

### Post by chewearn on 2010-01-27
From your description, I assumed you want to strip out the leading zeros?

Here is one way (though it's not the most elegant)
```
rename 's/pg_000/pg_/;s/pg_00/pg_/;s/pg_0/pg_/' pg_*.png
```

---

### Post by DaithiF on 2010-01-27
```
rename 's/pg_0*/pg_/'  pg_*.png
```

---

