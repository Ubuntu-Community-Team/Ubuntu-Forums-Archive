---
title: "move files to new folders with name of file?"
date: 2012-09-24
forum: General Help
---

### Post by sohlinux on 2012-09-24
Hi,

I have 62600 files all in one folder, I want to move all the files into new folders with the name of the file

for example - 

all files beginning with anthony move to a folder called anthony

all files beginning with tom move to a folder called tom

I dont want to do them all individually as there are many so is there a command to do them all?

thanks

---

### Post by carranty on 2012-09-24
I'm not sure I unserstand.  Do you want to move *each* file into a new folder, giving 62600 folders?

If not, can you give some example filenames and what folder you would like them to go into.  Also when you say all files beginning with, e.g. Anthony, is there a blank space following the name i.e. Anthony Bloggs, or is it AnthonyBloggs etc.

---

### Post by sohlinux on 2012-09-24
there are 120 files beginning with anthony, all files beginning with anthony should be moved into the same folder called anthony

the file names look like "anthony new york" or "tom rome"

there are about 450 names in total so the result would be 450 new directories created and all 62600 file will be moved into those folders.


thanks

---

### Post by carranty on 2012-09-24
Ok, but in order to be able to instruct bash (or whatever program other people may use) to recognise the end of a name we'll need to know how the filename is written.  For example if your files are
Anthony Jones.ext
Anthony Bloggs.ext
Anthony Smith.ext

then the end of the name can be defined as the first whitespace, similarly if they are of the form Anthony.Jones / AnthonyJones / Anthony_Jones the end of name can be defined as the period/2nd capital letter and _ respectively.  Hence I need an example filename in order to help - assuming of course that all of your filenames are of the same format.

---

### Post by sohlinux on 2012-09-24
> **carranty said:**
> Ok, but in order to be able to instruct bash (or whatever program other people may use) to recognise the end of a name we'll need to know how the filename is written.  For example if your files are
Anthony Jones.ext
Anthony Bloggs.ext
Anthony Smith.ext

then the end of the name can be defined as the first whitespace, similarly if they are of the form Anthony.Jones / AnthonyJones / Anthony_Jones the end of name can be defined as the period/2nd capital letter and _ respectively.  Hence I need an example filename in order to help - assuming of course that all of your filenames are of the same format.

there are 4 different extensions .jpg .txt .pdf .doc

example 

Anthony Jones italy.jpg
Anthony Jones.doc
Anthony Bloggs barcelona.jpg
Anthony Smith job.txt
Anthony Jones interview.txt
Anthony Jones access.pdf
Anthony Smith ec1.jpg

there are 120 files all beginning with Anthony, so the command needs to create a folder call Anthony and move all the files beginning with Anthony to the new folder called Anthony.

the command needs to pick out the first word of each file and create a new folder of that first word then move all the files beginning with that word into that folder. there are 450 different first words. example "tom house.txt"  "holiday london.jpg" "balance.pdf" "sent out.doc" "sent.txt" victory.jpg

the end result will be 450 new folders, all folders will contain a number of files beginning with the same word.

---

### Post by Vaphell on 2012-09-24
try this
```
for f in *' '*; do dir="${f%% *}"; mkdir "$dir"; mv "$f" "$dir/$f"; done
```

not terribly efficient but should work. For all files with space in name
- get first word (${f%% *}=take f and remove longest possible space+anything on the right)
- try to create the dir with the name (it will get created at 1st occurence, error will be thrown later but it doesn't matter)
- move file to subdir

---

### Post by sohlinux on 2012-09-24
> **Vaphell said:**
> try this
```
for f in *' '*; do dir="${f%% *}"; mkdir "$dir"; mv "$f" "$dir/$f"; done
```

not terribly efficient but should work. For all files with space in name
- get first word (${f%% *}=remove longest space+anything from f)
- try to create the dir with the name (it will get created at 1st occurence, error will be thrown later but it doesn't matter)
- move file to subdir

thanks for the info but before I run this can you tell me if its going to rename the files with spaces?

I dont want to rename any files

---

### Post by sohlinux on 2012-09-24
tried it on a test folder and it shows

mv: cannot stat `* *': No such file or directory


edit: it worked but I forgot to mention some filed dont have a space so they were not moved

---

### Post by Vaphell on 2012-09-24
no, $f is not modified in any way
(file) -> (first_word)/(file)

to be sure you can do a dry run and print things - better safe than sorry
replace ```
mv "$f" "$dir/$f";
```
with ```
echo mv "'$f'" "'$dir/$f'";
```
i added single quotes to echo line to make crystal clear where words begin and end, with spaces that would not be too obvious.
You can also add -v option to mv to get visual feedback when mv is performed.
```
$ > "a b"    # create empty 'a b'
$ for f in *' '*; do dir="${f%% *}"; mkdir "$dir"; mv -v "$f" "$dir/$f"; done
`a b' -> `a/a b'
```


if you like what you see, you can run it armed and dangerous :-)

---

### Post by Vaphell on 2012-09-24
was the dir you tried empty? if no matching files are found, pattern is treated literally. At least one spaced name is required

---

### Post by sohlinux on 2012-09-24
> **Vaphell said:**
> no, $f is not modified in any way
(file) (first_word)/(file)

to be sure you can do a dry run and print things - better safe than sorry
replace ```
mv "$f" "$dir/$f";
```
with ```
echo mv "'$f'" "'$dir/$f'";
```
i added single quotes to echo line to make crystal clear where words begin and end, with spaces that would not be too obvious.
if you like what you see, you can run it armed and dangerous :-)

thanks that worked fine, do you know how to make it work so it chooses the first 2 or 3 or 4 words?

so for example if the folder contains

tom and jess in spain.jpg
tom and jess in uk.jpg
tom and jess in usa.jpg

so it will move all files starting with the same 4 words tom and jess in

or the same first 3 words

john april 2010 spain.doc
john april 2010 france.pdf
john april 2010 uk.jpg

thanks

---

### Post by Vaphell on 2012-09-24
that's more complicated. How to detect correct set of words automatically? Computers don't really work like 'i know it when i see it' ;-)

let's say you got
- tom and jess in spain.jpg
- tom and jess in uk.jpg
- tom and jess in usa.jpg

take the first word and see if there are other matches. If yes, test with 2nd word added, if yes add another word. If the number becomes 1, previous pattern is most likely ok. Somewhat doable in this scenario but there is non-trivial ambiguity lurking.

lets say you have
- tom and henry 1.jpg
- tom and jess in usa.jpg
- tom and jess in france.jpg

there is possibility that you will be left with 'tom and' as a result because in this case it's the longest sequence of words producing set greater than 1 (if you dissect tom and henry 1.jpg)
I think it would be better if the script asked for feedback
eg
1. tom
2. tom and
3. tom and jess
4. tom and jess in
#?
you pick 3. and
- 'tom and jess' subdir is created
- 'tom and jess'* are moved to 'tom and jess'

... but that would be quite a lot of questions, considering 400+ categories

---

### Post by sohlinux on 2012-09-24
> **Vaphell said:**
> that's more complicated. How to detect correct set of words automatically?
let's say you got

tom and jess in spain.jpg
tom and jess in uk.jpg
tom and jess in usa.jpg

take the first name, take first word and see if there are other matches. If yes, test with 2nd word added, if yes add another word. If the number becomes 1, previous pattern is most likely ok. Somewhat doable but there is non-trivial ambiguity lurking.

lets say you have
- tom and henry 1.jpg
- tom and jess in usa.jpg
- tom and jess in france.jpg

there is possibility that you will be left with 'tom and' as a result because in this case it's the longest sequence of words producing set greater than 1 (if you dissect tom and henry 1.jpg)
I think it would be better if the script asked for feedback
eg
1. tom
2. tom and
3. tom and jess
4. tom and jess in
#?
you pick 3. and
- 'tom and jess' subdir is created
- 'tom and jess'* are moved to 'tom and jess'

... but that would be quite a lot of questions, considering 400+ categories

thanks

ok then how about just the first 4 words?

---

### Post by Vaphell on 2012-09-24
regular expressions

```
$ f="a b c d.txt"
$ echo "$f" | sed -r 's/(([^ ]+ ){3}[^ ]+)[ .].+/\1/'
a b c d
$ f="a b c d e f.txt"
$ echo "$f" | sed -r 's/(([^ ]+ ){3}[^ ]+)[ .].+/\1/'
a b c d
```

[^ ]+ = non-empty sequence of non-spaces, [ .] = space-or-dot, () marks the first four words and \1 makes the result contain only that part.

```
for f in *\ *\ *\ *; do dir=$( echo "$f" | sed -r 's/(([^ ]+ ){3}[^ ]+)[ .].+/\1/'); **echo** mkdir "$dir"; **echo** mv "$dir" "$dir/$f"; done
```

---

### Post by sohlinux on 2012-09-24
> **Vaphell said:**
> regular expressions

```
$ f="a b c d.txt"
$ echo "$f" | sed -r 's/(([^ ]+ ){3}[^ ]+)[ .].+/\1/'
a b c d
$ f="a b c d e f.txt"
$ echo "$f" | sed -r 's/(([^ ]+ ){3}[^ ]+)[ .].+/\1/'
a b c d
```

[^ ]+ = non-empty sequence of non-spaces, [ .] = space-or-dot, () marks the first four words and \1 makes the result contain only that part.

```
for f in *\ *\ *\ *; do dir=$( echo "$f" | sed -r 's/(([^ ]+ ){3}[^ ]+)[ .].+/\1/'); **echo** mkdir "$dir"; **echo** mv "$dir" "$dir/$f"; done
```

thanks but that created the directories ok but it didnt move the files, I did remove the echo

thanks

---

### Post by Vaphell on 2012-09-24
example of the file that didn't move?

---

### Post by Lars Noodén on 2012-09-24
It looks like the 2nd to last instance of $dir ought to be $f:

```
for f in *\ *\ *\ *; do dir=$( echo "$f" | sed -r 's/(([^ ]+ ){3}[^ ]+)[ .].+/\1/'); echo mkdir "$dir"; echo mv "$f" "$dir/$f"; done

```

---

### Post by Vaphell on 2012-09-24
true, i made an error :/

---

### Post by sohlinux on 2012-09-24
thanks! perfect . solved :)

---

