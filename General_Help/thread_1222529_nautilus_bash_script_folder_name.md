---
title: "nautilus bash script folder name"
date: 2009-07-25
forum: General Help
---

### Post by bunorama on 2009-07-25
How do I return the current folder from NAUTILUS_SCRIPT_SELECTED_FILE_PATHS?

path=abc/def/ghi/jkl.txt

echo ${path##*/}  returns jkl.txt

How can i get it to return just ghi?

---

### Post by kaibob on 2009-07-25
> **bunorama said:**
> How do I return the current folder from NAUTILUS_SCRIPT_SELECTED_FILE_PATHS?

path=abc/def/ghi/jkl.txt

echo ${path##*/}  returns jkl.txt

How can i get it to return just ghi?
It's not pretty but it works:

```
path=abc/def/ghi/jkl.txt ; echo $path | rev | cut -d "/" -f 2 | rev
```

You could also use pwd, which returns the path to the selected file. To see this:

```
path=$(pwd)

echo ${path##*/} > ck
```

---

### Post by bunorama on 2009-07-25
Thanks that works

---

### Post by kaibob on 2009-07-25
Another one that works:

```
#!/bin/bash

path="${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS%/*}"

folder="${path##*/}"
```

---

### Post by bunorama on 2009-07-25
Here's a quick list of them if anyone finds this post in searches.
The / can be replaced with , or any other character or multiple characters, whatever the string is delimited with.

```

test=abc/def/ghi
echo ${test%/*}         # abc/def
echo ${test##*/}        # ghi
echo ${test#*/}         # def/ghi
echo ${test%%/*}        # abc

```Now I'm trying to get CD1 to be cd1 for comparison, this doesn't work...
```

sourcefolder="${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS%/*}"
lowersource=$sourcefolder | tr '[:lower:]'      #does not work
if [ "$lowersource"="cd1" ]; then 
    gdialog --msgbox "lowersource = $lowersource" 300 300
if

```

---

### Post by bunorama on 2009-07-25
I got it...

lowersource=`echo $sourcefolder | tr A-Z a-z`

```

sourcefolder="${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS%/*}"
[COLOR=Blue]lowersource=`echo $sourcefolder | tr A-Z a-z`       #works[/COLOR]
if [ "$lowersource"="cd1" ]; then 
    gdialog --msgbox "lowersource = $lowersource" 300 300
if

```

---

