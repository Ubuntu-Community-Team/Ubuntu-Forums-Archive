---
title: "Scripting in bash..."
date: 2010-08-05
forum: General Help
---

### Post by aidenscool09 on 2010-08-05
I'm not sure weather it's possible or not, but would it be possible to make a script that goes the the directory typed into the terminal, as I'm making a script that is newbie-friendly for compiling software. Anyway, would it be possible to make the script unzip the package typed into the terminal when prompted, and if so, how. Thanks in advance.


EDIT: Also, if the user says they've already extracted the archive, but haven't compiled, could it ask the user the location of the unpacked archive.

---

### Post by anglican on 2010-08-06
> **aidenscool09 said:**
> I'm not sure weather it's possible or not, but would it be possible to make a script that goes the the directory typed into the terminal, as I'm making a script that is newbie-friendly for compiling software. Anyway, would it be possible to make the script unzip the package typed into the terminal when prompted, and if so, how. Thanks in advance.


EDIT: Also, if the user says they've already extracted the archive, but haven't compiled, could it ask the user the location of the unpacked archive.Is this the sort of thing you mean?```
#!/bin/bash

# Ask for destination directory and go there
echo
echo -n "Destination directory?: "
read DESTINATION
cd $DESTINATION
echo You are now in:
pwd
```H

---

### Post by aidenscool09 on 2010-08-10
Yeah, thanks so much.

---

