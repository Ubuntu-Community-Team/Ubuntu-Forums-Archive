---
title: "Trouble with Grep"
date: 2011-10-27
forum: General Help
---

### Post by bonesjones256 on 2011-10-27
Ok I'm pretty good with Linux. Been using it for servers for years. But I've got the most stupid problem that I can't figure out. 

I've created a script to run tdsskiller on my windows machines, and upload the log file to my linux server. ok done no problem there

So now I have about 200 log files and I'm wanting to search those files and if the file contains the word "warning" in any way shape or form I want to know. 

I've tried every way of using grep I can think of and it never will spit any results but I know there is at least one log file that contains what I'm looking for cause I found it manually. And here is the whole line. 

"14:57:04.0516 3428	\Device\Harddisk0\DR0 ( TDSS File System ) - warning"

Since that line has the WORD "warning" i want to know. 

Any ideas?

---

### Post by Vaphell on 2011-10-27
so what does your grep looks like?
grep 'warning' <file_that_has_it> doesn't return anything?

---

### Post by ajgreeny on 2011-10-27
```
grep -w warning /path/to/*.log
```should do it if your log files are all named as *name*.log.

If not change the "path/to" string to fit your situation.

---

### Post by bonesjones256 on 2011-10-28
> **ajgreeny said:**
> ```
grep -w warning /path/to/*.log
```should do it if your log files are all named as *name*.log.

If not change the "path/to" string to fit your situation.

See that's what i'm doing, and everytime it comes back with NOTHING. very bizarre as I'm very familiar with grep.
The ONLY thing i can think of is that when these files were uploaded )via ftp) the trigger was set to BINARY on each upload. 

And these logs are from a windows machine.

---

### Post by deloquencia on 2011-10-28
Hmm, a windows machine...

Run **file** on the files, just to check what kind of file it is.
Perhaps it's an issue with encoding?

---

### Post by SeijiSensei on 2011-10-28
You might try installing [tofrodos]("http://packages.ubuntu.com/lucid/tofrodos") and using the fromdos program to clean up the extraneous line feeds.

The real problem is that binary transfer from FTP I suspect.  Have you tried forcing a text transfer?

---

### Post by SeijiSensei on 2011-10-28
You might try installing [tofrodos]("http://packages.ubuntu.com/lucid/tofrodos") and using the fromdos program to clean up the extraneous line feeds.

The real problem is that binary transfer from FTP I suspect.  Have you tried forcing a text transfer?  What about compressing the files in Windows with ZIP, transferring the ZIP files, then unpacking them on the Linux box with [unzip]("http://packages.ubuntu.com/lucid/unzip")?

---

### Post by bonesjones256 on 2011-10-28
I just thought today that the binary transfer could have been the problem typo in the script. I'm going to try again Monday. 

I ran "file" on one of them and this is what it shows. 

DESKTOP156.log: Little-endian UTF-16 Unicode text, with CRLF, CR line terminators


Ran fromdos to them all, didn't help.

---

### Post by deloquencia on 2011-10-29
UTF-16 Unicode... hmm...

I checked some files at my system which I recently got from a Windows System and I have the same problems grepping anything in that files - just like you have. 

I ran **iconv** on that files and got a usuable - greppable files.

For example run:
**iconv -f UTF-16 -t UTF-8 <bad-file> -o <hopefully-better-file>**
**iconv -l** gives you a list with all supported encodings

Hope that helps you to grep into your files :)

---

