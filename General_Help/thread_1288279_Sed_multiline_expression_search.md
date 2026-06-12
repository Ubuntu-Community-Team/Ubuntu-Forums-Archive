---
title: "Sed multiline expression search"
date: 2009-10-11
forum: General Help
---

### Post by lofarkas on 2009-10-11
Hi everyone, I need some help with sed (or maybe grep can do it too)

I need to extract sections from a txt file, starting with a given character string and ending with another.

My source file looks like this:
string1 bla bla
bla bla string1
bla
bla
string2
blaa
string1

And I'd like 

string1
bla
bla
string2

to be the result from this section.

So, basically, I'm looking for lazy extraction of segments spread over several lines, based on starting and ending character strings, written into a new file.


Here's a page that discusses something along these lines, but I'm too daft to make sense of it: [http://www.ilfilosofo.com/blog/2008/04/26/sed-multi-line-search-and-replace/](http://www.ilfilosofo.com/blog/2008/04/26/sed-multi-line-search-and-replace/) 


Anyone?

---

### Post by geirha on 2009-10-11
This might be what you're after
```
sed -n '/string1/,/string2/p' file
```

---

### Post by lofarkas on 2009-10-11
I believe sed only searches one line by default, i.e. it has to be tricked into finding an expression that starts in one line and ends in another one further down. A simple command like that won't do.

---

### Post by geirha on 2009-10-11
Ah, sorry, I didn't read it carefully enough. You want the shortest matches? that is indeed more complex. I'll give it a try with my limited sed-knowledge.

---

### Post by lofarkas on 2009-10-11
Yes, ideally it should be lazy, i.e. exclude string1 from occurring inside the matched string.
It's also a 100MB file so I'm guessing the script needs to have some efficiency. Probably can't just load the entire file into the hold space.

---

### Post by geirha on 2009-10-11
This is the best my sed-knowledge lets me do. Not sure how to lose that empty line
```
sed -n ':a;/string1/{d;x;d;n;b a};H;/string2/{g;p}' sedtest.txt
```

If string1 is found, **d**elete pattern buffer, e**x**change buffers, and **d**elete again, then read **n**ext line and **b**ranch to label a. Basicly, when a line with string1 is found, loop until a line without string1 is found. Then we append (**H**) each line to the hold buffer until either string1 or string2 is found. If string2 is found, print the hold buffer.

EDIT: Ok try 2. The above will fill up the hold buffer also outside a string1-string2 block, which probably isn't very efficient, so maybe this will be better:

```
sed -n '/string1/,/string2/{:a;/string1/{d;x;d;n;b a};H;/string2/{g;p;d}}' sedtest.txt
```

---

### Post by lofarkas on 2009-10-14
Thank you, I'll check it out soon.
I've been very busy and didn't get to play with my linux 'puter...

---

