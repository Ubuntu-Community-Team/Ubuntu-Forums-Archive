---
title: "Help on regular expression with sed"
date: 2009-08-12
forum: General Help
---

### Post by oremusnix on 2009-08-12
Hi

I am having trouble reformating a text file. The file is full of lines like this :
```
entry_title	login	password	notes	/group	random_text	other_random_text
```
Where each bit of text is separated from the other by tabs.
I need to rearrange this like that:
```
group	entry_title	login	password
```
I could not find any gui tool capable of doing this, so I went back to the command line but I am a complete beginner with regular expression.
Can anyone help?

Thank you in advance!

---

### Post by sisco311 on 2009-08-12
try:
```
awk '{print $5"\t"$1"\t"$2"\t"$3}' path/to/file
```

---

### Post by oremusnix on 2009-08-12
> **sisco311 said:**
> try:
```
awk '{print $5"\t"$1"\t"$2"\t"$3}' path/to/file
```

Hi!

Thank you, it works! There is just the "/" still in the name of the group ("/group" instead of "group") but I can manage that.

Thank you very much!

---

