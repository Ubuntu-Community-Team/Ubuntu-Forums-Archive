---
title: "command for data difference between two files"
date: 2011-03-17
forum: General Help
---

### Post by trojanworrier on 2011-03-17
Hi,

I'm looking for command for following requirement:

file A has all data
file B has a part of data (little be missing)

how do I find out which data is missing from file B compare to file A?

i.e. file A and file B are zone files. and they have zone/domain name listed in each new line. so how do I find out which domain names are missing from file B compare to file A

---

### Post by varunendra on 2011-03-18
Looks like "diff" or "fc" commands are your solutions.

Description with examples:- 
**Diff:**
[http://lowfatlinux.com/linux-compare-files-diff.html](http://lowfatlinux.com/linux-compare-files-diff.html)
[http://www.cyberciti.biz/faq/how-do-i-compare-two-files-under-linux-or-unix/](http://www.cyberciti.biz/faq/how-do-i-compare-two-files-under-linux-or-unix/)

**FC:**
[http://ss64.com/nt/fc.html](http://ss64.com/nt/fc.html)

---

### Post by seawolf167 on 2011-03-18
As previously noted, use *diff*

```
man diff
```

ex.

```
diff file1 fil2
```

---

### Post by engine on 2011-06-17
As far as I understand, diff runs a line-by-line comparison: so if line 14 in file A is not the same as line 14 in file B, this will be identified as a difference even though the content of line A:14 shows up as B:17

I'm not sure this is the most efficient way of comparing two lists, where what you want to see is a report showing the lines present in A and not in B.

Any ideas?

---

### Post by amauk on 2011-06-17
If you want a GUI app, try "meld"

---

### Post by engine on 2011-06-17
Interesting app, indeed; thanks for mentioning it! but still doing a line-by-line comparison rather than scanning the complete content.

---

### Post by erind on 2011-06-17
> **engine said:**
> As far as I understand, diff runs a line-by-line comparison: so if line 14 in file A is not the same as line 14 in file B, this will be identified as a difference even though the content of line A:14 shows up as B:17

I'm not sure this is the most efficient way of comparing two lists, where what you want to see is a report showing the lines present in A and not in B.

Any ideas?

 You can try something like this:

[ EDIT: *Updated code*.  In some cases where the second file has the same repeating records found also in the first file, the older code would erroneously print these repeating lines as being unique to the second file only. The updated code will take that into account ]

 ```
awk 'FNR==NR { a[$0]; f1=FILENAME; next }
     !($0 in a) { print "Record only in " FILENAME " >> " $0; next } { b[$0] }
     END { for( rec in a ) if(!( rec in b )) print "Record only in " f1 " -> " rec }' file1 file2
```And testing it:

```
$ cat file1
aaaa
bbbb
cccc
dddd
$ cat file2
cccc
dddd
xxxx
cccc

$ awk 'FNR==NR { a[$0]; f1=FILENAME; next }
       !($0 in a) { print "Record only in " FILENAME " >> " $0; next } { b[$0] }
       END { for( rec in a ) if(!( rec in b )) print "Record only in " f1 " -> " rec }' file1 file2
Record only in file2 >> xxxx
Record only in file1 -> bbbb
Record only in file1 -> aaaa
```_____
Below is the older code, but for correct results use the code above.

```
   awk 'FNR==NR { a[$0]; f1=FILENAME; next }
        ($0 in a) { delete a[$0]; next }
        { print "Record only in " FILENAME " >> " $0 }
        END { for( rec in a ) print "Record only in " f1 " -> " rec }' file1 file2

```

---

### Post by MondoTofu on 2011-06-17
Meld has my vote.

---

### Post by engine on 2011-06-18
Serious-looking stuff! thanks very much; I'll let it loose on some sample files.

---

### Post by SACHINVD on 2011-06-18
you can use diff command or you can use winmerge tool.

---

