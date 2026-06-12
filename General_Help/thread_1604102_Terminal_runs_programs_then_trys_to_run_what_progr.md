---
title: "Terminal runs programs then trys to run what program prints to the terminal"
date: 2010-10-23
forum: General Help
---

### Post by JoeOrozco on 2010-10-23
When I try to run any java or perl program from the terminal, it will run the program, then it runs what the program prints to the terminal.

Simple perl program:

#!/usr/bin/perl

use strict;
use warnings;

my $data = $ARGV[0];
my @rows = split(';', $data);
chomp @rows;
print @rows;

Output: 
joe@joe0:~/Desktop$ ./inverse.pl 1;2
12: command not found
joe@joe0:~/Desktop$ ./inverse.pl cat;dog
catNo command 'dog' found, did you mean:
 Command 'mog' from package 'mazeofgalious' (universe)
 Command 'dig' from package 'dnsutils' (main)
 Command 'dlg' from package 'pccts' (universe)
 Command 'iog' from package 'iog' (universe)
 Command 'eog' from package 'eog' (main)
 Command 'dot' from package 'graphviz' (main)
dog: command not found
joe@joe0:~/Desktop$

Not sure what is going on, any help would be appreciated

---

### Post by DaithiF on 2010-10-23
Hi,
its not that the shell executes whatever is output by the perl script, its just that the ';' is a statement separator in bash, so what you are actually running is two separate commands:

firstly
```
./inverse.pl 1

```then
```
2

```

put quotes around the parameter so that the whole things gets passed to your script:

./inverse.pl "1;2"

---

### Post by JoeOrozco on 2010-10-23
Thank you

---

