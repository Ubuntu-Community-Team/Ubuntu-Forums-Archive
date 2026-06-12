---
title: "Unrar files"
date: 2010-02-08
forum: General Help
---

### Post by CatchItBaby on 2010-02-08
Hi Everyone,
The following is the script which unrar the files :

Quote:
```
for x in *.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar x "../$x" && cd ..; done
```
If I am using the sript its extracting the same files into different folders. Also here is a screenshot :-

[IMG]http://i47.tinypic.com/qov9ud.jpg[/IMG]

But I want A Script That Will Give Me An Output Like The Following Screenshot.

[IMG]http://i48.tinypic.com/2ag9mc6.jpg[/IMG]


I'm a new user in Ubuntu 9.04 & need a bash script which would delete all the rar files after extraction.

Thanks. TC. Peace Out.

---

### Post by darolu on 2010-02-08
It is far easier to right click the first part of the rar files and click "extract here" from the contextual menu.

Seems like this part of your script "for x in *.rar; do mkdir "${x%.rar}" is what causes the multiple directories.

---

### Post by CatchItBaby on 2010-02-08
I hv Bulk of .rar files and i want that script will do this thing can any one edit this code ? or suggest me any alternative solution to accomplish this goal

thanks

---

### Post by psavva on 2010-02-08
> **CatchItBaby said:**
> Hi Everyone,
The following is the script which unrar the files :

Quote:
```
for x in *.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar x "../$x" && cd ..; done
```
If I am using the sript its extracting the same files into different folders. Also here is a screenshot :-

[IMG]http://i47.tinypic.com/qov9ud.jpg[/IMG]

But I want A Script That Will Give Me An Output Like The Following Screenshot.

[IMG]http://i48.tinypic.com/2ag9mc6.jpg[/IMG]


I'm a new user in Ubuntu 9.04 & need a bash script which would delete all the rar files after extraction.

Thanks. TC. Peace Out.

Try only to unrar Part1

```
for x in *part1.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar x "../$x" && cd ..; done
```

---

### Post by CatchItBaby on 2010-02-08
Agree but it will still create folder name with part1...

and one more modification i want that if any file sucessfully unrar it will delete rar file too

---

