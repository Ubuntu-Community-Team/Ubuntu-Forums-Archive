---
title: "Printing directory contents to text file"
date: 2009-10-06
forum: General Help
---

### Post by overcast on 2009-10-06
I know how to do this in windows. by typing it in dir>print.txt" will create text file with list of directory contents listed. But  this is for windows. Is there any terminal command like windows to do achieve this ? any program to do this ?


How to do this in ubuntu ?

---

### Post by kanikilu on 2009-10-06
Same way, just with **ls** instead of **dir**: ```
ls -l > print.txt
``` More on [IO Redirection](http://tldp.org/LDP/intro-linux/html/chap_05.html).

---

### Post by overcast on 2009-10-06
Thanks :)

I'll try that out. In between, is there any software that does similar job ? i mean sorting files by date and printing them out in text file or clipboard ?

---

### Post by alphaniner on 2009-10-06
You can use **ls -lt** to sort by date, and there is also the **sort** command.  Don't know of any software.

---

### Post by overcast on 2009-10-07
is it possible to use sort command and print the list ?

---

### Post by alphaniner on 2009-10-07
There are a number of ways.  You can **ls -l > file** and then **sort file > file2**

Or you can use a pipe to combine this into one step **ls -l | sort > file**.  The pipe is the vertical bar and it's on the key with the '\'.

Keep in mind that you will need to use some flags (aka options, like -l for ls) with **sort**.  The syntax can be a bit confusing and I still need to refer to online examples when I use it.

---

### Post by Pinos on 2009-11-20
Use Print directory to print the [directory listing]("http://www.print-directory.com") to a file..

Find Here :  [http://www.print-directory.com](http://www.print-directory.com)

---

### Post by Mike_tn on 2012-03-26
When you use ls -l > print.txt Is there a way to automatically get the current date in the file name written this way,
```
filename-2012-03-26
``` ?

---

### Post by Vaphell on 2012-03-26
yes
```
ls -l > file-$(date '+%Y-%m-%d').txt
```
$() captures the output of *date* command (try running *date '+%Y-%m-%d'*) and glues it with the fixed rest of the filename. +<format> describes how *date* output should be formatted
if you want to check what you can do with the date format, run
```
date --help
```

---

### Post by Mike_tn on 2012-03-26
> **Vaphell said:**
> 
```
ls -l > file-$(date '+%Y-%m-%d').txt
```

You are awesome, thanks! That works like a dream. Gonna look at the man page too.  I will use that for outputting ```
dpkg --get-selections > ~/my-packages
```But now this```
dpkg --get-selections > ~/my-packages-$(date '+%Y-%m-%d')
``` Because I make that list every time I run updates. Maybe I'm paranoid but it's a kind of backup. Not my only backup.

---

