---
title: "Need help with awk filtering"
date: 2011-06-12
forum: General Help
---

### Post by wiseguy12851 on 2011-06-12
I did a recursive search using grep in a list of files for lines containing a specific word. It brought everything up ok but now I need to filter it out and print the results to a file with

* Path Name
* A section of the line

The path ends in a colon and after it could be any number of words, spaces, and punctuation which the one phrase I need being somewhere in there - I need the phrase to be filtered out and merged with the path like this

"path/to/file: phrase"

I'm guessing awk is the best way to do this but I don't know anything at all about awk except it specializes in filtering.

---

### Post by Vaphell on 2011-06-12
i must admit i don't understand exactly what you want to get
if it's the 'path: only-matching-string' then grep -o is the way to go
if you want 'path: matching-string' in 1st line and a snippet holding it in 2nd line then something along the lines of
```
#!/bin/bash

pattern='def'

grep -r "$pattern" . | while read line
do
  echo "${line%%:*}:" $( echo "${line#*:}" | grep -o "$pattern" )
  echo "${line#*:}"
done

```
should do the trick (i admit it's quite ugly :)).

Give a clear example of input and expected output.

---

### Post by DaithiF on 2011-06-13
```
grep -or "your phrase" .
```
seems like a good start, like Vaphell says, unless the phrase varies line by line and you therefore need to match on a subset of the phrase.

---

