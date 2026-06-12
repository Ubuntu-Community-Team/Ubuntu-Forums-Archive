---
title: "How can I find all java files in a directory and do something with them"
date: 2010-11-18
forum: General Help
---

### Post by mcclane400 on 2010-11-18
I am trying to use "find" but I can't quite get all of the switches right for it to work.  I have a folder that contains many folders.  Let's call that original folder "MyFiles".  The subfolders contain java files (and those subfolders possibly contain subfolders that contain java files).  Here is what I want to have happen:

0.  Create a file to print to, call it "output.ps"
1.  Find all of the Java files in the MyFiles tree.
2.  For each java file that is found, append it to output.ps along with it's absolute path name.

So far I have:

find . -iname *.java

and this finds all of the java files for me.  But then I can't get the files to print to a file using exec.  Any suggestions?  Thanks in advance.

---

### Post by nothingspecial on 2010-11-18
```
find . -iname *.java > output.ps
```

---

### Post by mcclane400 on 2010-11-18
> **nothingspecial said:**
> ```
find . -iname *.java > output.ps
```

I have done this but this only saves the file names to a file.  I want to save the entire contents of each java file to the ps file.  Also, I don't want to simply pipe the contents to the ps file...  I want to be able to "print" the contents to the ps file so that I can use something like ps2pdf and create a pdf file from the ps file (unless I can do that directly with lpr or some other command).

I've tried something like this:

find . -iname *.java -exec cat {}; > myFile.txt

and this saves the contents of each file to myFile.txt but it does not "print" the file.  In other words, I want to use something like lpr instead of cat.  Any ideas?

---

### Post by lykeion on 2010-11-18
A text file is not the same as a ps file. You'll need to convert the text file to ps, perhaps using groff like this:
```
groff -Tps textfile > file.ps
```

---

