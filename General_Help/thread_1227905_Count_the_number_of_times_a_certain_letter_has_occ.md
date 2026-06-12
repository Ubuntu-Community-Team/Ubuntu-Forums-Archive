---
title: "Count the number of times a certain letter has occurred in a text file"
date: 2009-07-31
forum: General Help
---

### Post by lethalfang on 2009-07-31
As the title suggests, what command(s) should I use to count the number of times the letter "A" has occurred in a text document?
I'm looking a bunch of text files containing DNA sequences, and I need to know how many A, T, C, and G's are there.

Thanks in advance.

---

### Post by megamania on 2009-07-31
> **lethalfang said:**
> As the title suggests, what command(s) should I use to count the number of times the letter "A" has occurred in a text document?
I'm looking a bunch of text files containing DNA sequences, and I need to know how many A, T, C, and G's are there.

Thanks in advance.
A quick-and-dirty solution is to use a text editor and do a "find". Most editors will return the number of occurrences.

---

### Post by The Cog on 2009-07-31
Try this:
Put this in a text file called **atcgcount** with an editor:
```
#!/usr/bin/env python

import sys

if len(sys.argv) < 2:
    print "Count the number of 'A', 'T', 'C', 'G' in a file"
    print "usage: %s <filename>"
    sys.exit(1)

chars = "ATCG"
counts = {"A":0, "T":0, "C":0, "G":0}

fname = sys.argv[1]
f = open(fname)
for char in f.read():
    if char in chars:
        counts[char] += 1
f.close()
print "A:", counts["A"]
print "T:", counts["T"]
print "C:", counts["C"]
print "G:", counts["G"]

```
and make the file executable with the command **chmod +x atcgcount** and run it with the command: **./atcgcount filename** to count a files characters.

---

### Post by SPr on 2009-07-31
```

grep --count A dna_text_file.txt

```
Substitute A for the other letters.
From the manual:
```

-f FILE, --file=FILE
              Obtain patterns  from  FILE,  one  per  line.   The  empty  file
              contains  zero  patterns, and therefore matches nothing.  (-f is
              specified by POSIX.)

```
if you're feeling lazy.

Sorry, I'm not thinking. That only counts the number of lines.

---

### Post by SPr on 2009-07-31
```

cat dna_file.txt|sed s/[^A]//g|wc -m

```
is the closest I can get but it is always needs one taking away from the result to give the true answer.

Edit: I knew it was possible :)
```

cat dna_file.txt|sed s/[^A]/\ /g|wc -w

```
Replace everything in dna_file.txt that isn't an "A" with a space and wc will count the correct number of words.
Of course [^A] will need replacing with [^T] etc.
Damn, it's still wrong. It must be possible to do this without using a script. This has turned into a challenge.

Edit2:
```

cat dna_file.txt|sed s/[^A]//g|tr -d "\n"|wc -m

```
It's ungainly but it works (until I find another error :( )

---

### Post by Numbski on 2009-07-31
> **lethalfang said:**
> As the title suggests, what command(s) should I use to count the number of times the letter "A" has occurred in a text document?
I'm looking a bunch of text files containing DNA sequences, and I need to know how many A, T, C, and G's are there.

Thanks in advance.

cat file.txt | grep -c "A"

---

### Post by lswb on 2009-07-31
Not pretty but this will work:

grep -o 'A' filename.txt|wc -l

---

### Post by SPr on 2009-07-31
> **lswb said:**
> Not pretty but this will work:

grep -o 'A' filename.txt|wc -l

That's the winner.

---

### Post by lethalfang on 2009-08-01
> **SPr said:**
> That's the winner.

It is. Thanks! :-)

---

### Post by Numbski on 2009-08-04
Bah, I forgot that -c counts lines, not actual occurences.  Sorry about that.

I was thinking you could just simply do grep -c 'A' filename.txt, but that's not quite right.  Good on the guy that went to the trouble of looking into it specifically. :P

---

