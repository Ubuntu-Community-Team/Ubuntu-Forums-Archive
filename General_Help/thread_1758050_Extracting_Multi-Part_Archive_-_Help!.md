---
title: "Extracting Multi-Part Archive - Help!"
date: 2011-05-14
forum: General Help
---

### Post by aoniumo on 2011-05-14
[http://ubuntuforums.org/showthread.php?t=952119](http://ubuntuforums.org/showthread.php?t=952119)

 I tried the link above but it doesn't work.    I move the the files on the desktop and home folder, but still nothing.       I renamed the files hello.z01 and hello.zip and below is the result: _____________________________________________________________________ iru@ubuntu:~$ cat hello.z01 hello.zip > hello-concatenated.zip 
cat: hello.z01: No such file or directory 
cat: hello.zip: No such file or directory 

siru@ubuntu:~$ zip -F hello-concatenated.zip     zip warning: fix options -F and -FF require --out:                      zip -F indamagedarchive --out outfixedarchive  zip error: Invalid command arguments (fix options require --out) siru@ubuntu:~$ unzip hello-concatenated.zip Archive:  hello-concatenated.zip   End-of-central-directory signature not found.  Either this file is not   a zipfile, or it constitutes one disk of a multi-part archive.  In the   latter case the central directory and zipfile comment will be found on   the last disk(s) of this archive. unzip:  cannot find zipfile directory in one of hello-concatenated.zip or         hello-concatenated.zip.zip, and cannot find hello-concatenated.zip.ZIP, period. __________________________________________________________________________

---

### Post by aoniumo on 2011-05-14
Problem 2: What happened to my post?  That's not how it looked when i was typing it?

---

### Post by satanselbow on 2011-05-14
If you can find the original webpage you downloaded the files from see if they give you anymore info about how the files were created... you might find this useful to rejoin your particular archive ;)

[http://www.hjsplit.org/linux/](http://www.hjsplit.org/linux/)

---

### Post by dandnsmith on 2011-05-14
It's possible that the renaming has messed things up (breaking the relationship between the pieces), and anyway you usually have to start unzipping with the last part of the sequence (as that holds the info about the previous parts as well and what they all contain).

You definitely don't just concatenate the files - that's a real nono

HTH

---

### Post by aoniumo on 2011-05-14
It's working now after overnight. Thanks

---

