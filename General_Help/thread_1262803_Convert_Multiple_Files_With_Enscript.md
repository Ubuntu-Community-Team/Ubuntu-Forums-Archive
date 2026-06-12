---
title: "Convert Multiple Files With Enscript"
date: 2009-09-10
forum: General Help
---

### Post by mechdesignron on 2009-09-10
Hello,

I have a folder with over 5000 .txt files. I would like to convert them to either .rtf or html. Can someone please show me the syntax on the command line with Enscript to do this. If there is another linux program that will work thats fine.

Thank You greatly

---

### Post by DaithiF on 2009-09-10
Hi,
something like:

```

for i in *.txt
do
  enscript -w html -p ${i%.txt}.html $i
done

```

---

