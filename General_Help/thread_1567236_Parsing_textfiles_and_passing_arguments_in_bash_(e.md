---
title: "Parsing textfiles and passing arguments in bash (eg; to preserve tracker-tag metadata"
date: 2010-09-03
forum: General Help
---

### Post by tehowe on 2010-09-03
Hello script gurus;

I'm at the bottom of the bash learning curve, looking up, hoping someone can toss me a line.

I need to update tracker on my system but this will erase the metatag database I've been building up over the course of months for the purpose of indexing a news archive.

So the solution seems to be, 1) save the output of tracker-tag to a text file for all relevant files within a directory, 2) upgrade tracker (since the version in the Ubuntu repositories is very much out of date) and then 3) use a script to parse the text file and pass appropriate arguments back to tracker-tag to rebuild the database.

It sounds as though it ought to be simple enough, but I need a push in the right direction, which hopefully will not be off the cliff. Before I confuse my metaphors any further, here's what the text file looks like.

```
Found:
'/home/me/Documents/News/2010/August/20100801_NewsArticle1.html': tag1|tag2|tag3
'/home/me/Documents/News/2010/August/20100802_NewsArticle2.html':  tag1|tag2
'/home/me/Documents/News/2010/August/20100802_NewsArticle3.html':  tag1|tag2|tag3|tag4
```.
.
.
etc.

I've generated this textfile with a script based around  this command

```
tracker-tag *html > tag-dump-$WORKDIR/_$ITEMS
```The text files have an arbitrary number of entries. So now, using a second script, I want to step through it line by line (except for the first line that reads 'Found:') and automatically pass a series of command lines that look like this

```
tracker-tag -a tag1 -a tag2 -a tag3 20100801_NewsArticle1.html
```I know (vaguely) that piping commands through some combination of sed, grep, and xargs is the way to go. Can anyone add some clarity here? Should be a useful exercise not only for myself but anyone else struggling to learn the basics of string manipulation in the shell.

Thanks in advance.

---

### Post by DaithiF on 2010-09-03
Hi,
a couple of options:
1. using awk:
```
awk -f script.awk somefile
```where script.awk contains:
```
BEGIN { FS=":" }
$1 == "Found" { next }
{ 
    ntags = split($2, tags, "|");
    cmd="echo tracker-tag ";
    for(i=0; i<ntags; i++)
        cmd = cmd " -a " tags[i];
    cmd = cmd " " $1;
    system(cmd)
}


```2. using sed, more terse, but less clear
```
tail -n +1 somefile | sed 's/^\(.*\):\s*\(.*\)$/\2\t\1/;s/^[^\t]/echo tracker-
tag -a &/; s/|/ -a /g; s/\t/ /' 

```
#2. only generates commands in the required form, it doesn't also execute them (unlike #1). redirect the output to a file and then run that file to execute those commands

in both cases, remove **echo** if happy that its doing the right thing.
and of course to run for multiple files enclose in a loop of some sort, eg.
```
for file in tagdir/*     
do
   command from 1. above with "$file" in place of somefile
done

```

---

### Post by tehowe on 2010-09-03
I've made some progress here... it should be amusing for the pros to see this code at least. 

Problems to be solved include, 

1) Figuring out how many tags there are in the string and adding an "-a " before each one.
2) In the loop to pass the arguments to tracker-tag, starting on the second line in the file.

```
#!/bin/bash

# I bet this doesn't work
# add sed scripts together with -e once debugging's complete
# so various temporary files aren't generated

# on 2nd line to last line, remove everything between first ' and last / to remove path
sed '2,$ s_\(\'[a-zA-Z/]\) \(.*\)_\2_' <tag-dump >tag-dump-new1

# now remove the ': and any |'s between the tags, replacing them with a space
sed '2,$ s_\':_ _' <tag-dump-new1 >tag-dump-new2
sed '2,$ s_|_ _g' <tag-dump-new2 >tag-dump-new3

# rearrange things so the tags come before the filename
sed '2,$ s_\([0-9a-zA-Z\_]*\) \([a-z ]\)_\2 \1_' <tag-dump-new2 >tag-dump-new3

# add "-a" before each tag - but how do you count the tags in sed? is a recursion 
# within sed even possible?
sed ????????????????? <tag-dump-new3 >tag-dump-final

#loop to send each line to xargs
START=2
END=wc -l tag-dump

for line in "$(cat tag-dump-final)"
do
    echo "$line" | xargs tracker-tag
done
```

---

### Post by tehowe on 2010-09-03
Thanks for the reply! I'll try that when I get home. I'm sure it beats mine hands down. :)

> **DaithiF said:**
> Hi,
a couple of options:
1. using awk:
```
awk -f script.awk somefile
```where script.awk contains:
```
BEGIN { FS=":" }
$1 == "Found" { next }
{ 
    ntags = split($2, tags, "|");
    cmd="echo tracker-tag ";
    for(i=0; i<ntags; i++)
        cmd = cmd " -a " tags[i];
    cmd = cmd " " $1;
    system(cmd)
}


```2. using sed, more terse, but less clear
```
tail -n +1 somefile | sed 's/^\(.*\):\s*\(.*\)$/\2\t\1/;s/^[^\t]/echo tracker-
tag -a &/; s/|/ -a /g; s/\t/ /' 

```#2. only generates commands in the required form, it doesn't also execute them (unlike #1). redirect the output to a file and then run that file to execute those commands

in both cases, remove **echo** if happy that its doing the right thing.
and of course to run for multiple files enclose in a loop of some sort, eg.
```
for file in tagdir/*     
do
   command from 1. above with "$file" in place of somefile
done

```

---

