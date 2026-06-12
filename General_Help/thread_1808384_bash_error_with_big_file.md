---
title: "bash error with big file"
date: 2011-07-20
forum: General Help
---

### Post by mme oscar on 2011-07-20
Hi all,

I got a strange error when using one of my scripts with a very big file. I managed to isolate the source of the problem and here is a small test which shows what happens:

[FONT=Courier New]limit=500000000; x=1; while [ $x -le $limit ]; do printf "%010d\n" $x; x=$(( $x + 1)); done >bigfile.txt
[/FONT]
while read line ; do echo -e "TEST\t$line" ; done < bigfile.txt > bug.txt

Basically the first line creates a big 5Gb text file (be careful if you try it!) containing 500 millions numbered lines. Then the second line reads this file line by line and adds a prefix 'TEST' to each.
The problem is that after the line 0195225788 (don't know if it's always this particular line?) the script goes wrong and loops on the following sequence:    

TEST    0195225788
TEST    225778
TEST    0195225779
TEST    0195225780
TEST    0195225781
TEST    0195225782
TEST    0195225783
TEST    0195225784
TEST    0195225785
TEST    0195225786
TEST    0195225787
TEST    0195225788
TEST    225778

so don't forget to stop the script, the bug.txt file will grow infinitely!

Does anyone has an idea about what happens? Is there a limit in bash which can explain that? If not, is it a bug and where am I supposed to post it please?

Thanks!

---

### Post by gmargo on 2011-07-20
I can confirm this.  Very interesting.

I used a perl script to create the bigfile.txt since shell is way too slow.  And I only went up to 200M (redirect output manually):
```

#!/usr/bin/perl -w
use strict;
use warnings;

#        0195225788
my $limit=200000000;
printf "%010d\n", $_ foreach 1 .. $limit;
exit 0;

```Then used a bash script to read it:
```

#!/bin/bash

while read line
do
        echo -e "TEST\t$line"
done <bigfile.txt >bug.txt

```And sure enough, it gets up to line "0195225788" and then goes into the exact same pattern you show.

Tested on 64-bit 10.10 Maverick with GNU bash, version 4.1.5(1)-release (x86_64-pc-linux-gnu)
Tested on 64-bit 11.04 Natty with GNU bash, version 4.2.8(1)-release (x86_64-pc-linux-gnu)

Bonus:  I tested the **dash** shell: it works fine, so it is likely a **bash** bug.

---

### Post by mme oscar on 2011-07-21
Thank you for confirming the problem

since it seems to really be a bug I reported it here:
[http://groups.google.com/group/gnu.bash.bug/browse_thread/thread/ef4bc62baec3dd05#](http://groups.google.com/group/gnu.bash.bug/browse_thread/thread/ef4bc62baec3dd05#)

---

### Post by gmargo on 2011-07-21
Here's an interesting clue:  The input file has 11 characters per line, and it errors out on line 195225788.  Multiply it out:

11 * 195225788 = 2147483668 = 0x80000014

So it looks like a signed 32-bit integer overflow.

---

### Post by gmargo on 2011-07-21
Another interesting tidbit.  The following two commands should be equivalent. The first one, with the pipe, works fine.  The second one, with the stdin redirect, exhibits the error.
```

cat bigfile.txt | while read line ; do echo -e "TEST\t$line" ; done > bug_from_pipe.txt

while read line ; do echo -e "TEST\t$line" ; done < bigfile.txt > bug_from_redir.txt

```

---

### Post by mme oscar on 2011-07-22
made me realize I had forgotten the input redirection "<big.file.txt" in my first post in the second line, sorry. 
now corrected.

---

