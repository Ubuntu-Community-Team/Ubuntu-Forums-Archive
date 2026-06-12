---
title: "CLI Batch Rename"
date: 2010-03-13
forum: General Help
---

### Post by toaksie on 2010-03-13
I have been researching batch renaming and found some useful stuff on it, with regards to using the command line but have struggled to find an answer to this question.  Say for example I have

abcdef.avi
ghijkl.avi
mnopqr.avi

and I want to batch rename them to 

1.avi
2.avi
3.avi

is there an efficient means of doing this via the command line.  Thanks for any help,

Tom

---

### Post by toaksie on 2010-03-13
bump...anyone?

---

### Post by slakkie on 2010-03-13
```

O_IFS=IFS
# quote, press enter, quote
IFS="<enter>"

j=1
for i in *.avi ; do
    echo mv "$i" $j.avi
    j=$((j+1))
done
unset j i

IFS=$O_IFS

```

There is also the [rename](http://linux.die.net/man/1/rename) command.

---

### Post by Rocket2DMn on 2010-03-13
Please wait 24 hours before bumping your thread in order to give the community a chance to get back to you.

You could write a bash script to get all files in a directory, filter by those ending in .avi, then renaming them using a counter.  I don't do much scripting these days, but it would only need to be a relatively simple script involving the commands ls, grep, and mv.  You need a variable for a counter and possibly a list to store the files in.

EDIT: There you go, slakkie has something for you :)

---

### Post by falconindy on 2010-03-13
The IFS redefinition is unnecessary. Bash's globbing will handle white space and special characters cleanly. Bash also allows the unary pre/post-increment operator.

```
#!/bin/bash
unset j
for i in *.avi; do
  mv "$i" $((++j)).avi
done
```

---

### Post by toaksie on 2010-03-13
> **Rocket2DMn said:**
> Please wait 24 hours before bumping your thread in order to give the community a chance to get back to you.

You could write a bash script to get all files in a directory, filter by those ending in .avi, then renaming them using a counter.  I don't do much scripting these days, but it would only need to be a relatively simple script involving the commands ls, grep, and mv.  You need a variable for a counter and possibly a list to store the files in.

EDIT: There you go, slakkie has something for you :)

Apologies, I'm new to the community and don't want to get off on the wrong foot, have made a mental note to self to be more patient, my only excuse being when you first start to use Ubuntu it's like the best christmas present you ever had and I just didn't expect that at my age.  Thanks to all of you fine chaps for your excellent work and once again sorry for the impatience.  
Hopefully that'll get me out of too much trouble,

Tom

---

### Post by slakkie on 2010-03-14
> **falconindy said:**
> The IFS redefinition is unnecessary. Bash's globbing will handle white space and special characters cleanly. Bash also allows the unary pre/post-increment operator.

```
#!/bin/bash
unset j
for i in *.avi; do
  mv "$i" $((++j)).avi
done
```

Could be, but I tend to avoid bashisms, since I would like to be able to use scripts not only in bash, but also sh, ksh, zsh and others.

---

