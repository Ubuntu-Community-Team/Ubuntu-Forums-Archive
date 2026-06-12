---
title: "extracting archive from cdrom"
date: 2010-07-31
forum: General Help
---

### Post by Oblivion4234 on 2010-07-31
Hello. I am trying to install MySQL, Apache, and PHP onto my Linux Ubuntu laptop from a cdrom that I got from a teach yourself MySQL, Apache, and PHP book I bought. First off there were two steps which i think i did right. The first was to mount the CD-ROM under /mnt in my file system which i did and there seems to be no problem except for the reply 

"mount: block device /dev/sr0 is write-protected, mounting read-only"

but I figured that this was acceptable seeing as how the cd was mounted and kept on going. It then told me to create a user for the MySQL server which I did with no errors, but then the book tells me to input this code

"cd /usr/local/"
"gunzip < /mnt/MySQL/Linux/tarballs/source/mysql-5.0.51a.tar.gz | tar xf -"

which returns the message

"bash: /mnt/MySQL/Linux/tarballs/source/mysql-5.0.51a.tar.gz: No such file or directory
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors"

now first of all there are two things I need to explain, first of all I was superuser for all of this by using the command su at the beginning of my terminal session. Second of all the symbol "|" on my line of code above looks different from the symbol in the book. It should have a small space in the middle of it. However it looks like this on my keyboard so I am assuming it is simply a difference in text font. That is it, it would be really nice to figure out what went wrong because to be honest I am curious as to why the book is giving me code that gives multiple errors. It states that this is an installation guide for Linux users and has been tested on Red Hat Linux and SuSE Linux so I am curious as to what is going on. Thank you for any constructive input you have to give.

---

### Post by jerenept on 2010-07-31
Why not install Apache-Mysql-PHP from the repositories? I can guarantee it is going to be easier than what you are doing there.

Just open Synaptic Package Manager., and search for apache, mysql and php.

---

### Post by Oblivion4234 on 2010-07-31
Jerenept, that is a possibility and I have looked those up in my Synaptic Package Manager however there were many different programs of MySQL, PHP, and Apache that are quite frankly confusing to me as I bought the book for me to understand what I was getting into. Also I want to know what I am doing wrong so that the next time I attempt to do something like this in the future I will understand how to fix it. Finally if this does not work then there is an on line section in the chapter if I want to get it on line, however the code to installing it and setting up the various programs is similar to the code i just mentioned. Therefore I would really appreciate an answer to my problem with the code, thank you though for your suggestion.

---

### Post by Bachstelze on 2010-07-31
> **Oblivion4234 said:**
> 
"bash: /mnt/MySQL/Linux/tarballs/source/mysql-5.0.51a.tar.gz: No such file or directory


Pretty self-explanatory: the file is not where you're expecting it to be.  Probably the mount point for the CD is different, what is the outpuf of [font=monospace]mount[/font]?

If you want to just use the repos, you'll need apache2, php5 and mysql-server-5.0.

---

### Post by Oblivion4234 on 2010-07-31
Thank you Bach for your input, I did install the packages that you mentioned and everything is fine. However I am a little confused about where these programs are located in Ubuntu, are they within the File System or are they programs under applications. Like I said I am only a beginner in this and just starting to understand Ubuntu so any input would be great. Thank you for your patience.

---

