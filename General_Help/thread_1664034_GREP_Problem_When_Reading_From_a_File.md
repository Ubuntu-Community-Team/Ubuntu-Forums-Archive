---
title: "GREP Problem When Reading From a File"
date: 2011-01-10
forum: General Help
---

### Post by Nosophorus on 2011-01-10
Hi!

I'm a Ubuntu 10.04 (Lucid Lynx) user and I'm having a problem when using grep and want to read a set of patterns from an ASCII file. The grep version installed in my machine is **GNU grep 2.5.4**.

For example, if I use the command

```
grep -f ./mypattern mydata.dat
```

grep outputs on the screen the whole "mydata.dat" and highlights the patterns in "mypattern". The image below shows what happens:

[IMG]http://img524.imageshack.us/img524/7035/capturadetelak.png[/IMG]

The red highlighted words are the patterns grep found and the black ones are the missing patterns (since they are not in "mypattern" file).

The problem is that I cannot send only the patterns in "mypattern" to another file (**grep -f ./mypattern mydata.dat > myfile.dat**), since it will send the whole data in "mydata.dat" to "myfile.dat".

I want to turn off that highlight feature in grep and show only the patterns inside a file when reading from a (pattern) file.

How could I do that?

Thank You!

---

### Post by DaithiF on 2011-01-10
Grep does what you want it to do ... which is to only output lines which match the pattern(s).  The problem (I suspect) is that you may have a blank line in your patterns file, which grep matches against all lines in your data file.

Once you remove the blank line you will only get matching lines in the output.

Also, I wasn't clear if you wanted to get the full lines in your output, or only the portion of each line that matched a pattern.  If the latter then use the -o flag:
```
       -o, --only-matching
              Print only the matched (non-empty)  parts  of  a  matching
              line, with each such part on a separate output line.

```

---

### Post by Nosophorus on 2011-01-10
Hi!

Thanks a lot for your reply!

You're right! The problem was a blank line in the pattern file. I removed and now everything is working fine.

I wanted the whole line and not only the matched pattern, since I need the numerical data to make statistical analysis. By the way, thank you very much for your hint!

Just another question: When I display a big ASCII file on the terminal screen, the output lags a lot to be displayed. It did not happen in Ubuntu 8.04 (Hardy Heron). Even using something like "cat myfile.dat | less" the same situation happens and pressing the up/down arrow only scrolls down a few lines and it is slow, whereas in Hardy Heron pressing those arrows would scroll fast and a nice amount of lines.

Would be there something I could do to solve that?

Thank You!

---

### Post by DaithiF on 2011-01-10
unlikely to be the cause of any discernible lag but theres no need to use cat for this, just use less:
```
less somefile
```

for scrolling, why not page through the data (ie. display one screenful at a time) rather than scroll line-by-line, so spacebar to page forward, b key to page back

---

### Post by Nosophorus on 2011-01-10
Hi!

Yeah, I do that to avoid the lagging problem. But I feel more comfortable using the key to individually see some data points.

By the way, thank you for your reply!

Thank You!

---

