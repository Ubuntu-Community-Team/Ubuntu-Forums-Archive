---
title: "Linux text manipulation: sort columns according to the first row"
date: 2011-06-20
forum: General Help
---

### Post by lethalfang on 2011-06-20
Let's say I have 50,000 rows of data that looks like the following:


B   A   D   C   Z   E   F   ......
3   1   4   1   9   2   3   ......
...... ......
0   1   3   4   2   4   8   ......


And I want to sort the columns of the data according to the first row, such that the output looks like:

A   B   C   D   E   F   ......   Z
1   3   1   4   2   3   ......   9
...... ......
1   0   4   3   4   8   ......   2



How do I do that?


I tried to transpose columns into rows using "awk," and then use the "sort" command, and transpose back use "awk."

But awk doesn't work if the number of columns exceed ~33K, which happens when those rows are first transposed to columns, i.e., transposing back didn't work for me. 


Any idea how to do this?

Thanks in advance.

---

### Post by FormatSeize on 2011-06-20
Is pasting it into the OpenOffice version of a spreadsheet and using the sort function there, then pasting it back into the file not an option? If you have to do a lot of them, you can use the OpenOffice spreadsheet thingy to automate the process.

---

### Post by lethalfang on 2011-06-20
I just tried it and ran into the same issue: cannot copy-and-paste the transpose of that data set, because the number of columns (50K rows into 50K columns) exceeds the program limit.

---

### Post by AlphaLexman on 2011-06-20
Why are you transposing rows into columns?

My version of OOo will take 1,048,576 **rows**

What is the length of each row?

[S]I don't understand your sorting requirements either![/S]
**EDIT:** Re-read the OP, each column keeps the same numerical value below the top-most alphabetic character.

---

### Post by lethalfang on 2011-06-20
> **AlphaLexman said:**
> Why are you transposing rows into columns?

My version of OOo will take 1,048,576 **rows**

What is the length of each row?

I don't understand your sorting requirements either!


I want to sort the columns, but the "sort" command sorts rows. 
So I first wanted to transpose columns into rows, sort it using "sort" command, and then transpose it back. 
The problem was that I could not transpose it back. When I tried to transpose columns back into rows, the "awk" program could not deal with >35000 columns. 


Can Openoffice directly sort columns? I tried the same method: transpose columns into rows, and then sort the rows, and transpose back. But I couldn't transpose because it would have too many columns.

---

### Post by gmargo on 2011-06-20
A trivial **perl** problem:
```

#!/usr/bin/perl -w
# vim: ts=8 sts=4 sw=4 et :
use strict;
use warnings;

# First line of input is the sort key
my $firstline = <>;
$firstline =~ s/[[:space:]]+\z//s;
my @firstline = split /[[:space:]]/,$firstline;

# Sort first line to create sorted list of indexes
my @sindexes = sort { $firstline[$a] cmp $firstline[$b] } (0 .. $#firstline);

# Print first line, sorted
print "".(join ' ', map { $firstline[$_] } @sindexes)."\n";

# Read the rest of the lines, and print them sorted.
while (<>)
{
    s/[[:space:]]+\z//s;
    my @line = split /[[:space:]]/;
    print "".(join ' ', map { $line[$_] } @sindexes)."\n";
}

``````

$ cat in.txt
B A D C Z E F
3 1 4 1 9 2 3
0 1 3 4 2 4 8 

$ sortcol.pl  < in.txt 
A B C D E F Z
1 3 1 4 2 3 9
1 0 4 3 4 8 2

```

---

### Post by g999b on 2011-06-20
Definitely a Perl job...

---

### Post by lethalfang on 2011-06-20
> **gmargo said:**
> A trivial **perl** problem:
```

#!/usr/bin/perl -w
# vim: ts=8 sts=4 sw=4 et :
use strict;
use warnings;

# First line of input is the sort key
my $firstline = <>;
$firstline =~ s/[[:space:]]+\z//s;
my @firstline = split /[[:space:]]/,$firstline;

# Sort first line to create sorted list of indexes
my @sindexes = sort { $firstline[$a] cmp $firstline[$b] } (0 .. $#firstline);

# Print first line, sorted
print "".(join ' ', map { $firstline[$_] } @sindexes)."\n";

# Read the rest of the lines, and print them sorted.
while (<>)
{
    s/[[:space:]]+\z//s;
    my @line = split /[[:space:]]/;
    print "".(join ' ', map { $line[$_] } @sindexes)."\n";
}

``````

$ cat in.txt
B A D C Z E F
3 1 4 1 9 2 3
0 1 3 4 2 4 8 

$ sortcol.pl  < in.txt 
A B C D E F Z
1 3 1 4 2 3 9
1 0 4 3 4 8 2

```


Thanks! This looks great.
One more question though, since I know nothing about Perl. If the field separator is tab, what changes in the code?

---

### Post by gmargo on 2011-06-20
> **lethalfang said:**
> Thanks! This looks great.
One more question though, since I know nothing about Perl. If the field separator is tab, what changes in the code?

Nothing changes for the input part.  For output, see each **join** statement - the first argument is the field separator.  Replace the ' ' with "\t":

```

print "".(join "\t", map { $firstline[$_] } @sindexes)."\n";

-and-

    print "".(join "\t", map { $line[$_] } @sindexes)."\n";

```Be sure to enclose the backslash-t in double quotes.

---

### Post by lethalfang on 2011-06-20
> **gmargo said:**
> Nothing changes for the input part.  For output, see each **join** statement - the first argument is the field separator.  Replace the ' ' with "\t":

```

print "".(join "\t", map { $firstline[$_] } @sindexes)."\n";

-and-

    print "".(join "\t", map { $line[$_] } @sindexes)."\n";

```Be sure to enclose the backslash-t in double quotes.


Thanks. That works very well! :guitar:

---

