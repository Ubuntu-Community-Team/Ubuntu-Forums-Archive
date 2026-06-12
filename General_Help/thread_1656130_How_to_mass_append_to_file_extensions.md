---
title: "How to mass append to file extensions"
date: 2010-12-30
forum: General Help
---

### Post by knottshawk on 2010-12-30
Maybe I don't know what to search for, but I can't find this anywhere.

I need to take all the files in a given directory and append an underscore to their file extension. I'd love to put it in a shell script... the various renaming options I've tried have failed. So... I'm up for suggestions.

Lets say that the files are all in a folder on my desktop named 'extensions'

---

### Post by matt_symes on 2010-12-30
Hi

What about something simple like...

```

#!/bin/bash
for file in ~/Desktop/extensions/*
do
mv "$file" "$file"_
done
```

EDIT: Hold on. Has problems with spaces.

EDIT2: tredegar provided the correct solution for this, but i will amend my misplaced ".

Kind regards

---

### Post by knottshawk on 2010-12-30
I got this when I tried it:

mv: missing destination file operand after `_'

EDIT:

Got it with this:

#!/bin/bash

for f in *; 
do 
mv $f `basename $f `_; 
done;

---

### Post by vanadium on 2010-12-30
change 
```

mv $file $file"_"

```
to
```

mv $file "$file_"

```

but I have an easier one:

```

rename 's/$/\_/' *

```
Before you do this, do a "dry run" to see what will come out using the -n option:
```

rename -n 's/$/\_/' *

```

---

### Post by tredegar on 2010-12-30
**for file in *; do mv "$file" "$file"_; done**

Works with **filenames-with spaces**, but _won't_ work if *many* filenames: You need to use **find** if there are many files to be renamed.

---

### Post by knottshawk on 2010-12-30
Thanks folks... several good solutions there. Much appreciated.

---

