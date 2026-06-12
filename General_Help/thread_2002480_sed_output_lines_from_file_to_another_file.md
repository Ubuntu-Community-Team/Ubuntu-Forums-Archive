---
title: "sed output lines from file to another file"
date: 2012-06-12
forum: General Help
---

### Post by spiritech on 2012-06-12
how can i tell sed to replace the end of each line with a line from another file. so copy line 1 from read file to end of line 1 of input file, and so on for each line.

my code so far

sed -r 's/$/         /g' input

spiritech

---

### Post by steeldriver on 2012-06-12
sounds like a job for 'paste' not 'sed'

[http://www.techrepublic.com/article/lesser-known-linux-commands-join-paste-and-sort/5031653](http://www.techrepublic.com/article/lesser-known-linux-commands-join-paste-and-sort/5031653)

---

### Post by bodhi.zazen on 2012-06-12
I would use awk or perl

---

### Post by Vaphell on 2012-06-12
what about
```
while read -r -u3 l1; read -r -u4 l2; do echo "${l1}${l2}"; done 3< file1.txt 4< file2.txt
```

---

### Post by steeldriver on 2012-06-12
```

$ paste file1 file2               # append lines - separate with tabs (default)
file 1 line 1    file 2 line 1
file 1 line 2    file 2 line 2
file 1 line 3    file 2 line 3
    
$ paste -d ' ' file1 file2       # append lines - separate with single space
file 1 line 1 file 2 line 1
file 1 line 2 file 2 line 2
file 1 line 3 file 2 line 3
 
$ paste -d '\n' file1 file2       # interleave lines
file 1 line 1
file 2 line 1
file 1 line 2
file 2 line 2
file 1 line 3
file 2 line 3

```

---

### Post by spiritech on 2012-10-01
> **steeldriver said:**
> sounds like a job for 'paste' not 'sed'

[http://www.techrepublic.com/article/lesser-known-linux-commands-join-paste-and-sort/5031653](http://www.techrepublic.com/article/lesser-known-linux-commands-join-paste-and-sort/5031653)

thankyou this does what i need

---

