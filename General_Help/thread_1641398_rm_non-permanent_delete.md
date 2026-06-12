---
title: "rm non-permanent delete"
date: 2010-12-09
forum: General Help
---

### Post by COKEDUDE on 2010-12-09
I read this article as a way to do a non-permanent of something. 

I saw 2 problems. The first that my **rm** is located at **/bin/rm**. I would assume I would change the location to **/bin/rm**. The second my rm is a executable file and not a text file. So will replacing my rm file with the shellscript below work? I would think they would need to be the same type of files. 

> As far as how to make stuff go to the trash instead of deleted, run this as root:
```
mv /usr/bin/rm /usr/bin/rm.bak
```
> 
Now copy this script and save it as /usr/bin/rm:

```
#!/bin/bash

mkdir ~/.Trash &> /dev/null

while [ ! -z "$1" ]; do
    mv "$1" ~/.Trash/
    shift
done
```

> This will, instead of deleting files, move them to the .Trash directory in your home directory, and you can delete them for real later. 

[http://www.linuxforums.org/forum/364949-post2.html](http://www.linuxforums.org/forum/364949-post2.html)

---

### Post by zvacet on 2010-12-09
As far I can say you will rename rm to rm.bak with first command.That will be reason why rm probably wont work any more.Then comes script witch will do that job for you.

---

