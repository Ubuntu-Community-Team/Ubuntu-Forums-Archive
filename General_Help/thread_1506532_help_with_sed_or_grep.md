---
title: "help with sed or grep?"
date: 2010-06-10
forum: General Help
---

### Post by daveli on 2010-06-10
Hi there!
I have a long text file organised in blocks of 21 lines. Line 10 has a Name entry and I want to find and remove from the file those blocks where the "Name" entry has a _d1_ in it.

I have managed to extract these blocks to another file using

$ cat infile | grep -A 11 -B 9 'Name=.*_d1_.*' >> outfile

but how can I actually remove these blocks from the "infile"?

Thanks for your help,

D.

---

### Post by BoneKracker on 2010-06-10
This should be possible to do with a little sed script.

It would be helpful if you could provide (i.e. attach) some sample data (e.g., a contiguous portion of a file that includes five or six blocks, two of which should be deleted). This will save time with people asking questions like, "is it possible to identify block delimitation in any way other than line numbering?", "are the blocks always consistently 21 lines without exception?", and "are there blank lines?".

[Edit: never mind, just adapt and test what I've provided below.]

---

### Post by StuartN on 2010-06-10
> **BoneKracker said:**
> "is it possible to identify block delimitation in any way other than line numbering?"

Yes, if every line is of the form "field=value", then there must be some neat solution - especially if there is a record delimiter as well.

But a bit of butchery like this would work:

```
echo -n > outfile
while read f1 ; do
 read f2 ; read f3 ; read f4 ...
  if echo $f10 | grep "_d1_" ; then
    # records to be deleted
  else
    echo -e "$f1\n$f2\n$f3\n$f4\n ..." >> outfile
  fi
done < infile
```

---

### Post by BoneKracker on 2010-06-10
That looks like it should work, but there's a fairly simple sed solution.  Rather that wait for sample data, here it is generically:

You need to make substitutions for "first" and "last" though:
[LIST]
[*]Substitute for "first" a regular expression that matches the first line of all blocks (and only the first line).
[*]Substitute for "last" a regular expression that matches the last line of all blocks (and only the last line).
[/LIST]
```
#!/bin/bash

sed -e ':top 
/first/,/last/ {
   /last/!{
      $!{
         N;  
         b top
      }
   } 
   /Name=.*_d1_.*/d;
}'
```

I've created some sample data of my own as best I can, and it seems to fine.


This solution was adapted from an example at [this source]("http://www.linuxtopia.org/online_books/linux_tool_guides/the_sed_faq/sedfaq4_011.html").
I'd be interested to see what an AWK solution to this problem looks like, if anybody knows.

---

### Post by daveli on 2010-06-11
Hi again, thanks for your help. I wonder why it is better to identify start and end of blocks instead of using positions. I show some entries of the file I want to parse. Keep in mind that the file has different sections and I am only interested in a specific section that contains such blocks, some of them I want to remove. The block to remove will contain its two empty lines after it, so that the structure remains intact. The [Unit****] code, can go upto less than 100000. Next you can see three blocks and only the second one has the _d1_ expression I am after, so the output in this example should have two blocks only.

[Unit1080]
Name=NONE
Direction=3
NumAtoms=2      1
NumCells=2
UnitNumber=1080
UnitType=3
NumberBlocks=1

[Unit1080_Block1]
Name=DBo36_o13
BlockNumber=1
NumAtoms=2
NumCells=2
StartPosition=0
StopPosition=1
CellHeader=X    Y       EXPOS   
Cell1=164       297     0       
Cell2=451       653     1       


[Unit1081]
Name=NONE
Direction=3
NumAtoms=2      1
NumCells=2
UnitNumber=2699
UnitType=3
NumberBlocks=1

[Unit1081_Block1]
Name=DB1_53_d1_o13
BlockNumber=1
NumAtoms=2
NumCells=2
StartPosition=0
StopPosition=1
CellHeader=X    Y       EXPOS   
Cell1=137       466     0       
Cell2=447       176     1      


[Unit1082]
Name=NONE
Direction=3
NumAtoms=2      1
NumCells=2
UnitNumber=1081
UnitType=3
NumberBlocks=1

[Unit1082_Block1]
Name=DBo37_o13
BlockNumber=1
NumAtoms=2
NumCells=2
StartPosition=0
StopPosition=1
CellHeader=X    Y       EXPOS   
Cell1=228       654     0       
Cell2=240       1       1

---

### Post by StuartN on 2010-06-11
> **daveli said:**
> ... I wonder why it is better to identify start and end of blocks instead of using positions. ... the file has different sections

Identifying the start (and end) ensures that a whole record is processed as a unit. Relying on position could mean destroying all subsequent records if any record is malformed, or has a missing or extra field.

It might be worth adding a positional check, for instance if you did read in every field, and assume that the first field always contains "Unit", then this will print a message and exit on error:

```
if ! echo $f1 | grep "Unit" ; then echo "Incorrect field 1 in $f1" ; exit ; fi
```

I assume you have some means of identifying the relevant section of the document, in order to start processing at line 1 of the first record and to terminate on line 21 of the last.

And I assume that _Block1 is never followed by _Block2 within a record in the data set.

---

### Post by BoneKracker on 2010-06-11
That's why I wanted to see the sample data.
I think this is a job for awk.  This ought to get you started:

```
#!/bin/bash

awk '
    BEGIN{RS="\n\n\n"; ORS=RS}
    /_d1_/{next}1
' old.txt > new.txt
```

Explanation:
"Records are separated by two blank lines (both in the existing file and the one we will output.
If a record contains the regex '_d1_' move on to the next one, otherwise print the record.
Use old.txt as input and send output to new.txt."

---

