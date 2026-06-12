---
title: "Copying Windows files by extension..."
date: 2010-03-08
forum: General Help
---

### Post by jblaven on 2010-03-08
Hey guys,

I thought I posted this already, guess not!

I want to search a Windows partition for all .doc and .xls files and move them over to Xubuntu to burn them to CD.

Is this easiest to do via terminal?  I tried to use catfish and select all files, but I think my Mac keyboard (and USA standard keyboard settings) threw the select all files ability.

Any ideas?

Thanks,

Joe

---

### Post by pbrane on 2010-03-08
This is something like what you want:
```

#!/bin/bash

files=$(find . -name "*.doc")
cp $files path/to/your/directory

exit

```

Just change the **.doc* to **.xls* for the xls files.
You can also change the . (dot) after the *find* command to the path you want to search.

---

### Post by blueridgedog on 2010-03-08
Use find, then execute a copy.  Replace as indicated:

```
find /path/to/windows/files/ -name *.xls -exec cp {} /path/to/where/you/want/them \;
```

Change /path/to/windows/files/ to the mount point of your windows disk and /path/to/where/you/want/them to be the location you want to copy the files to.

You can test this fist by using ls:

```
find /path/to/windows/files/ -name *.xls -exec ls {} \;
```

This will list the files that would be copied in the above step.

Repeat with *.doc

Note that this is case sensitive.

---

### Post by pbrane on 2010-03-09
Perhaps another way to copy those files would be to use rsync:
```

rsync -avlt --stats /path/to/windows/*.doc /home/user/directory
rsync -avlt --stats /path/to/windows/*.xls /home/user/directory

```

replace */path/to/windows* with the actual path to your windows drive and */home/user/direstory* with the path you want to copy to.

---

### Post by jblaven on 2010-03-09
Wow,

Thanks guys.  All good choices!:p

---

