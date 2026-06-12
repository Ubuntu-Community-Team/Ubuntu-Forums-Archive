---
title: "Multi-threaded SHA512 checksum supporting sub-directories?"
date: 2009-07-29
forum: General Help
---

### Post by palmboy5 on 2009-07-29
I notice that sha512sum in terminal has no support for going into sub-directories. Nor is it able to run as many threads as there are CPU cores, for that matter.

md5deep seems to be capable of going into sub-directories, but I see no sha512sum equivalent (sha512deep?)...

So, is there any terminal or GUI based checksumming program for SHA512 that can checksum everything within a directory, even those that are in sub-directories of that directory? Even better if it can do more than just one file at a time.

---

### Post by palmboy5 on 2009-08-01
Bump?

---

### Post by palmboy5 on 2009-08-02
Ooookayyy.. I can understand Windows having better support for games and GPU acceleration stuff but this is just checksumming! There is ExactFile for Windows that can do more than what these various terminal checksum programs can even dream of doing! Is there seriously nothing for linux??

---

### Post by Andre.C on 2011-06-18
Why is it so essential for you to generate a sha512 checksum? Save your self time and effort by sticking with md5deep and using either sha256 or tiger192. I sincerely doubt anything you are trying to accomplish in Ubuntu needs a 512bit cryptographic hash function. Also, as far as I know there is no way to thread any digest algorithm; they are all sequential and will probably remain that way for some time to come**. The best you can do for now is run a message digest inside a thread (on a per file basis) or use a scripting language to spawn individual digest processes concurrently on different files.  Most languages can query the OS for the number of available logical cpu's, its a trivial matter to use that data to  drive your work distribution logic. You can pretty much use any modern language for that task as they all have support for cryptographic digest functions.

**[http://en.wikipedia.org/wiki/Skein_%28hash_function%29]("http://en.wikipedia.org/wiki/Skein_%28hash_function%29")

---

### Post by dethrophes on 2011-12-30
Not quiet right current gen hash algorithims are designed to be linear non threadable. Next gen are however per definition multi threadable. i.e. md6 etc.

---

