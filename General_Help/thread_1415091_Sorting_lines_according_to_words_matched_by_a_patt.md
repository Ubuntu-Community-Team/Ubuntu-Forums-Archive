---
title: "Sorting lines according to words matched by a pattern"
date: 2010-02-24
forum: General Help
---

### Post by tjoff on 2010-02-24
Hello out there.

I have a text file for which each line contains a four-digit number.

Example:

1945 was the year World War 2 ended.
Battle of Hastings: 1066.
In 1492 America was discovered by a european - again. 

I want to sort the lines according to the numerical value of the number, such that I get:

Battle of Hastings: 1066.
In 1492 America was discovered by a european - again. 
1945 was the year World War 2 ended.

I have tried to fool around with grep, awk and sort to do this, and I am sure it can be done. 
I know i can use the pattern [0-9][0-9][0-9][0-9] to match a four digit number, and i can use the -o flag of grep to isolate the numbers and pipe them into sort. But I want to retain the whole text line.
Any ideas?

---

### Post by gmargo on 2010-02-24
Perl to the rescue:

```

#!/usr/bin/perl -w
use strict;
use warnings;

my @lines = <DATA>;

my @newlines =
    map { $_->[1] }
    sort { $a->[0] <=> $b->[0] }
    map { [ ((/(\d{4})/) ? $1 : 0), $_ ] }
    @lines;

print $_ foreach @newlines;

__DATA__
1945 was the year World War 2 ended.
Battle of Hastings: 1066.
This line does not have a number.
In 1492 America was discovered by a european - again. 

```Output:
```

This line does not have a number.
Battle of Hastings: 1066.
In 1492 America was discovered by a european - again. 
1945 was the year World War 2 ended.

```

---

### Post by steviefordi on 2010-02-24
Not tested it but how about:

```
grep -o '[0-9][0-9][0-9][0-9]' file | sort -g | while read line; do grep $line file; done
```

This should isolate the numbers with grep and sort them with sort. The output from sort is piped into a while loop, that - one sorted number at a time - calls grep on the original file using the number as the search pattern.

---

### Post by tjoff on 2010-02-24
Thanks a lot to both of you! Both methods work like a charm.
Stevefordis suggestion was just the kind of answer I was looking for, and gmarcos answer a reminder that I should look more into Perl for this kind of task, when it gets just a little more complicated.

---

### Post by gmargo on 2010-02-24
> **steviefordi said:**
> ```
grep -o '[0-9][0-9][0-9][0-9]' file | sort -g | while read line; do grep $line file; done
```

I don't think this will work properly if you have duplicate numbers - you'll end up with more lines of output than input.  Maybe a "sort -gu" would fix that. You'd also lose lines with no number.

---

### Post by gmargo on 2010-02-24
> **tjoff said:**
> Thanks a lot to both of you! Both methods work like a charm.
Stevefordis suggestion was just the kind of answer I was looking for, and gmarcos answer a reminder that I should look more into Perl for this kind of task, when it gets just a little more complicated.

Well, just for you, since you might become more interested in Perl (my favorite language), I revised the program to be more immediately useful to you. This one will open and read any number of filenames on the command line or read from standard input.

```

#!/usr/bin/perl -w
use strict;
use warnings;

my @lines;
push(@lines, $_) while (<>);

@lines =
    map { $_->[1] }
    sort { $a->[0] <=> $b->[0] }
    map { [ ((/(\d{4})/) ? $1 : 0), $_] }
    @lines;

print $_ foreach @lines;

```

---

### Post by kaibob on 2010-02-25
I thought I would play around with this to see if I could address gmargo's concerns with steviefordi's suggestion. I utilized gmargo's suggestion to avoid duplicates by use the grep unique option and then added another grep command with the invert-match option to print lines that did not contain matching numbers. It's a bit of a kludge but does work. 

```
#!/bin/bash

grep -v '[0-9]\{4\}' file | sort

grep -o '[0-9]\{4\}' file | sort -gu | while read line ; do
   grep $line file   
done
```

> $ cat file
1945 was the year World War 2 ended.
Battle of Hastings: 1066.
1945 was the year World War 2 ended. Duplicate.
In 1492 America was discovered by a european - again. 
This line does not have a number.
$
$ sortscript
This line does not have a number.
Battle of Hastings: 1066.
In 1492 America was discovered by a european - again. 
1945 was the year World War 2 ended.
1945 was the year World War 2 ended. Duplicate.

---

### Post by steviefordi on 2010-02-25
> I don't think this will work properly if you have duplicate numbers - you'll end up with more lines of output than input.

Quite right gmargo!

I never said it was perfect - but I thought it would do for tjoff's situation.

Anyway, thanks for pointing it out gmargo and thanks to kaibob for taking the time to sort it out.

---

