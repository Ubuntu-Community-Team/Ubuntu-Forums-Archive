---
title: "Nautilus script open a window?"
date: 2010-10-06
forum: General Help
---

### Post by stealth1236 on 2010-10-06
Hi I have a script that i run from the context menu in nautilus, it combines two avi's into one, right now it does not open a terminal when it runs. i am just wondering if there is some command i have to put in to get it to open the terminal and not run silently?

Thanks!


```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import os
import subprocess

files = os.listdir(".") # create list from files in current directory
files.sort() # make sure the files are sorted

n=len(files) # get length of list
print files[0]
print files[1]

os.system('mencoder -forceidx -ovc copy -oac copy -o Output.avi '+files[0] +' ' +files[1])

os.system('mv Output.avi Done.avi')
```

---

