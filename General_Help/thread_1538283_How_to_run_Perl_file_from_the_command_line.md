---
title: "How to run Perl file from the command line"
date: 2010-07-24
forum: General Help
---

### Post by rstackhouse on 2010-07-24
I'm trying to run a perl script found at [http://wiki.scribus.net/index.php/Web_optimised_PDF](http://wiki.scribus.net/index.php/Web_optimised_PDF).

running "compress-newsletter.pl input.pdf" produces the result:

-bash: compress-newsletter.pl: command not found

Please help! :(

---

### Post by glickboy on 2010-07-24
You have to call it like this...

perl compress-newsletter.pl input.pdf

---

### Post by rstackhouse on 2010-07-24
If I run "perl compress-resume.pl input.pdf" then I get:

Can't find compress-resume.pl on PATH, '.' not in PATH.

---

### Post by geoffjay on 2010-07-25
Try adding this to the top of the file (must be first line)
#!/usr/bin/env perl

then make executable
$ chmod +x compress-newsletter.pl

now you should be able to execute the script directly using
$ ./compress-newsletter.pl input.pdf

---

### Post by rstackhouse on 2010-07-25
calling ./compress-resume.pl resume.pdf ran the script without changing the shebang line, but I have no idea why.

---

