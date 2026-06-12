---
title: "bash help"
date: 2009-09-02
forum: General Help
---

### Post by prem1er on 2009-09-02
I need to read part of a huge file from a specific line # that I used 'cat -n' to find.  How would I start my loop at that specific line number?  Thanks.

---

### Post by DaithiF on 2009-09-02
one way:
```
sed -n 'X,$p' | while read line
do
   echo $line
   # do other stuff with $line here
done

```

where X is the line number you want to start from

---

### Post by asmoore82 on 2009-09-02
I'm not sure what you mean by "start my loop,"
but the `head` and `tail` commands are for trimming by line numbers.

to see only the first 5 lines:
```
head -n 5 *filename*
```
to see only the last 6 lines:
```
tail -n 6 *filename*
```
to see only line 7 through the end:
```
tail -n +7 *filename*
```

the commands are also pipe-able; to see the last 10 lines:
```
cat *filename* | tail
```

to see 6 lines starting at line #12:
```
cat *filename* | tail -n +12 | head -n 6
```

---

### Post by aeiah on 2009-09-02
```

tail -n+# file.name

```

will read everything from # to the end of the file. or did you just want a chunk of text starting at line #?

---

### Post by aeiah on 2009-09-02
bah. beaten :(

---

### Post by prem1er on 2009-09-02
Ok, I think you answered my question but I am still not sure.  Here is what I have.

```
cat -n $1 | grep "BACKPAGE" | tail
```

I need to read line by line after the first instance of "BACKPAGE"

---

### Post by asmoore82 on 2009-09-02
If you are doing this interactively, you can use the `less` command:

while in `less`,
you can use arrow keys to scroll up/down/left/right
hit '/' to search for text
hit 'q' to quit `less`

so...
```
less *filename*
/BACKPAGE

```

If you need to do this in a script, maybe something like...
```
startline=$( cat -n *filename* | grep BACKPAGE | head -n 1 | cut -f1 )
tail -n "+$startline" *filename*
```

---

### Post by prem1er on 2009-09-02
Edit: I'm working through this now. Thanks for the responses. I'll let you know if I have another problem.

---

### Post by asmoore82 on 2009-09-02
it's a whitespace problem, this is the corrected version:
```
startline=$( cat -n filename | grep BACKPAGE | head -n 1 | cut -f1 )
startline=$( echo $startline ) [COLOR="Blue"]#intentional missing "..." to eat whitespace[/COLOR]
tail -n "+$startline" filename
```

---

### Post by DaithiF on 2009-09-02
or
```
sed -n '/BACKPAGE/,$p' filename
```

---

