---
title: "Compare Two Files for Duplicate Lines"
date: 2011-02-15
forum: General Help
---

### Post by mastermindg on 2011-02-15
I referenced this post before addressing this question:

[http://ubuntuforums.org/showthread.php?t=977081&highlight=Compare+Files](http://ubuntuforums.org/showthread.php?t=977081&highlight=Compare+Files)

...however, the command that was given is giving me the following output:


$ cat file1.txt | sed s/\"//g |awk -F\- '{print "grep "$2 " file2.txt"}' | sh >> dups.txt
: No such file or directory
: No such file or directory
: No such file or directory
: No such file or directory
sh: gre: not found

Both files exist and dups.txt is created but is repeating these lines:

grep  file2.txt
grep  file1.txt

I need a command that will output duplicate lines between the two files.

Thanks,

KJ

---

### Post by mastermindg on 2011-02-15
Found it...

a nice one liner from awk. A whole lot easier than the sed equivalent.

sort file1.txt file2.txt | awk 'seen[$0]++ == 1' > dups.txt

---

### Post by Habitual on 2011-02-15
+1 for finding it on your own!

Props.

---

### Post by asmoore82 on 2011-02-15
Wow, there's a lot of the long way 'round in that thread.

```
cat file1.txt | sort > test.1
cat file2.txt | sort > test.2

comm -23 test.1 test.2 > only-file1.txt
comm -13 test.1 test.2 > only-file2.txt
comm -12 test.1 test.2 > dups.txt
```

"an elegant weapon for a more civilized age" ~ Obi-Wan Kenobi

I hesitate to call another solution *wrong*, but they aren't quite *right*.

If it must be a one liner:
```
comm -12 <(sort file1.txt) <(sort file2.txt) > dups.txt
```

---

