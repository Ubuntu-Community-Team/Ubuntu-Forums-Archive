---
title: "print zip file contents"
date: 2012-03-27
forum: General Help
---

### Post by winzip on 2012-03-27
I have a zip file...abc.zip

It has  folder structure  abc.zip/com/lib

I want to  print  files under lib directory .

Whats the command ?

---

### Post by raja.genupula on 2012-03-27
```
unzip file_name.zip
```
then 
use this link 
[http://blog.nguyenvq.com/2011/04/13/lpr-printing-on-command-line/](http://blog.nguyenvq.com/2011/04/13/lpr-printing-on-command-line/)

---

### Post by codemaniac on 2012-03-27
use unzip with -l switch to peek into the contents of a zipped file .
```
unzip -l test.zip
```

---

### Post by Mark Phelps on 2012-03-27
> **winzip said:**
>  .. I want to  print  files under lib directory...

Print the CONTENTS of the files? OR print the NAMES of the files?

The answers for both have already been given:
1) Contents: Have to unzip the archive
2) Names: Use the unzip command as indicated in post #3.

---

### Post by winzip on 2012-03-29
> **codemaniac said:**
> use unzip with -l switch to peek into the contents of a zipped file .
```
unzip -l test.zip
```

I want to  print  _files **under **lib directory_ .

---

### Post by raja.genupula on 2012-03-29
post #2 , look at the link .

---

### Post by winzip on 2012-03-30
> **raja.genupula said:**
> post #2 , look at the link .

No...you misunderstood my post.

suppose  in  location  **abc.zip/com/lib **  has  3 files  say **abc.jar**  , **def.jar **. **ijk.jar**

and I  want to  print  file NAMES under lib directory ONLY. ....not the entire  zip archive.

So looking for a command something like this ..

unzip  -l  abc.zip/com/lib

**expected **prints ..
[I]abc.jar
def.jar
ijk.jar[/I]

What would be the correct command ?

---

### Post by raja.genupula on 2012-03-30
ok look this 

```
raja@raja-Ubuntu:~$ unzip zip.zip >l.txt
raja@raja-Ubuntu:~$ cat l.txt
Archive:  zip.zip
   creating: zip/
 extracting: zip/1                   
 extracting: zip/2                   
 extracting: zip/3                   
raja@raja-Ubuntu:~$ 
```

so here the contents names are stored in l.txt filename . so if you print that l.txt file it will gives you what you want . 

hope that helps .

---

### Post by winzip on 2012-03-31
> **raja.genupula said:**
> ok look this 

```
raja@raja-Ubuntu:~$ unzip zip.zip >l.txt
raja@raja-Ubuntu:~$ cat l.txt
Archive:  zip.zip
   creating: zip/
 extracting: zip/1                   
 extracting: zip/2                   
 extracting: zip/3                   
raja@raja-Ubuntu:~$ 
```so here the contents names are stored in l.txt filename . so if you print that l.txt file it will gives you what you want . 

hope that helps .

No. that will be complicated. This is just an example.  What if I have multiple  sub folders ? then your approach will create .txt file  crowded with  all unnecessary file names  coming out from other sub folders....then I need to search through again to get the relevant file names.

This would be inconvenient.

All I need is a command which can print files names for a specific folder only. 

I want to say to unzip  these words ...  " hey  unzip  can you please print files names under lib directory only.....skip everything else" ?


Is it  available ?

---

### Post by Vaphell on 2012-03-31
```

unzip -l archive.zip | grep 'some/dir/'
unzip -l archive.zip | awk '/[0-9][0-9]:[0-9][0-9]/{ print }' | cut -b 31- | grep 'some/dir/'
```

unzip -l prints file names with paths and you can pipe it to grep to look for directory name or whatever. these awk | cut parts, while not necessary, remove general archive info, filesizes and timestamps from unzip -l output, leaving only file paths for further use.

---

### Post by winzip on 2012-04-02
> **Vaphell said:**
> ```

unzip -l archive.zip | grep 'some/dir/'
unzip -l archive.zip | awk '/[0-9][0-9]:[0-9][0-9]/{ print }' | cut -b 31- | grep 'some/dir/'
```

unzip -l prints file names with paths and you can pipe it to grep to look for directory name or whatever. these awk | cut parts, while not necessary, remove general archive info, filesizes and timestamps from unzip -l output, leaving only file paths for further use.


unzip -l archive.zip | grep 'some/dir/'
I  like this . Thanks. It was very much helpful.

---

