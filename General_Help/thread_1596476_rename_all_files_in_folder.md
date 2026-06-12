---
title: "rename all files in folder"
date: 2010-10-14
forum: General Help
---

### Post by SadnesS on 2010-10-14
Hello

I have this script: 
> 
for f in d*; do mv "$f" "T${f#d}"; done

it outputs all files which strats with letter d to T but it doesn't work when i run it from Cron. It only affect root file / .

How i can make work like this:
/home/user/files/dfile.txt 
=>
/home/user/files/Tfile.txt

---

### Post by sanderd17 on 2010-10-14
add a 
```

cd /home/user/files/

```

to it?

---

### Post by SadnesS on 2010-10-14
> **sanderd17 said:**
> add a 
```

cd /home/user/files/

```

to it?

Sorry, i forget give this information:
Script works IF i run it from /home/user/files folder but when i run it from Cron it don't work.

---

