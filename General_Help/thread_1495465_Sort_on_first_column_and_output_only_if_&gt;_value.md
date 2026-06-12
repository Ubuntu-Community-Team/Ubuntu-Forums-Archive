---
title: "Sort on first column and output only if &gt; value"
date: 2010-05-28
forum: General Help
---

### Post by dragos2 on 2010-05-28
I have a file and I wanted to list word frequencies like this:
```

cat file | sort | uniq -c | sort -nr

```

How can I output only the lines that appears more than once using sort ?

---

### Post by StuartN on 2010-05-28
> **dragos2 said:**
> I have a file and I wanted to list word frequencies like this:
```

cat file | sort | uniq -c | sort -nr

```

How can I output only the lines that appears more than once using sort ?

This will read test.txt and output the words in it that appear more than once:

```
grep -o "[a-zA-Z0-9\_\'-]\+" test.txt | sort | uniq -c | sort -nr | while read count word ; do if [ "$count" -gt 1 ] ; then echo "<$count> $word" ; fi ; done
```

---

### Post by dragos2 on 2010-05-28
> **StuartN said:**
> This will read test.txt and output the words in it that appear more than once:

```
grep -o "[a-zA-Z0-9\_\'-]\+" test.txt | sort | uniq -c | sort -nr | while read count word ; do if [ "$count" -gt 1 ] ; then echo "<$count> $word" ; fi ; done
```

Thanks a lot :)

Can this be made faster ?
```

 while read count word ; do if [ "$count" -gt 1 ] ; then echo "<$count> $word" ; fi ; done

```

---

### Post by StuartN on 2010-05-29
> **dragos2 said:**
> Can this be made faster ?

There does not seem to be much fat to trim, but **head** might be quicker if the greater than one condition is approximate, rather than absolute - e.g. if you were content with the top 100 words.

My machine only took 32 seconds to list every word used more than once by William Shakespeare. The same task ran overnight and into the next day back in 1995.

---

### Post by dragos2 on 2010-06-01
> **StuartN said:**
> There does not seem to be much fat to trim, but **head** might be quicker if the greater than one condition is approximate, rather than absolute - e.g. if you were content with the top 100 words.

My machine only took 32 seconds to list every word used more than once by William Shakespeare. The same task ran overnight and into the next day back in 1995.

Hmm, how much time for this:
```

grep -o "[a-zA-Z0-9\_\'-]\+" test.txt | sort | uniq -c | sort -nr | awk ' $1 > 1 '

```

?

---

### Post by StuartN on 2010-06-01
> **dragos2 said:**
> ```
grep -o "[a-zA-Z0-9\_\'-]\+" test.txt | sort | uniq -c | sort -nr | awk ' $1 > 1 '
```

I have just rebooted, and I get 14.8 seconds for the first and 11.6 for the second, so it is 22% faster.

It is very impressive for 900,000 occurrences of 19,000 unique words in a 5.3 MB plain text file.

I have written a program in C for word analysis ([http://www.iol.ie/~stuartneilson/projects/](http://www.iol.ie/~stuartneilson/projects/)) which is massively slower, but I still use it for convenience when handling multiple files - e.g. comparing word frequencies between two versions of a website (*dehtml.sh Revised/*.html | wordlist -rank > Revised_rank.txt && dehtml.sh Original/*.html | wordlist -rank > Original_rank.txt*). It also does Boolean set operations, like *wordlist test.txt NOT English.txt* is a simple spell checker.

---

