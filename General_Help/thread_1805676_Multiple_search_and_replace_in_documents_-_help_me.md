---
title: "Multiple search and replace in documents - help me creating a sed script"
date: 2011-07-16
forum: General Help
---

### Post by fatteralbert on 2011-07-16
I want to do search and replace in multiple files. 

I've seen that it possible to create a sed script but I haven't got the talent to do it myself. Could anyone help me with it? 

What I need is to locate all instances of a word - lets say 'day' - and replace it with for example 'night' in all odm-documents in a specific folder. It would be great if the search only matched whole words and was case sensitive. 

Cheers!

---

### Post by Habitual on 2011-07-16
cd dir
```
for i in $(ls -1 odm-documents) ; do sed -i "s/\<day\b/night/g"
```

---

