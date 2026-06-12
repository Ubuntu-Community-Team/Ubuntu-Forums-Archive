---
title: "Help with small bash script, please"
date: 2006-05-05
forum: General Help
---

### Post by mexlinux on 2006-05-05
Hi:
I have a collection of .cmx image files in several folders I want to convert to SVG.
I have installed sketch, so I have the tool skconvert, which can do the job...
Can any one please help me on how to make a script to convert all the images??

All I need it to do is:
Move recursively inside a given folder, and execute the comand 

skconvert name.cmx name.svg

where name is the actual name of the file...

any one can help, please?

Thanks in advance

---

### Post by cgjones on 2006-05-05
This should work, but I would test it out first by making a copy of one of the directories containing these files, and running this script from within that directory. This will affect the current directory, and all sub directories. I don't know anything about skconvert, so this might not work if you need the destination filename (name.svg).
```

#!/bin/bash

find . -name *.cmx -exec skconvert {} \;

```

---

### Post by mexlinux on 2006-05-05
Just realized:
krename can do the job with the command plugin!

---

### Post by hw-tph on 2006-05-05
I have no experience with cmx images nor skconvert. However, the find command should be able to do it:
```
find . -name "*.cmx" -exec skconvert {} {}.svg \;
```
That would give you files called name.cmx.svg but technically it should work.


Håkan

*Edit:* cgjones beat me to it.

---

### Post by cgjones on 2006-05-05
[QUOTE=hw-tph]I have no experience with cmx images nor skconvert. However, the find command should be able to do it:
```
find . -name "*.cmx" -exec skconvert {} {}.svg \;
```
That would give you files called name.cmx.svg but technically it should work.


Håkan

*Edit:* cgjones beat me to it.[/QUOTE]

But I think your solution is more likely to work. I wasn't sure how to handle a second argument to -exec *command*

---

