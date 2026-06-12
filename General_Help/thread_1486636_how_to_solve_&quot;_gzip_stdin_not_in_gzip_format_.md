---
title: "how to solve &quot; gzip: stdin: not in gzip format &quot; ?"
date: 2010-05-18
forum: General Help
---

### Post by gads on 2010-05-18
I'm new with Ubuntu and I'm using Xubuntu 10.04,and I have encountered a problem when I extract the software that I have downloaded...

this is what happened...
when I extracted the software....

[B]xu-ciso@xu-ciso-desktop:~$ sudo tar -zxvf nagios-3.2.1.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

xu-ciso@xu-ciso-desktop:~$ [/B]

how can I fix this problem?
can you give me some step on how to solve it?

---

### Post by sedawk on 2010-05-18
Looks like the download is not compressed or broken.

You can try the command file, it will tell you
what it thinks about the file, e.g. if it
looks only like data, or a tar archive, or a 
gzip file ("file <file_to_examine>").

If it is recognized as tar you can run tar without
the "z" option.

Most likely they have a checksum on their web site
like md5sum or sha1. Compare the size of you file
and the checksum with the one on their web site.

---

### Post by gmargo on 2010-05-18
1. Don't use sudo here.  No reason for it.

2. The file is likely corrupted:

2a. Find out the file type with the command "file nagios-3.2.1.tar.gz".  It should say "gzip compressed data" if the header looks good.

2b. Use the gzip command to test the integrity of the file with "gzip -t nagios-3.2.1.tar.gz".

3. The repository contains nagios-3.2.0 (see the **nagios3** package).  Is there any particular reason that you must compile your own?

---

