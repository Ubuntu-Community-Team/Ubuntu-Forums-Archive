---
title: "Comparing/filtering text files"
date: 2010-04-30
forum: General Help
---

### Post by anlag on 2010-04-30
I've got two files, which each consists of a list of unique strings, and with some differences. How can I conveniently (command line) get a list of what lines exist in both files? 

Say if file1.txt is:

abc100
abc101
abc102

And file2.txt is:

abc100
abc200
abc300

Then I would want an output of:

abc100

The closest I can think of is diff, but the files are different length and I can't get a reasonable output from it. If I could tell diff to require strict matching within each line, but otherwise ignore line numbers, that would be alright... couldn't find that in the man page though.

Did a temporary workaround in merging the file (cat), sorting them (sort) and just scrolling through with emacs deleting everything line that appears just once. Or vice versa, if I wanted the single hits only. Of course this feels much more cumbersome than it should have to be.

Any suggestions?

---

### Post by dino99 on 2010-04-30
open synaptic and search "duplicate", found fdupes, binstats, ohcount, maybe some others too, i'm never been concerned

wonder if some apps like openoffice writer can do that

---

### Post by anlag on 2010-04-30
Thanks for the tip, seems most of those programs do other things tough. fdupes works on comparing directories, binutils is something entirely different. I did however look around, and found two GUI programs that compare files: meld, and diffuse. Particularly the latter arranges things nicely, side by side, so it's easy to see what lines appear in both or one file. This does the job. However, I find no convenient method for getting the output. And command line would be preferable over GUI.

I suppose it would be a pretty quick job to just write a string matching script either in whatever shell, or in python, but it just feels like it's the kind of thing that already exists if one only knows where to find it. :-)

---

### Post by dino99 on 2010-04-30
better to post on the programming forum

maybe search: script+dupe

---

### Post by kaibob on 2010-04-30
I seem to recall that there is an easier way to do this, but it escapes me at the moment. In the meantime, the following does work:

```
comm -1 -2 <(sort file1) <(sort file2)
```

Using your example, but with file1 changed so that it is not in sorted order, the above command works as follows:

> $ cat file1
abc102
abc101
abc100

$ cat file2
abc100
abc200
abc300

$ comm -1 -2 <(sort file1) <(sort file2)
abc100

---

### Post by anlag on 2010-04-30
Perfect, that's exactly what I was looking for. Thanks a lot.

Minor detail: I get a syntax error near unexpected token '(' when running the command with sort on the same line.

> anlag@casper:~/Work/tmp$ comm -3 < (sort 95node.txt) < (sort 63node.txt)
bash: syntax error near unexpected token `('


Wouldn't mind a solution to that, also for general benefit of IO handling. But for the practical purpose, sorting separately before running comm is quite alright really.

---

### Post by dino99 on 2010-04-30
take care  of the space you have added

---

### Post by kaibob on 2010-04-30
> **dino99 said:**
> take care  of the space you have added
I agree with dino99. You have to remove the spaces between < and (.

---

