---
title: "Shell Script"
date: 2012-05-10
forum: General Help
---

### Post by jat421 on 2012-05-10
Hi, I am new at shell scripting and need some help. I am trying to convert all the files in a folder from .tif to .pdf using tiff2pdf. But every time it converts it saves the name as file.tif.pdf. How can I get rid of .tif in between the file. Here is my script. Thanks

```

for f in *.tif; do sudo tiff2pdf -o $f.pdf $f; done


```Thanks for any help!

---

### Post by papibe on 2012-05-10
Hi jat421.

The easiest way is to use 'parameter substitution':
```
for f in *.tif; do tiff2pdf -o "${f%.tif}".pdf "$f"; done
```
Where ${f%.tif} means: "take f and trim the shortest appearance of '.tif' from the end.

Don't forget to quote your variables ;)

Hope it helps.
Regards.

BTW, I took again the sudo part. I don't think you need it.

---

### Post by jat421 on 2012-05-11
Thanks works great!!!. I did have to put sudo as it gave me errors when writing .pdf file. Do you know of a way around that? Thanks!

---

### Post by kuifje09 on 2012-05-11
If you needed sudo then the files are not yours, better take care of that first.
Its not a good idea to do a lot of user tasks by using the root account.

---

### Post by jat421 on 2012-05-11
Hi, thanks for helping. What do you mean when you say the files are not yours?

The files are on a Windows network Drive. I have mapped to it using admin credentials and when I check the permission on the files they seems to have 755 access.

Thanks for your help!

---

### Post by kuifje09 on 2012-05-15
If the owner of the file(s) is not you, you cannot do much ( usually ) with the files.
Then you need root other the other account to do some things...

You can see the owner by   :   ls -l  <file(s)>
Change the owner with :  chown <user>:<group> <file(s)>
 Group only if needed of course.

But it can also be the problem the directory you are working in, cannot be written by you ...


( But maybe you could show some of the errors you got. could be something else too... )

Did this help ?

---

