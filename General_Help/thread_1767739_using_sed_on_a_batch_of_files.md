---
title: "using sed on a batch of files"
date: 2011-05-26
forum: General Help
---

### Post by engine on 2011-05-26
Continuing to extend my command-line skills … fun! I have a couple of thousand files (site audit) where I need to make a consistent change; my first successful experiment is

```
sed -e 's/{{tag>/{{tag>86 /' ec00200.txt > newEC00200.txt
```

The question, then, is "how to run this change over a whole slew of files?" I can imagine that

```
sed -e 's/{{tag>/{{tag>86 /' ec00*.txt
```

might go and do things to all the files matching the pattern, but how do I define the new name to be used for each updated file? (and no, I don't want to do anything bleeding-edge like writing the new file over the original!)

Thanks in advance.

---

### Post by mbeierl on 2011-05-26
I usually use the "for" built-in of bash, like so:
```
for file in ec00*.txt ; do new_name=`echo new$file`; sed -e 's/{{tag>/{{tag>86 /' $file > $new_name ; done

```

Edit:  just noticed you wanted a change in the case of the new name.  You can sed there too:
```
for file in ec00*.txt ; do new_name=`echo $file | sed "s/ec00/newEC00/" `; sed -e 's/{{tag>/{{tag>86 /' $file > $new_name ; done

```

---

### Post by sisco311 on 2011-05-26
> **mbeierl said:**
> I usually use the "for" built-in of bash, like so:
```
for file in ec00*.txt ; do new_name=`echo new$file`; sed -e 's/{{tag>/{{tag>86 /' $file > $new_name ; done

```

Edit:  just noticed you wanted a change in the case of the new name.  You can sed there too:
```
for file in ec00*.txt ; do new_name=`echo $file | sed "s/ec00/newEC00/" `; sed -e 's/{{tag>/{{tag>86 /' $file > $new_name ; done

```
You don't need to use external applications to get the new filename, parameter expansion should do the trick:

```

for file in ec*.txt
do
  sed -e *script* "$file" > "new${file^^}"
done

```


Oh, always **put double quotes around every parameter expansion!**

See:
[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

---

### Post by engine on 2011-05-28
Thanks! I'd wondered about a "for ..." loop, but didn't know where to start.

---

### Post by sisco311 on 2011-05-28
You're welcome!

Please don't forget to mark this thread as [SOLVED]. Thanks!

---

