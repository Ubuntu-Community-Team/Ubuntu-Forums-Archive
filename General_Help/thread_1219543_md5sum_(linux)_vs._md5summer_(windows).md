---
title: "md5sum (linux) vs. md5summer (windows)"
date: 2009-07-21
forum: General Help
---

### Post by jalandoak on 2009-07-21
Ok,

Everything I burn to a disc gets a md5 checksum file to help ensure my archive copies are good copies.  I'm trying to abandon windows entirely, and making good progress, but I've come across a problem that seems like it should be easy to solve, but...

md5summer produced a checksum file with this, as an example:

55ce38618efd42bc32bbb55212a60812 *pestpatrol-v9consumer/aspy9_en.exe 
07aaaa18549b905ed17d4697c547aad9 *pestpatrol-v9consumer/CA Anti-Spyware 2007 - Datasheet.pdf 
e1717b1221a2d262390ecc83b9d827bc *pestpatrol-v9consumer/CA Anti-Spyware 2007 - Installation Guide.pdf 


Running md5sum -c filename produces this:

: FAILED open or read
: No such file or directory

The files exist, and it will pass with md5summer under Windows.  I think it has something to do with the asterisk, but I'm not positive.  Any help would be appreciated.

j.

---

### Post by DGortze380 on 2009-07-21
> **jalandoak said:**
> Ok,

Everything I burn to a disc gets a md5 checksum file to help ensure my archive copies are good copies.  I'm trying to abandon windows entirely, and making good progress, but I've come across a problem that seems like it should be easy to solve, but...

md5summer produced a checksum file with this, as an example:

55ce38618efd42bc32bbb55212a60812 *pestpatrol-v9consumer/aspy9_en.exe 
07aaaa18549b905ed17d4697c547aad9 *pestpatrol-v9consumer/CA Anti-Spyware 2007 - Datasheet.pdf 
e1717b1221a2d262390ecc83b9d827bc *pestpatrol-v9consumer/CA Anti-Spyware 2007 - Installation Guide.pdf 


Running md5sum -c filename produces this:

: FAILED open or read
: No such file or directory

The files exist, and it will pass with md5summer under Windows.  I think it has something to do with the asterisk, but I'm not positive.  Any help would be appreciated.

j.

So there is an asterisk as the first character in the file name?

That's a wild card in bash and will certainly cause a problem.

You could try \*filename but ultimately I would avoid using an asterisk or other special characters and spaces in file names.

---

### Post by jalandoak on 2009-07-21
Hi, thanks for the response.  No, the filename that I run md5sum on doesn't have an asterisk.  The asterisks are in the text file.  Each line in the file has a hash, a space, an asterisk, and the directory/filename each hash has been generated for.

j.

---

### Post by crono_logical on 2010-02-16
Came across this thread via google, after noticing windows checksummers inserting asterisks (*'s) in front of filenames but the linux ones don't by default, and wondering why linux would give me the same errors mentioned above when trying to use these checksum files.

If anyone else comes across this thread wondering, it turns out it's actually a line-break issue (windows using CRLF). Running the checksum file through the dos2unix tool before feeding it to md5sum or sha1sum on linux fixed the problems.

---

### Post by PathFinder_Cate on 2010-02-23
The asterisk flags a file as binary (as opposed to text).  Some versions of the command
line program md5sum.exe require the  asterisk ahead of the filename in a checksum file
to properly check  binary files.

See tip #3 on this web page: [http://www.codejacked.com/using-md5sum-to-validate-the-integrity-of-downloaded-files/](http://www.codejacked.com/using-md5sum-to-validate-the-integrity-of-downloaded-files/)

---

