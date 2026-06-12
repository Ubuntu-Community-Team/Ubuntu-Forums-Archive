---
title: "How do I use &quot;for ... next&quot; in a script?"
date: 2010-08-08
forum: General Help
---

### Post by Coco999 on 2010-08-08
Assume I want to repeat 100 times the same operation. This could be expressed by this example:
```
for i=001 to 100
convert i.png i.jpg
next i
```
But this fails. What must I do?

---

### Post by chopinhauer on 2010-08-09
> **Coco999 said:**
> But this fails. What must I do?

Read the [bash manpage]("http://manpages.ubuntu.com/manpages/lucid/en/man1/bash.1.html#toptoc9") for the details. You can surely use
```

for i in {001..100}; do
   convert $i.png $i.jpg
done

```but usually one doesn't rely on the file names having a common pattern and write:
```

for i in *.jpg; do
  convert "$i" "${i%jpg}png"
done

```
to convert all files in the directory.

---

### Post by Coco999 on 2010-08-10
Thank you, chopinhauer, for your help, that solves nicely my problem.

---

