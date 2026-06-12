---
title: "problems running a .sh file"
date: 2012-06-08
forum: General Help
---

### Post by ultan on 2012-06-08
Im trying to execute a .sh file on a program i downloaded from this site [http://www.ark.cs.cmu.edu/mheilman/questions/](http://www.ark.cs.cmu.edu/mheilman/questions/)

ive tried running the build.sh file and a few other things

someone said it might be a java problem

anybody any ideas?

---

### Post by MG&amp;TL on 2012-06-08
Okay, I'm presuming you have this folder in Downloads, otherwise you can either move it there, or (learn how to) use cd.

1. Open terminal.

2. ```
cd Downloads/whatyoucalledthedownload
```

3.```
bash ./build.sh
```

4. Paste output/errors here.

---

### Post by ultan on 2012-06-08
ive tried cd downloads/whaticalledthefile but it just tells me that its not their!

i know its their though

---

### Post by greenpeace on 2012-06-08
can you run the following please?  It will tell us what is there at that location:

```
file ~/Downloads/whatyoucalledthedownload
```

---

### Post by SeijiSensei on 2012-06-08
Does the file have execute permissions?  Use "sudo chmod a+x /path/to/build.sh" to make the file executable.

Also if you are in the same directory as the script, you cannot run it without using the "./script.sh" syntax.

Honestly, though, it's pretty hard to diagnose a problem if you don't give us the exact error messages you received.

---

### Post by steeldriver on 2012-06-08
I don't think it's anything to do with the .sh file - I've added a suggestion in your original thread

[http://ubuntuforums.org/showpost.php?p=12010159&postcount=18](http://ubuntuforums.org/showpost.php?p=12010159&postcount=18)

do that and then try

```
./run.sh < tests/article461.Mary_II_of_England.txt
```

regards

---

