---
title: "Bash Problem..."
date: 2010-06-06
forum: General Help
---

### Post by CatchItBaby on 2010-06-06
I have a command (mtn) which is used for creating screenshot from terminal and whenever i type mtn from terminal it works as shown in figure 

[http://i47.tinypic.com/okyaza.jpg]("http://i47.tinypic.com/okyaza.jpg")

but when i try to do from bash script it give error

```
#! /bin/bash

mtn
```


./test.sh: line 3: mtn: command not found

Where i m doing wrong...Plz help 

Thanks

---

### Post by apmcd47 on 2010-06-06
> **CatchItBaby said:**
> I have a command (mtn) which is used for creating screenshot from terminal and whenever i type mtn from terminal it works as shown in figure 

[http://i47.tinypic.com/okyaza.jpg]("http://i47.tinypic.com/okyaza.jpg")

but when i try to do from bash script it give error

```
#! /bin/bash

mtn
```


./test.sh: line 3: mtn: command not found

Where i m doing wrong...Plz help 

Thanks

Sounds like a path problem. What is the result of ```
type mtn
```in your bash terminal?

Andrew

---

### Post by CatchItBaby on 2010-06-06
when i type in "type mtn" in terminal i got this

mtn is aliased to `/home/username/Desktop/Tools/mtn'

---

### Post by Leppie on 2010-06-06
use the full path to the app:
```
#! /bin/bash

/home/username/Desktop/Tools/mtn

```

---

### Post by apmcd47 on 2010-06-06
> **CatchItBaby said:**
> when i type in "type mtn" in terminal i got this

mtn is aliased to `/home/username/Desktop/Tools/mtn'

mtn will not be aliased in your script. Either use Leppie's solution or create a folder /home/username/bin, ensure this folder is in your PATH (look in .bash_profile or .bashrc) in your home folder and move mtn into this folder.

The PATH definition statement will look something like this:

```
PATH=/usr/bin:/bin:/usr/local/bin
```It is basically a list of folders to find programs separated by colons.

Andrew

---

### Post by CatchItBaby on 2010-06-06
Thanks to All

Problem Solved by Above Solutions

---

