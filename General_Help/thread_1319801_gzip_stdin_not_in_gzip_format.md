---
title: "gzip: stdin: not in gzip format"
date: 2009-11-08
forum: General Help
---

### Post by ProgressionMurph on 2009-11-08
Hello everyone,

I was wondering if anyone was familiar with the following error's:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

and

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

I've been trying to unzip them to no avail.  Unsure were to begin.

Sincerely,
Alex

---

### Post by hal8000 on 2009-11-08
This error happens when the file you are de-compressing is not in gzip format.
Either post the name of the file you are extracting or the resource you downloaded it from, so someone can test the results.

---

### Post by ProgressionMurph on 2009-11-08
Thanks for getting back.  I'm having the first error with 1 tar.gz file that I compressed and the second error with the second Tar.gz file that I compresssed.

---

### Post by ProgressionMurph on 2009-11-08
I get those errors when using Archive Manager.  When I try to use ark to open it I get:

Reading the archive '/home/alex/InformationNexus/TransformationNexus.tar.gz' failed with the error 'The archive reading failed with message: Unrecognized archive format: Invalid or incomplete multibyte or wide character

---

### Post by ProgressionMurph on 2009-11-08
Got them to work.  I could open them with ark, xarchiver and the other archiver program when I put them on my Ipod.  Thats were I put the files before I upgraded to Karmic.  Then I put the files on Karmic and it didn't work.

Thanks for the help!

---

### Post by jrwoooolf on 2010-12-12
Am getting the gzip: stdin: not in gzip format
tar: Child returned status 1
tar: error is not recoverable: exiting now
 
The code was:
wget -O adodb4991.tgz [http://sourceforge.net/projects/adodb/files/adodb-php-4-and-5/adodb-4991-for-php/adodb4991.tgz/download](http://sourceforge.net/projects/adodb/files/adodb-php-4-and-5/adodb-4991-for-php/adodb4991.tgz/download)

---

### Post by newSuperHuman on 2012-04-12
I got this message when my file was not fully transferred (via scp command from another computer) because the computer I was transferring to was out of memory (although it appeared to be a successful transfer in all other respects).

---

### Post by oldos2er on 2012-04-12
Closed, necromancy.

---

