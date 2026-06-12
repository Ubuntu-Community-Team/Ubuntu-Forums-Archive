---
title: "Make a script"
date: 2011-01-31
forum: General Help
---

### Post by edvac on 2011-01-31
Hello,

 I have a problem when performing a script, this script has to be used to find several files and delete them.

 find filename

 This gives me a series of files that need to be clear, my problem is this. How do I can delete?

 I think it could be:

 rm find filename 

 But he would not know how to do it ...

 I also want information from that file would go to one. txt to review ... but this is not essential.

 Thanks for your help in advance.

 Regards,

 EDVAC

---

### Post by nothingspecial on 2011-01-31
Hi,

You need find with the -exec option.

Type man find

---

### Post by McNils on 2011-01-31
Here you go, some simple ways to delete the files you are looking for.
```
find -name filename -delete
find -name filename -print0 | xargs -0 rm 
```

you can also use
```
rm $(find filename)
```
but that is useless if you have spaces and other special characters it the file name.

To save filenames into a file do:
```
find -name filename > log.txt
```
or if you just want to look at it 
```
find -name filename | less
```

Hopes this helps you :)

---

