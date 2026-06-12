---
title: "Perl script"
date: 2011-01-09
forum: General Help
---

### Post by ghostzen on 2011-01-09
Hi all,
below is my perl parsing file that I test on my Ubuntu apache2 Webserver.
 
```

#!/usr/bin/perl
use CGI qw/:standard/;
my $x = param("first");
my $y = param("last");

print header;
print starthtml;
print "Hello there! It's nice to meet you, $x $y." ;
print endhtml;
#***************************************#
open (NAME,">> names.txt");
print NAME "$x $y\n";
close(NAME);


```
Everything works fine, except the code under the stars.  I can't get it to create a file names.txt and redirect the output to names.txt.
What did I do wrong?
Please help.
Thanks

---

### Post by jim_deadlock on 2011-01-09
A couple of suggestions:

Try changing this:

```
open (NAME,">> names.txt");
```

... to this:

```
open (NAME,'>>./names.txt');
```

(remove the space) ... or better still:

```
open (NAME,'>>/full/path/to/names.txt');
```

Also, try creating the empty file and making it fully writable first. The filesystem may not allow creation of the file from an outside source.

---

### Post by ghostzen on 2011-01-10
Thank you so much.  It works!!!  
Since the file is in my root accessed folder, it needs write permission, which I totally forgot.  Your last sentence "from an outside source" gives me the hint.  You're awesome!

---

