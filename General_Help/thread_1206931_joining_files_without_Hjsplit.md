---
title: "joining files without Hjsplit?"
date: 2009-07-07
forum: General Help
---

### Post by Helios1276 on 2009-07-07
Hey folks,

I'm trying to join some .avi files from a holiday video that a friend sent me. As far as I know, I do not need Hjsplit to do it and can simply use 'cat'? Could anyone give me an example of this, I think my syntax is all wrong?? The files look like holiday.avi.001 etc 

Cheers:popcorn:

---

### Post by michy99 on 2009-07-07
In the terminal, go to the directory where the split file is. Enter```
cat holiday.avi.* > holiday.avi
```

---

### Post by Helios1276 on 2009-07-07
> **michy99 said:**
> In the terminal, go to the directory where the split file is. Enter```
cat holiday.avi.* > holiday.avi
```

Hey, could you give an example using say 3/4 files, I have seen the command written like that before but I am having a little trouble adapting it to my needs.

---

### Post by sshannin on 2009-07-07
```
cat holiday.avi.001 holiday.avi.002 holiday.avi.003 > holiday.avi
```

---

### Post by michy99 on 2009-07-07
If I wanted to put four files together, I could say```
cat fileA fileB fileC fileD
```but that would output to the terminal. I want the output to go to a file, so I say```
cat fileA fileB fileC fileD > bigfile
```which outputs it to bigfile instead of the terminal.

Now if the files are named file.001, file.002, etc, I can save some typing and just say```
cat file.* > bigfile
```

---

### Post by Helios1276 on 2009-07-07
The joined file does not appear in its parent folder outside of a search using the terminal and when I play it in VLC it still does not seem to pass the first part ( continue into the others parts I am supposed to have joined to it). Oh well, I'll keep trying

---

### Post by mwolfer1 on 2009-07-07
Here is a little shell script:

#!/bin/sh

# catavi - Script to concatenate multiple AVI files.
# by Adam Pierce [http://www.doctort.org/adam](http://www.doctort.org/adam)
#
# Note: The AVI files must be of the same format (eg. same codec, frame size etc).
#
# This script is freeware. You can use it, copy it, change it, whatever.

TEMPFILE=/tmp/avitmp_$$

cat "$@" > $TEMPFILE

nice mencoder -forceidx -oac copy -ovc copy $TEMPFILE -o joined_$$.avi

rm $TEMPFILE

---

### Post by Francewhoa on 2009-09-06
HJsplit for Ubuntu [http://ubuntuforums.org/showthread.php?p=7909007#post7909007](http://ubuntuforums.org/showthread.php?p=7909007#post7909007)
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

---

