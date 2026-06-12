---
title: "Read a file and save a parameter as variable"
date: 2012-06-19
forum: General Help
---

### Post by sd@ksu on 2012-06-19
I have a file with data. Each data-set have a line of this format at the beginning:
[HTML]#S number[/HTML]

where the number is changing from 1, 2, 3, etc till as big as I want. I want to read the last number, and save as a variable and then pass to other parts of a code.
I am using :
```
grep \#S address_to_file_path|tail -1| tail -c +4
```

This prints out the last number after the last occurance of #S in that file to my bash window. But I am unable to save it as a variable. Can someone shed some light onto it. Thanks in advance.

---

### Post by matt_symes on 2012-06-19
Hi

Does this get you nearer ?

```
last_num=$(grep \#S address_to_file_path|tail -1| tail -c +4);
```

```
echo "$last_num";
```

Kind regards

---

### Post by SeijiSensei on 2012-06-19
I'd use awk for the second part myself:

```
NUM=$(grep \#S address_to_file_path | awk '{print $2}')
```

There are a couple of niceties that you might want to consider.  You could use "^\#S" to guarantee you only pull lines where "#S" starts at the beginning of the line.  Also, what happens if some lines have multiple spaces between the "#S" and the number?  To protect against both of these problems you could use 

```
NUM=$(grep ^\#S /path/to/file | sed -r 's/[[:space:]+]/ /g' | awk '{print $2}')
```

The sed command collapses multiple spaces into one.

---

### Post by sd@ksu on 2012-06-19
Thanks to both of you. Should have used $(). My bad. :-)

---

### Post by HiImTye on 2012-06-19
I always prefer sed but everyone prefers a different parsing tool
```
 number=$(tail -1 /path/to/file | sed 's|.*\([0-9]*\)$|\1|')
```

---

