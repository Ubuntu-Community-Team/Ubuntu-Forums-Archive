---
title: "Running a script on the current directory"
date: 2009-08-04
forum: General Help
---

### Post by leezer3 on 2009-08-04
OK, this is doing my head in :P
I'm not bad at bash or perl, but nowhere near good either. 
What I've got at present is a simple Perl script- When run, this enumerates through each of the files in it's current directory, and runs MKVMerge on all the videos. Finally, the script cleans up after itself with a filesize check and deletion of the original files.

What I'm trying to do now is to get this script to work on a global basis without having to move the base file each time. To this end, I've shifted the script to /usr/bin - From here, the script executes nicely, but it points itself at /usr/bin, not the current working directory.
Any pointers please? :)

-Leezer-

---

### Post by Subban on 2009-08-04
If you are running it from a terminal, then in bash something like:

```
workdir="`pwd`"
```

workdir is the variable you want to store the current folder in. the double quotes wrapping it will deal with spaces.

The single quotes tell bash to run the quoted command in this case, pwd.

pwd is the terminal command to return the Present Working Directory.

later in your script you can then of course use it something like:

```
for i in *.txt; do echo "looks its file $i";done
``` (not tested written off top of my head)

That isn't going to be a perfect explanation, for a start its not perl (I don't do perl), but as you mentioned knowing both you can make use of it and translate?

Also, I'm good enough at bash but no expert, and my explanation is probably wrong in many many ways so DO NOT take it as anything other basically wrong.

---

### Post by credobyte on 2009-08-04
Perl & command line arguments: [http://www.cyberciti.biz/faq/howto-pass-perl-command-line-arguments/](http://www.cyberciti.biz/faq/howto-pass-perl-command-line-arguments/)

---

### Post by leezer3 on 2009-08-04
Gotcha, cheers :)
For anyone looking to do something like this, this is my rather kludged solution:
I created a new BASH script to launch the Perl script, like this:
```
#!/bin/bash
PERL=/usr/bin/perl
workdir="`pwd`"
$PERL /usr/bin/bmkv.pl "$workdir"
```
I then added this to the start of the perl script, so that it changes to the current working directory, which is passed as a command line argument by the previous batch script:
```
chdir("$ARGV[0]") or die "$!";
```

Works perfectly for what I'm trying to do :)
(Probably a much easier way to do this, but it works!)

-Leezer-

---

### Post by geirha on 2009-08-04
When you start the script, it will not be in the directory where the script is located, it will be in the directory you're currently in (the one reported by the pwd command and the $PWD environment variable). So you're really just changing to the same dir here.

---

### Post by leezer3 on 2009-08-04
Trouble is that it wasn't, hence why I posted in the fist place :D
I've no idea whether it was an issue with my Perl or what, but the fix is doing the job.

-Leezer-

---

### Post by geirha on 2009-08-04
You must have a very weird setup then. I don't know of any programs that behave that way, and my install of perl doesn't either.
```

~$ cat ~/bin/perltest 
#!/usr/bin/env perl
use Cwd;
print cwd . "\n";
~$ cd /tmp
/tmp$ ~/bin/perltest
/tmp
/tmp$ cd /
/$ ~/bin/perltest
/
/$ 

```

---

