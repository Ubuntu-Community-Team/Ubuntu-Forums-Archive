---
title: "Zgrep and AWK problem"
date: 2012-02-02
forum: General Help
---

### Post by Vercynogetorix on 2012-02-02
Not sure wheter its correct forum... 

Hi,

now ive got a problem i have to take out some info from files, its text data, so shouldnt be easy, but files are on linux server, and are over 500mb in size..

i was advised to use zgrep first, but it have its problems, as it doesnt discern string but a line,

ie. if line have page break and/or enters within, it will break it up, and if you use zgrep "-A X command", you will end up sucking in lots of unwanted content, as it will, say, take from the phrase you look for, and for example 5 next lines, 3 of which you didnt want,

now i was advised to write a bash -awk, and make such command, that it copies out from line containing x phrase untill mark given

ie. from "name_of_transaction" untill "name_of_transaction_finish_sentence"

which should logically copy out all the data i want without unwanted content,

i ask here, is there another way? i cannot write awk script, i tried to learn how, but my knowledge of programming is abysmall, and all the tutorials i have seen are still too confusing, as they are written for people who already knows whats it all supposed to do :/

any advice appreciated.

example:

i need a command that would: copy to a separate file everything from:

line containing <transaction_id=xxxxx>

untill:

<transaction=end>

---

### Post by drmrgd on 2012-02-02
Without knowing exactly the text you're trying to grab from the file (the semantics, as I've found, are important (i.e. are there brackets in the original string like you've written, is the 'xxxx' part variable, is each string you listed on a newline?)), I think you should be able to easily do this with awk.  As a newbie to awk myself, I've been using this resource of simple common awk one-liners to help me figure out how to do what I'm trying to do:

[http://www.pement.org/awk/awk1line.txt]("http://www.pement.org/awk/awk1line.txt")

See the section near the bottom called "Selective Printing of Certain Lines".  What you'll need to do is use regular expressions to frame what you'd like to grab as markers:

> # print section of file between two regular expressions (inclusive)
 awk '/Iowa/,/Montana/'             # case sensitive

What I usually do (since I do am usually working with huge files) is to make a test document that only contains a bit of it in this way:

```
head -nx bigfile > testfile
```

where x is the number of lines that you'd like to transfer to the testfile.  Then run your test awk command on the small one to see if it's working, rinse and repeat.  

Maybe give us some example text of exactly what you're looking at and someone will be able to help you get the right awk command.

---

### Post by Vercynogetorix on 2012-02-02
how it looks like its a log file, each log starts with a new line, tho a line may be broken in pieces, one after another so its 

<LOG>xxxxxx id_number xxxxxxx xxxx xxxx xxxx <LOG>

or

<LOG>xxxxx id_number xxx
xx

xxx
xxxx
</LOG>

it cannot happened that within each log there would be another line ie. like this:

<LOG> xxx id_number xxx
xxx
<LOG> xxx another_id xxx
xxx
</LOG>

hence what i really need is a formula to extract:

all lines between 1st line containing string "id_number" (ie 1234567) untill </END> which would mean that essentially whole log would be extracted after providing command with id, which only exists in first line of log (this past cannot be broken)

hope it makes more sense

VRC

ps. reason i cannot do it with zgrep is, that zgrep only searches single lines, so if log is broken into several, it will not extract all of it, and if you use zgrep -A X, where X is number of lines to search it would perhaps find broken lines, but if log designator exists in 250 entries, it would also add X of lines after the one containing entry, and you end up with 600 lines, of which 350 are useless

Otherwise, is it possible to use zgrep to find between line and marker?

example: zgrep 1234567 command </end> ~/path/file.txt.gz

where: 

1234567 is id_string
command is used to request search untill certain phrase is found, and than look for another line containing id_string


Im sorry i cannot make myself clear enough, im not programmer :S

---

