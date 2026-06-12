---
title: "bash to sort files into subdirectories"
date: 2010-09-04
forum: General Help
---

### Post by aflores3 on 2010-09-04
i currently have hundreds of files all in a single directory. What I would like to do is create 8 subdirectories and move the files into the subdirectories based on the first character of the file name. Ideally, the script would omit any 'the' or 'a' and use the second word for filing purposes. No filenames have spaces. Instead they use periods

The subdirectories will be: 

0-9
a-d
e-h
i-l
m-p
q-s
t-v
w-z

Can you help?

---

### Post by asmoore82 on 2010-09-04
This is an ugly hack, but it should work.

It is good shell scripting practice to always quote variable references.
But here we have a little walk on the dark side where we play fast and loose
with unquoted references - trying to force them to do our bidding...

```
[COLOR="Blue"]#!/bin/bash
#This file is in the Public Domain

# A variable to be shell parsed - shaky ground
# Also intentionally using mixed-cased ranges for Collate Magic[/COLOR]
ranges=[COLOR="Magenta"]"0-9 a-D e-H i-L m-P q-S t-V w-Z"[/COLOR]

[COLOR="Blue"]#intentional unquoted reference to parse variable[/COLOR]
mkdir $ranges

[COLOR="Blue"]#process prefixed files first - the final "" is to process the rest[/COLOR]
for prefix in [COLOR="Magenta"]"a." "A." "the." "The." "THE." ""[/COLOR]
do
    [COLOR="Blue"]#intentional unquoted reference to parse variable[/COLOR]
    for range in $ranges
    do
        [COLOR="Blue"]#intentional unquoted reference for use of the [...] construct[/COLOR]
        mv [COLOR="Magenta"]"$prefix"[/COLOR][$range]* [COLOR="Magenta"]"$range/"[/COLOR]
    done
done

[COLOR="Blue"]#End of File[/COLOR]
```

---

### Post by asmoore82 on 2010-09-04
Here is the test suite -
assuming the script is named "sort.bash" and is somewhere in your $PATH
```
mkdir test.d
cd test.d
touch {a.,the.,}{{0..9},{a..z},{A..Z}}{{0..9},{a..z},{A..Z}}
sort.bash
```
^this will create 11532 empty files and sort them.

---

