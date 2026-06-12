---
title: "Sorting Multiple Keys?"
date: 2011-08-27
forum: General Help
---

### Post by Chunkizzo on 2011-08-27
Hello I am trying to sort files in a directory numerically.  The files are listed like this below
whatever-10.txt
whatever-11.txt
whatever-12.txt
whatever-13.txt
whatever-14.txt
whatever-15.txt
whatever-1.txt
whatever-2.txt
whatever-3.txt
whatever-4.txt
whatever-5.txt
whatever-6.txt
whatever-7.txt
whatever-8.txt
whatever-9.txt

I have tried sort -n and it outputs the same as above I need the files to be listed in order from 1-10 I am still unfamiliar with the sort -k command but any help with this would be appreciated.

---

### Post by thefasterblueone on 2011-08-27
The application 'sort' is for organizing lines of text within a file.

 If you want to organize files within a directory click 'view' 'arrange items' in file manager.

---

### Post by Chunkizzo on 2011-08-27
What I'm working on is in Bash sort can be used in a directory, and need to be organized through the script or via command line, I need a non GUI solution but thanks for the reply

---

### Post by Chunkizzo on 2011-08-27
Ok I figured it out guys thank you!

my solution to anyone with the same issue was

~$ ls | sort -t - -k 2 -n

::sort the delimiter of "-" and in the 2cnd column sort numerically:: 

 BTW:  This will work fine for sorting files within a directory not just txt within files.

---

