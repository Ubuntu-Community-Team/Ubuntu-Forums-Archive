---
title: "Bulk file rename based on contents"
date: 2012-08-31
forum: General Help
---

### Post by nrKist on 2012-08-31
Seems like this would be something that either a command at the CL or a script could accomplish most efficiently, but I'm game for a GUI option too if that's the best option.

So here's the specifics. Hopefully this is clear.
I'd like to rename a large number of text files based on the text before the first space in the file. Each beginning text is unique, so collisions aren't a problem. The text I'm interested in is in the format "NN.NN " So that's 1 or 2 numbers, a decimal, 1 or 2 more numbers, then a space.

example 1
text= "1.14 "
rename= 1.14.txt

example 2
text= "2.4 "
rename= 2.4.txt

example 3
text= "11.8 "
rename 11.8.txt


Solutions? Suggestions? I'm toast and I'm going to have to rename them all manually?

Thanks!

---

### Post by steeldriver on 2012-08-31
```
for file in *.txt; do  mv "$file" "$(sed -nr '1s/^([^ \t]+)(.*$)/\1/p' "$file").$file"; done
```or more specifically

```
for file in *.txt; do  mv "$file" "$(sed -nr '1s/^([0-9]+\.[0-9]+)(.*$)/\1/p' "$file").$file"; done
```maybe?

[B]Obviously it would be a good idea to dry-run it with 'echo' in place of the mv to make sure it's constructing the new names properly
[/B]
```
for file in *.txt; do  echo "$(sed -nr '1s/^([0-9]+\.[0-9]+)(.*$)/\1/p' "$file").$file"; done
```

---

### Post by Vaphell on 2012-08-31
these sed expressions won't work if the line format is *text= "9.99 "*
```
sed -rn '1s/^.*"([0-9.]+) ".*$/\1/p' "$file"
``` would be more like it

---

### Post by steeldriver on 2012-08-31
my apologies - I had assumed the OP meant the first line was literally of the form

```
1.14 other stuff
```rather than 

```
text="1.14 " other stuff
```

---

### Post by Vaphell on 2012-08-31
hm, i read more into the OP's post and i think it's me who misunderstood. Carry on ;-)

---

### Post by steeldriver on 2012-08-31
maybe... maybe not 

it's always nice when people post actual file snips to clarify these things :D

---

### Post by sisco311 on 2012-08-31
No need for GNU sed (NOTE: -r is a GNU extention); you can use ERE in BASH (>=3.1):
```

for file in *.txt
do
    reg='^[[:digit:]]{1,2}\.[[:digit:]]{1,2} '
    if [[ $file =~ $reg ]]
    then
        printf '%s\t-\t%s\n' "$file" "${file#* }"
    fi
done

```

---

### Post by Vaphell on 2012-08-31
but that does not use the content of the first line of the file but the file name itself.
One would have to go with
```
for file in *.txt
do
  read -r line < "$file"
  echo mv "$file" "${$line% *}.txt"
done
```
or something

---

### Post by RedRat on 2012-08-31
Have you considered Thunar. It has a very good batch renaming ability. YOu can either focus it on only the suffix, i.e., in your case 'txt'. Thunar can ignore all of the periods in the file name proper. Thunar allows you to rename by inserting whatever you want either from the left or right, which it appears that you want to do.

---

### Post by steeldriver on 2012-08-31
so if we put that all together...

```
#!/bin/bash

reg='^[[:digit:]]{1,2}\.[[:digit:]]{1,2}'

for file in *.txt; do 
  read -r -d' ' var < "$file"
  if [[ $var =~ $reg ]]; then 
    echo mv "$file" "$var"."$file"
  fi
done
```

??

---

### Post by nrKist on 2012-08-31
steeldriver's original interpretation is closest to correct. 

Let's say we have a file named...```
c0019.tif.txt

```

and the contents of the file are...```
1.13 Blah Blah, Blah
Blah Blah blah
```

But my goal is to change the name to...```
1.13.txt
```

Rather than...
```
1.13.c0019.tif.txt
```
which his original command does. But I'd be quite happy with that. I think I may understand the command well enough to make this change though. Using the "echo" example...
```
for file in *.txt; do  echo "$(sed -nr '1s/^([0-9]+\.[0-9]+)(.*$)/\1/p' "$file").txt; done
``` seems to do the trick.

Two twists. One I had not considered in my original description and one the in the results of the command.

First, occasionally there will be a letter at the end of the string of numbers...```
1.13b blah blah
```
If that letter is present I'd like to include it...```
1.13b.txt
```

Second, a few aren't renaming as I'd expect. One file contains...```
14.4 Park and entrance
```
But fails to add anything to the name. ```
.c0218.tif.txt
```
About 10% of the others react the same.

---

### Post by steeldriver on 2012-08-31
you can fix the first issue by adding an optional single alphabetical character as

```
[[:alpha:]]?
```or

```
[A-Za-z]?
```to the first match group, i.e.

```
([0-9]+\.[0-9]+[A-Za-z]?)
```or with POSIX classes

```
([[:digit:]]+\.[[:digit:]]+[[:alpha:]]?)
```I don't know why it's not working in the 10% of cases you mention - did you try the second (bash script) version with sisco's regex?

---

### Post by nrKist on 2012-08-31
Should be a couple of hours before I'll be able to work on it again. I haven't tried sisco's yet. 
I did try the bash script you just posted, minus the mv, and interestingly it completely ignores the files that are being mis-named with the "for file in *.txt; do  echo "$(sed -nr '1s/^([0-9]+\.[0-9]+)(.*$)/\1/p' "$file").$file; done" command.

---

### Post by steeldriver on 2012-08-31
yes the bash script version actually tests whether the regex match succeeds

```
if [[ $var =~ $reg ]]; then
  mv ...
fi
``` 

before going ahead with the move - my original version was defective in that respect and would have silently renamed any nonmatching filename to .filename (confusingly hiding them)

---

### Post by nrKist on 2012-09-02
RedRat, I'd be willing to try Thunar, but how do I tell it what to retrieve from each file to use as the new name?

steeldriver, Looks like your script is now working. After some poking about I found that the problematic files had the BOM character at their start. Once I stripped it out they renamed properly just like the rest.

Thanks!
Keith

---

### Post by steeldriver on 2012-09-02
I don't know what a BOM character is! but glad you got it working, I figured there had to be some non-printing character we were missing - regex syntax is unforgiving about that kind of thing

---

### Post by MG&amp;TL on 2012-09-02
> **nrKist said:**
> Thanks to steeldriver my issue is solved. Unfortunately I can find no way for me to change the thread from [all variants] to [SOLVED]. Would a mod like to do that for me?

Under "Thread Tools" at the top of the page, click "Mark thread as solved". :)

---

### Post by RedRat on 2012-09-02
> **nrKist said:**
> RedRat, I'd be willing to try Thunar, but how do I tell it what to retrieve from each file to use as the new name?

steeldriver, Looks like your script is now working. After some poking about I found that the problematic files had the BOM character at their start. Once I stripped it out they renamed properly just like the rest.

Thanks!
Keith
nrKist
Sorry, I misread what you were trying to do. I thought that you were only interested in a simple bulk renaming of a set of files. I did not realize that you wanted to actually read the file and then name it based on its content. My bad.

---

### Post by nrKist on 2012-09-03
Thanks MG&TL!


No problem RedRat, more input is always good.

---

