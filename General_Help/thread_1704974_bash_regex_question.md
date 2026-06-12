---
title: "bash regex question"
date: 2011-03-11
forum: General Help
---

### Post by motoperpetuo on 2011-03-11
i'm trying to search through the "rejects" log file from a user import i recently did into LDAP. i want to extract just the uid values. here are some examples of these values:

uid=abc123456
uid=5656890
uid=GHT90043

the lengths of a uid value can vary from about six to maybe eleven characters, always comprised either of all digits, or three letters (upper or lower case) followed by digits. the uid value is always followed by a comma in the "rejects" file.

i tried this command:
```

cat rejects | grep -o uid=[a-zA-Z0-9]+\b

```

my logic is "find 'uid=' followed by one or more alphanumeric characters, to the end of the word." unfortunately, it returns nothing. if i shorten this to 
```

cat rejects | grep -o uid=[a-zA-Z0-9]

```
it returns output that looks like this:
```

uid=7
uid=H
uid=1
uid=1
uid=n

```
so, i'm guessing that my problem is with the '+\b' on the end of the expression. does anyone see what i'm doing wrong here. the + regex seems very useful, i guess i just don't know how to make it actually work.

---

### Post by gmargo on 2011-03-11
You need to escape the plus:
```

$ cat rejects | grep -o 'uid=[a-zA-Z0-9]\+'
uid=abc123456
uid=5656890
uid=GHT90043

```You can pipe that into sed to remove the uid= part.

---

### Post by TeoBigusGeekus on 2011-03-11
Try with
```
grep -o uid=[a-zA-Z0-9]* rejects
```

---

### Post by sisco311 on 2011-03-11
You should never pipe cat into grep or any other program.

Wrong: **cat file | grep PATTERN**
Correct: **grep PATTERN file**

Wrong: **cat file | tr '\t' '\n'** 
Correct: **tr '\t' '\n' < file**

Instead of [a-zA-Z0-9] use [[:alnum:]], which doesn't depend on the C locale and character encoding. 

And as gmargo pointed it out, you have to escape +:
```
grep -o 'uid=[[:alnum:]]\+' rejects
```

Or use **egrep** or **grep -E**:
```
grep -E -o 'uid=[[:alnum:]]+' rejects
```

For more info, check out the relevant section from grep's man page:
```
man grep | less +/"REGULAR EXPRESSIONS"
```

---

### Post by motoperpetuo on 2011-03-11
awesome, any number of those replies worked. thanks very much to those who responded.

about never piping cat into another program, is that just because it's unnecessary, or is there something else bad about doing it that way?

---

### Post by Telengard C64 on 2011-03-11
> **sisco311 said:**
> You should never pipe cat into grep or any other program.

Wrong: **cat file | grep PATTERN**
Correct: **grep PATTERN file**

Wrong: **cat file | tr '\t' '\n'** 
Correct: **tr '\t' '\n' < file**


I used to do this kind of thing too, but sisco311 is correct. I can't think of a single instance where it is truly necessary to pipe the output of **cat** into anything. When you find yourself doing it you should pause and ask yourself, "Is there a better way?"

[list]
[*]It invokes an extra unnecessary process which makes your code wasteful with resources.
[*]It just looks foolish. Read the man pages of programs you might want to pipe the output of **cat** into. Many of them accept a file name argument from which to take their input. For those that don't you can follow sisco311's example by redirecting the program's stdin from a file.
[*][http://en.wikipedia.org/wiki/Cat_%28Unix%29#Useless_use_of_cat](http://en.wikipedia.org/wiki/Cat_%28Unix%29#Useless_use_of_cat)
[*][http://www.iki.fi/era/unix/award.html](http://www.iki.fi/era/unix/award.html)
[/list]

---

### Post by gmargo on 2011-03-11
> about never piping cat into another program, is that just because it's unnecessary, or is there something else bad about doing it that way?"because it's unnecessary" in this specific case.  There's nothing wrong with using **cat(1)**.  It's a tool and you're allowed to use it, no matter how it "looks".  It's likely you were debugging a longer pipeline anyway.

---

### Post by AlphaLexman on 2011-03-11
@ motoperpetuo:

It is IMO just a beginner's logic/mistake. It still works the same, there is just a better way to do it.

**For instance:**

The human brain wants to see the entire file (cat) and then search (grep) for what they are looking for.

**However:**

A computer/machine can do both at the same time.

Regards.

---

