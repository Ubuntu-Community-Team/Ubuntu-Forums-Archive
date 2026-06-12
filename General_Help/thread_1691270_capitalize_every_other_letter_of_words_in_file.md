---
title: "capitalize every other letter of words in file"
date: 2011-02-19
forum: General Help
---

### Post by d3v1150m471c on 2011-02-19
i have this file, and considering it's obnoxiously huge i'd prefer not to have to do this manually. Is there some way i can manipulate sed or awk to change every other letter in all the words in a file to capital letters? IE:
pizza
pinball
poncho

would become...

PiZzA
PiNbAlL
PoNcHo

---

### Post by gmargo on 2011-02-19
```

$ echo -e "pizza\npinball\nponcho" | perl -p -e 's/(.)(.)?/\u$1$2/g'
PiZzA
PiNbAlL
PoNcHo

``````

$ echo -e "pizza\npinball\nponcho" | sed 's/\(.\)\(.\)\?/\u\1\2/g'
PiZzA
PiNbAlL
PoNcHo

```

---

### Post by idi0tf0wl on 2011-02-19
Is the file itself laid out like that (i.e. word-newline-word-newline)? If so just pipe the output of cat file.type to the command above and that should do it. If you're changing a paragraph of written text, you'll want to look for a regex somewhere along the lines of "^[\w]*[ ]", "[ ][\w]*[ ]", and "[ ][\w]*[\n] and then implement something similar with each matched (and trimmed) pattern.

---

### Post by d3v1150m471c on 2011-02-19
that's awesome. thanks guys

---

### Post by d3v1150m471c on 2011-03-22
would anyone know how to do this with a python string as well? ie:

```

MyString = "something"
MyString = MyString.replace(r'(some regex)', r'(replace regex)')
print MyString
# desired output : SoMeThInG

```

---

### Post by gmargo on 2011-03-22
I think "string.replace()" is only for fixed strings.

Anyway, here's an embarrassingly crude method.  There's probably a better way. Python doesn't seem to support the "\u" modifier that worked for Perl and Sed.

```

#!/usr/bin/python

import re

def alt2(S):
    global up
    if up == 0:
        a = S.group().upper()
    else:
        a = S.group()
    up ^= 1
    return a

for b in [ "pizza", "pinball", "poncho" ]:
    up = 0
    a = re.sub(r'(.)', alt2, b)
    print a

``````

$ python altcap2.py 
PiZzA
PiNbAlL
PoNcHo



```

Edit:
For a single character match, a regular expression is a waste; this works too:
```

for b in [ "pizza", "pinball", "poncho" ]:
    up = 0
    a = ""
    for let in b:
        if up == 0:
            a += let.upper()
        else:
            a += let
        up ^= 1
    print a

```

---

### Post by d3v1150m471c on 2011-03-22
i have several items in an array that i've piped into it via reading lines from a file. i'm gonna give this a whirl with some of the snippets you posted and i'll let you know how it turns out. thanks for the reply.

---

### Post by d3v1150m471c on 2011-03-22
```

ReadWords = open(wordlist, 'r')
for line in ReadWords:
     line = line.replace('\n', '')
     up = 0
     a = ""
     for let in line:
         if up == 0:
             a += let.upper()
         else:
             a += let
         up ^= 1
     print a

```

Works like a charm. I'm gonna play around with this some more and see what other neat word mangling i can come up with. Thanks!

---

