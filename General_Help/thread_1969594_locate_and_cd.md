---
title: "locate and cd"
date: 2012-04-30
forum: General Help
---

### Post by aberetta145 on 2012-04-30
Hello,
I'm trying to use locate and cd in a pipe.
I tried this: 
locate "directory name"|"some grep commands to have only one result"|cd 
but it didn't work. 
thank you

---

### Post by codemaniac on 2012-04-30
Try find instead of locate , it gives you more grip on the search .
something like below ?
```
cd `find . -name "directory_name" -type d -print | head -1`
```

---

### Post by aberetta145 on 2012-04-30
suppose I want to go to /opt/Adobe/Help/it_IT/ instead of 
ale@ale:/$ cd /opt/Adobe/Help/it_IT/
i write
ale@ale:/$ cd 'find . -name it_IT -type -d -print | head -1'
bash: cd: find . -name it_IT -type -d -print | head -1: File o directory non esistente (not exist)

---

### Post by codemaniac on 2012-04-30
> **aberetta145 said:**
> suppose I want to go to /opt/Adobe/Help/it_IT/ instead of 
ale@ale:/$ cd /opt/Adobe/Help/it_IT/
i write
ale@ale:/$ cd 'find . -name it_IT -type -d -print | head -1'
bash: cd: find . -name it_IT -type -d -print | head -1: File o directory non esistente (not exist)

Please specify to find in which path you want to search for your directory .
use back quotes(``) for command substitution not single quotes .
single quotes around find command line treats it an argument to cd .Try exactly the below .
 
```
cd `find /opt -name "it_IT" -type -d -print | head -1`
```

---

### Post by aberetta145 on 2012-04-30
ok thank you!

---

