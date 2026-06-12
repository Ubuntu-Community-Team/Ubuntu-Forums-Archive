---
title: "Extracting.tgz files"
date: 2010-07-20
forum: General Help
---

### Post by albertramsbottom on 2010-07-20
Very much a newbie here

I have issues trying to extract a .tgz file and was wondering if you could help me

I have used the command tar - xvwzf filename.tar but I get the following error:

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@test:/datastore/Newfolder# tar -xvwzf filename.tgz

Any ideas would be great

---

### Post by surfer on 2010-07-20
is that a space there between '-' and 'xvwzf'? that sould read '-xvwzf'. (i did not bother to check the options yet).

you could also use 'file-roller' to extract the archive.

---

### Post by rubylaser on 2010-07-20
```
tar xzvf filename.tgz
``` Should do it for you.

---

### Post by albertramsbottom on 2010-07-20
Thanks folks but I get the same error

Strange:(

I cant use file roller as I have the server version without the gui

Cheers

---

### Post by rubylaser on 2010-07-20
A few questions: 1. Is the file pubicly available, so I could take a look at it. 2. This is a stupid one, but are you in the same directory as the tgz when you're running that command?

---

### Post by albertramsbottom on 2010-07-20
The file isnt publicly availible and yes I am in the same directory as the .tgz file

Thanks for your help

---

### Post by surfer on 2010-07-20
what happens if you open it with file-roller?

---

### Post by albertramsbottom on 2010-07-20
Using the server version with no gui

Best way to learn I recon

Cheers

---

### Post by rubylaser on 2010-07-20
The only other thing I can think of it that you might have a corrupt archive. You can try to identify the file type with the "file" command as in:

file filename.tgz

In addition, you can test the integrity of the file with the following:

tar -tvvf filename.tgz

Can you post the results of those two commands?

---

### Post by albertramsbottom on 2010-07-20
Here si the results

file 20100720-0000.tgz
20100720-0000.tgz: gzip compressed data, from Unix, last modified: Tue Jul 20 00:00:02 2010


and 

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

I think you are right about the archive being corrupt.  I have deleted to old one and moved a new one from a mounted share but still the same.  If it makes any difference its 16.5GB

:o

---

### Post by rubylaser on 2010-07-20
It looks like it's a corrupt archive, it should look like this if it's working okay.

```
&#10140;  003 Tutorials  tar -tvvf Digital\ Tutors.tar.bz2                   
drwxrwsr-x  0 root   users       0 Jul 29  2009 Digital Tutors/
drwxrwsr-x  0 root   users       0 Jul 13  2009 Digital Tutors/Digital Tutors pipline with maya and zbrush/
-rwxrwsr-x  0 root   users 17167820 Jun 21  2007 Digital Tutors/Digital Tutors pipline with maya and zbrush/1.mov
```

Meaning that it can see the contents inside the file. Can you run the tar -tvvf on the .tgz on the mounted drive to see if that reports properly?

---

