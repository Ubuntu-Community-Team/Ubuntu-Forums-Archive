---
title: "A Linux puzzle"
date: 2010-08-30
forum: General Help
---

### Post by DanEnsign on 2010-08-30
Hi,

I just noticed a curious little Linux puzzle this morning:

When I do 'ls' in my current working directory, I get

densign@laptop:~/work
$ ls
C_129.in  C_161.in  C_193.in  C_225.in  C_33.in  C_65.in  C_97.in  G_129.in  G_161.in  G_193.in  G_225.in  G_33.in  G_65.in  G_97.in

with no surprises whatsoever. The output shows up as one line on my maximized terminal window. However, when I pipe into wc, I get

densign@laptop:~/work
$ ls | wc -l
14

which is of course exactly what I want it to do; but what is wc counting when the output from ls alone appears on one line?

Perhaps, somehow, ls 'knows' that I'm piping its output to wc, and gives the output on 14 lines instead of on 1 line. Or is there some character that's not a newline to the terminal, but not a space, between each of the file names in the output of ls, that is newliney enough that wc knows to count them as newlines when using -l? 

Have a good morning,
Dan

---

### Post by spjackson on 2010-08-30
> **DanEnsign said:**
> 
Perhaps, somehow, ls 'knows' that I'm piping its output to wc, and gives the output on 14 lines instead of on 1 line. Or is there some character that's not a newline to the terminal, but not a space, between each of the file names in the output of ls, that is newliney enough that wc knows to count them as newlines when using -l? 

'ls' doesn't know that you are piping to wc, but it does know that the output is not to a terminal. It behaves differently when outputting to a disk file or pipe than it does when outputting to a terminal.

---

### Post by Vaphell on 2010-08-30
piped stuff is usually delimited even by spaces, while writing a script you can change that to newline with IFS='
'

try IFS=... and then ls | wc -l

---

### Post by DanEnsign on 2010-08-30
> **Vaphell said:**
> piped stuff is usually delimited even by spaces, while writing a script you can change that to newline with IFS='
'

try IFS=... and then ls | wc -l

Cool, I've never heard of IFS but that looks **really** useful. However, I'm not getting different behavior with ls | wc and IFS:

```
#!/bin/bash
vals='/var,/opt,/etc'

echo BEFORE
echo -n "ls | wc -l gives: "
ls | wc -l
echo dollar-sign-vals are: $vals
echo "loop gives:"
for i in $vals; do echo $i "is in the list" ; done
echo 

IFS=','
echo AFTER
echo -n "ls | wc -l gives: "
ls | wc -l
echo dollar-sign-vals are: $vals
echo "loop gives:"
for i in $vals; do echo $i "is in the list" ; done

unset IFS
```

Ouput:

```
densign@laptop:~/tmp
$ ./script.sh 
BEFORE
ls | wc -l gives: 20
dollar-sign-vals are: /var,/opt,/etc
loop gives:
/var,/opt,/etc is in the list

AFTER
ls | wc -l gives: 20
dollar-sign-vals are: /var /opt /etc
loop gives:
/var is in the list
/opt is in the list
/etc is in the list

```

It's very interesting that in the AFTER block "dollar-sign-vals" are listed without the commas, almost as if the variable is modified, rather than the delimiter!

Dan

---

### Post by DanEnsign on 2010-08-30
> **DanEnsign said:**
> It's very interesting that in the AFTER block "dollar-sign-vals" are listed without the commas, almost as if the variable is modified, rather than the delimiter!

The plot thickens, and I find that my hunch is wrong: when the variable contains what is ordinarily delimiter, the output is a little surprising:

```
densign@laptop:~/tmp
$ ./script.sh 
BEFORE
dollar-sign-vals are: /var,/opt directory,/etc
loop gives:
/var,/opt is in the list
directory,/etc is in the list

AFTER
dollar-sign-vals are: /var /opt directory /etc
loop gives:
/var is in the list
/opt directory is in the list
/etc is in the list
```

So is there some character that echo interprets as a space, but for interprets as a delimiter? 

Dan

---

### Post by Vaphell on 2010-08-30
why is it surprising?
/var,/opt directory,/etc delimited with default whitespace becomes '/var,/opt' + 'directory,/etc'
/var,/opt directory,/etc delimited with ',' becomes '/var'+'/opt directory'+'/etc'
and this is exactly what you get in the loops. Original string is intact, its logical analysis has changed

i guess i don't get your train of thought :-)

on a sidenote, there are some differences between sh and bash, i use sh and for what i've seen it treats newlines differently

---

### Post by DanEnsign on 2010-08-30
> **Vaphell said:**
> i guess i don't get your train of thought :-)

Sorry, my fault for not being clear.  :)

> why is it surprising?
/var,/opt directory,/etc delimited with default whitespace becomes '/var,/opt' + 'directory,/etc'
/var,/opt directory,/etc delimited with ',' becomes '/var'+'/opt directory'+'/etc'
and this is exactly what you get in the loops. Original string is intact, its logical analysis has changed

It's surprising because of the way echo uses IFS, compared to the way for uses it. With IFS=<default>, echo prints the commas; with IFS equal to ',', echo treats the commas as spaces (see "dollar-sign-vals are: /var /opt directory /etc" when the string is set to '/var,/opt directory,/etc' in the AFTER part of my last output). On the other hand, the for loop treats the string as advertized, splitting at space by default but by comma when IFS is ','. 

Tying this back into the original question, there seem to be delimiter characters that are treated differently in different contexts by bash. For instance IFS is used differently by echo than it is used by for. (Although I still can't get ls | wc -l to change its behavior with IFS.)

At first, I was mainly curious what these differences are precisely, but now I realize it could be useful knowledge to debug complex scripts ... although I think if things ever get that bad I'd use less time rewriting and debugging things in something more sensible than bash. :)

> on a sidenote, there are some differences between sh and bash, i use sh and for what i've seen it treats newlines differently

That is very useful to know, thank you.

Dan

---

### Post by Vaphell on 2010-08-30
oh, i looked at the output but failed to notice the difference in the line dollar-sign-vals are: ...
now i get it :)

---

### Post by Vaphell on 2010-08-30
```
IFS=','
echo AFTER
echo -n "ls | wc -l gives: "
ls | wc -l
echo dollar-sign-vals are: $vals
echo "dollar-sign-vals are: $vals"
echo dollar-sign-vals are: "$vals"

echo "loop gives:"
for i in $vals; do echo "$i" "is in the list" ; done

```

"" makes all the difference

---

