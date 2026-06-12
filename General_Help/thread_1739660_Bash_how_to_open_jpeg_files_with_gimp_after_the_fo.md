---
title: "Bash: how to open jpeg files with gimp after the former has been closed"
date: 2011-04-26
forum: General Help
---

### Post by Ginosal on 2011-04-26
Hi everybody. I have to edit several video frames as jpg images. I can't do it through batch processes, because every frame must be edited individually. So, I've tried a bash file like this:

```
#!/bin/bash

gimp video0000.jpeg
gimp video0001.jpeg
gimp video0002.jpeg
```

But this opens the three files at once. What I need is that when I'm finished with video0000.jpeg, gimp would open video0001.jpg and so on... is there a way to do this with a bash script? I've tried to add a "read" instruction between the lines, but I have to push a key, and to go to the next line gimp must be closed. Please, can you help me? Thank you in advance!

---

### Post by DaithiF on 2011-04-26
you're on the right track with the read statement, but you just need to run gimp in the background (via a trailing '&' character) so that it doesn't block (and require you to exit gimp before moving on to the next line in the script).

something like:
```
for i in video0000.jpeg video0001.jpeg video0002.jpeg
do
   gimp "$i" &
   read -p "press any key for next file"
done
```

---

### Post by Ginosal on 2011-04-26
> **DaithiF said:**
> you're on the right track with the read statement, but you just need to run gimp in the background (via a trailing '&' character) so that it doesn't block (and require you to exit gimp before moving on to the next line in the script).

something like:
```
for i in video0000.jpeg video0001.jpeg video0002.jpeg
do
   gimp "$i" &
   read -p "press any key for next file"
done
```

Thank you! This works fine! Just a try... is there a way to make the second file open when the first is closed, without having to press a key? Thank you again!

---

### Post by DaithiF on 2011-04-26
the short answer ... no ... the closing of a file within gimp is known only to gimp, ie an external process (the script) has no knowledge of what may be happening within gimp.

the longer answer ... maybe ... by writing a python extension to gimp, but thats a non-trivial task.

---

