---
title: "Convert recursevely directories from eps to pdf"
date: 2011-04-10
forum: General Help
---

### Post by adpb001 on 2011-04-10
Hi there,

I would like to convert all my eps files recursively in a directory tree to pdf. 
I am currently using the following script to convert all files of a single directory:

for i in *.eps; 
   do epstopdf "$i"; 
done

I need to convert the whole directory tree, but the script above didn't work with the
-R option.

Thanks.:confused:

---

### Post by papibe on 2011-04-10
The command 'find' can do the recursive work for you, and you just need to specify what to execute when. I think something like this would work:
```
$ find -iname '*.eps' -exec epstopdf {} + ;
```
Good Luck!

---

