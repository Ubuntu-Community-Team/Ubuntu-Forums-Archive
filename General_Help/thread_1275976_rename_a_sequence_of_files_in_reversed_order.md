---
title: "rename a sequence of files in reversed order"
date: 2009-09-26
forum: General Help
---

### Post by mordantae on 2009-09-26
Hi, I'm trying to rename a sequence of .jpg files in reversed order.

so that for example 

01.A.jpg 
02.B.jpg
03.C.jpg
04.D.jpg

is renamed to

01.D.jpg
02.C.jpg
03.B.jpg 
04.A.jpg 

I was thinking i could write a script to this effect : 

```


#!/bin/bash

## tac [reverse cat] the ordered file list(list is the result of `ls > list` in the chosen directory):
reversedOrder=$(tac /home/tea/Desktop/working-folder/processed/list)

## Loop through files 
for name in $reversedOrder
do
        ## rename using this new reversed list.
        mv "$reversedOrder" "$name"
done

```


---

apart from the fact that i'm still very unsure of my logic there...mv is receiving the loop variable as a long stream of filenames as opposed to single filenames...


See output:


```
mv: cannot stat `+IMG_6422.jpg\n+IMG_6421.jpg\n+IMG_6420.jpg\n+IMG_6419.jpg\n+IMG_6418.jpg\n+IMG_6417.jpg\n+IMG_6416.jpg\n+IMG_6415.jpg\n+IMG_6414.jpg\n+IMG_6413.jpg\n+IMG_6412.jpg\n+IMG_6411.jpg\n+IMG_6410.jpg\n+IMG_6408.jpg\n+IMG_6407.jpg\n+IMG_6406.jpg\n+IMG_6405.jpg\n+IMG_6404.jpg\n+IMG_6403.jpg\n+IMG_6402.jpg\n+IMG_6401.jpg\n+IMG_6400.jpg\n+IMG_6399.jpg\n+IMG_6398.jpg\n+IMG_6397.jpg\n+IMG_6396.jpg\n+IMG_6395.jpg\n+IMG_6394.jpg\n+IMG_6393.jpg\n+IMG_6392.jpg\n+IMG_6391.jpg\n+IMG_6390.jpg\n+IMG_6389.jpg\n+IMG_6388.jpg\n+IMG_6387.jpg\n+IMG_6386.jpg\n+IMG_6385.jpg\n+IMG_6384.jpg\n+IMG_6383.jpg\n+IMG_6382.jpg\n+IMG_6381.jpg\n+IMG_6380.jpg\n+IMG_6379.jpg\n+IMG_6378.jpg\n+IMG_6377.jpg\n+IMG_6376.jpg\n+IMG_6375.jpg': File name too long

```



I've tried putting a comma at the end of every filename with the vim global replace : 

:%s/$/,/

but to no avail..i get the same error message.


Any ideas ??


---cheers for any help you might be able to provide!!

---

### Post by unutbu on 2009-09-26
Here is a solution in python:

[PHP]#!/usr/bin/env python
import os
filenames=os.listdir('.')
filenames.sort()
new_filenames=[]
for i,afile in enumerate(reversed(filenames)):
    j=i+1
    idx=afile.find('.')
    short=afile[idx+1:]
    new_filenames.append('%02.f.%s'%(j,short))
for old,new in zip(filenames,new_filenames):
    print '%s --> %s'%(old,new)

resp=raw_input('Rename?').lower()
if resp.startswith('y'):
    for old,new in zip(filenames,new_filenames):
        os.rename(old,new)[/PHP]
    
To use it, save it as reverse.py and make it executable, and run it like this:
```

reverse.py
```

The program will first present you with the renaming it is about to perform. Type 'y' if 
it is correct.
```

% reverse.py
01.A.jpg --> 01.D.jpg
02.B.jpg --> 02.C.jpg
03.C.jpg --> 03.B.jpg
04.D.jpg --> 04.A.jpg
Rename?y         
```

---

### Post by mordantae on 2009-09-26
First of all thanks for the speedy reply!



I ran reverse.py and it advised me of the following changes :

```


+IMG_6374.jpg --> 01.py
+IMG_6375.jpg --> 02.jpg
+IMG_6376.jpg --> 03.jpg
+IMG_6377.jpg --> 04.jpg
+IMG_6378.jpg --> 05.jpg
+IMG_6379.jpg --> 06.jpg
+IMG_6380.jpg --> 07.jpg
+IMG_6381.jpg --> 08.jpg
+IMG_6382.jpg --> 09.jpg
+IMG_6383.jpg --> 10.jpg
+IMG_6384.jpg --> 11.jpg
+IMG_6385.jpg --> 12.jpg
+IMG_6386.jpg --> 13.jpg
+IMG_6387.jpg --> 14.jpg
+IMG_6388.jpg --> 15.jpg
+IMG_6389.jpg --> 16.jpg
+IMG_6390.jpg --> 17.jpg
+IMG_6391.jpg --> 18.jpg
+IMG_6392.jpg --> 19.jpg
+IMG_6393.jpg --> 20.jpg
+IMG_6394.jpg --> 21.jpg
+IMG_6395.jpg --> 22.jpg
+IMG_6396.jpg --> 23.jpg
+IMG_6397.jpg --> 24.jpg
+IMG_6398.jpg --> 25.jpg
+IMG_6399.jpg --> 26.jpg
+IMG_6400.jpg --> 27.jpg
+IMG_6401.jpg --> 28.jpg
+IMG_6402.jpg --> 29.jpg
+IMG_6403.jpg --> 30.jpg
+IMG_6404.jpg --> 31.jpg
+IMG_6405.jpg --> 32.jpg
+IMG_6406.jpg --> 33.jpg
+IMG_6407.jpg --> 34.jpg
+IMG_6408.jpg --> 35.jpg
+IMG_6410.jpg --> 36.jpg
+IMG_6411.jpg --> 37.jpg
+IMG_6412.jpg --> 38.jpg
+IMG_6413.jpg --> 39.jpg
+IMG_6414.jpg --> 40.jpg
+IMG_6415.jpg --> 41.jpg
+IMG_6416.jpg --> 42.jpg
+IMG_6417.jpg --> 43.jpg
+IMG_6418.jpg --> 44.jpg
+IMG_6419.jpg --> 45.jpg
+IMG_6420.jpg --> 46.jpg
+IMG_6421.jpg --> 47.jpg
+IMG_6422.jpg --> 48.jpg
reverse.py --> 49.+IMG_6374.jpg


```


The intention is to rename +IMG_6422.jpg so that it is 01 and +IMG_6374 to 48. Hence reversing my list.

The script is leaving the images in their native ordering.

Also, it isn't accounting for its presence in the folder, and processes reverse.py itself along with the other files.

:)

Thanks for helping!

---

### Post by unutbu on 2009-09-26
Oh, okay. How about delete reverse.py and try
```

N=1; ls -tr -1 *.jpg | tac | while read file; do echo mv "$file" "$N".jpg; N=$((N+1)); done
```

This will echo to mv commands to the terminal.
If the proposed moves are satisfactory, just remove the "echo" from the command to really move the files.

---

### Post by mordantae on 2009-09-26
you are my hero of the day! :)


thanks. i will try to learn from the way you've reasoned this out.

:) 


Many many thanks.

---

