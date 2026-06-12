---
title: "Shell Script Help"
date: 2010-08-11
forum: General Help
---

### Post by yma981 on 2010-08-11
Why this isn't working any ideas?  

#!/bin/bash 
# This script will take a user input, the extension, and remove it from the files with this specific extension 

echo "What extension would u like to remove from files names?"
read extension  

rename '.$extension' '' *.$extension  

echo "Extension Removed"

---

### Post by surfer on 2010-08-11
this works for me:

```

#!/bin/bash
# This script will take a user input, the extension, and remove it from the files with this specific extension

echo "What extension would u like to remove from files names?"
read extension

/usr/bin/rename "s/\.${extension}\$//" *.${extension}

echo "Extension Removed"

```

---

### Post by yma981 on 2010-08-11
> **surfer said:**
> this works for me:

```

#!/bin/bash
# This script will take a user input, the extension, and remove it from the files with this specific extension

echo "What extension would u like to remove from files names?"
read extension

/usr/bin/rename "s/\.${extension}\$//" *.${extension}

echo "Extension Removed"

```

It still didn't work

---

### Post by surfer on 2010-08-11
could you post the listing of your working directory, the extension you typed and the error message you got?

---

### Post by yma981 on 2010-08-11
> **surfer said:**
> could you post the listing of your working directory, the extension you typed and the error message you got?

```

[~/YMA]# ./ren.sh
What extension would u like to remove from files names?
jpeg
Extension Removed
[~/YMA]# 

```

---

### Post by surfer on 2010-08-11
> **surfer said:**
> could you post the **listing of your working directory**, the extension you typed and the error message you got?

could you post (some of) the filenames before (and after) you run the script?

---

