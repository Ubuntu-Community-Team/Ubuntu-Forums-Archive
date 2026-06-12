---
title: "awk or sed"
date: 2010-06-29
forum: General Help
---

### Post by ankit.vader on 2010-06-29
i have a file with following contents

<[1:4, 2:5, 3:6] 53s, 10s, 999999s, 34s, 28s, 49s, 82s, 54s, 15s, 51s, 26s, 61s, 39s, 45s, 61s, 74s, 97s, 56s, 32s, 26s, 42s, 99s, 93s, 90s, 2s, 12s, 27s, 51s, 20s, 63s, 3s, 92s, 39s, 98s, 97s, 20s, 999999s, 84s, 35s, 78s, 71s, 96s, 86s, 70s, 44s, 23s, 42s, 77s, 26s, 73s, 20s, 4s, 51s, 41s, 56s, 29s, 82s, 2s, 78s, 35s, 96s, 0s, 72s, 82s>

from this file i want to extract anything between '[' and ']'. in this case [1:4, 2:5, 3:6]

how can this be done using awk or sed.

---

### Post by stlsaint on 2010-06-29
You will want to post this in the programming section and merge the two post. Also not to be mean or anything but a simple google search will yield some results for you! :guitar:

---

### Post by ankit.vader on 2010-06-29
```
You will want to post this in the programming section and merge the two  post
```

sorry about posting it in wrong section. how can i merge posts?

---

### Post by surfer on 2010-06-29
something like
```
grep -o -e "\[.*\]" file.txt
```
?

---

### Post by justleen on 2010-06-29
sed would be more 'obfuscated' here
```
sed 's/.*\(\[.*\]\).*/\1/' file.txt
```

---

### Post by ankit.vader on 2010-06-29
```
grep -o -e "\[.*\]" file.txt
```

this worked thanks, now i can sleep :)

---

### Post by surfer on 2010-06-29
you are very welcome!

good night and good luck!

---

### Post by DaithiF on 2010-06-29
just to be really pedantic :) theres no need to escape ]'s

grep -o '\[.*]' testfile
sed -r 's/^.*(\[.*]).*$/\1/' testfile

---

### Post by surfer on 2010-06-30
i used the -e (regex) flag. if you do, you must escape the []s. but you're right, its easier without -e and escaped []s.

---

### Post by DaithiF on 2010-06-30
> **surfer said:**
> i used the -e (regex) flag. if you do, you must escape the []s. but you're right, its easier without -e and escaped []s.
umm no, you need to escape the [ character regardless of -e or not.  And you don't need to escape the ] character either way.  I was just pointing out that people often escape ] as well as [, in the mistaken belief that otherwise ] is interpreted as the end of a character-class set rather than as a literal ].  But in fact the regex engine is smart enough to treat ] as a literal when there hasn't been a [ to start a character-class.  So one less character to type.  hardly world-changing, but just thought I'd mention it.

---

### Post by justleen on 2010-06-30
> **DaithiF said:**
> umm no, you need to escape the [ character regardless of -e or not.  And you don't need to escape the ] character either way.  I was just pointing out that people often escape ] as well as [, in the mistaken belief that otherwise ] is interpreted as the end of a character-class set rather than as a literal ].  But in fact the regex engine is smart enough to treat ] as a literal when there hasn't been a [ to start a character-class.  So one less character to type.  hardly world-changing, but just thought I'd mention it.


Have you tried this??
Cauz you most definitly need to match de \'s on both opening and closing (square) brackets. Sed _will_ complain on unmatched ])'s...

---

### Post by DaithiF on 2010-06-30
> 
Have you tried this??
Cauz you most definitly need to match de \'s on both opening and closing (square) brackets. Sed _will_ complain on unmatched ])'s...

Not for me it doesn't:
```
$ sed 's/^.*\(\[.*]\).*$/\1/' testfile
[1:4, 2:5, 3:6]

$ sed 's/^.*\(\[.*\]\).*$/\1/' testfile
[1:4, 2:5, 3:6]

$ sed --version
GNU sed version 4.1.5

```

---

### Post by justleen on 2010-06-30
*blush*

I remove the slash in the grouping brackets... \(  \) 


/me goes of to find a corner to sit in...

---

