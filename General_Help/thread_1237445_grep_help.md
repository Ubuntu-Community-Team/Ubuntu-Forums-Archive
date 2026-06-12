---
title: "grep help"
date: 2009-08-11
forum: General Help
---

### Post by prem1er on 2009-08-11
I'm trying to learn grep, but stuck trying to pull information out of this line. I want to pull out all the information after the ":" symbol.  Thanks.

```
Updating citadel_mv: OLD_LONG_ACCT|00000007681050394SMP|NEW_ACCT_NO|00000007681050394|NEW_SHORT_ACCT|7681050394|NEW_SRC|PFD
```

---

### Post by VCoolio on 2009-08-11
Use [awk]("http://ss64.com/bash/awk.html") for that. Assuming the line is always starting with "Updating citadel" and that the string you want always consists of one word, add this to your command:
<yourcommand> | awk '{print $3}'

It prints the third element of the line. Read the link on awk if it is more complex than this.

---

### Post by jocko on 2009-08-11
I may be wrong, but I think grep can only show whole lines or the part of the lines that match the expression you look for. But you may be able to pipe it through another command, like sed.

Try something like this:
```
grep -i '[COLOR=Red]EXPRESSION1[/COLOR]' [COLOR=Blue]/path/to/file[/COLOR] | sed s/'[COLOR=Lime]EXPRESSION2[COLOR=black]'[/COLOR][/COLOR]//
```That should find all lines containing [COLOR=Red]EXPRESSION1[/COLOR] (the -i option makes grep case-insensitive, leave it out if you want it to be case sensitive) in the file [COLOR=Blue]/path/to/file[/COLOR], pipe the output to sed, which will remove every occurence of [COLOR=Lime]EXPRESSION2[/COLOR] and show you the result.

---

### Post by prem1er on 2009-08-11
Thanks for the replies, but my senior developer just happened to walk in and I got to ask him.  Here is his solution.

```
grep "|" ../log/citadel-cpi-fix.log | cut -d":" -f2 | sed 's/^ //g'
```

---

### Post by slakkie on 2009-08-11
cut -d\: -f 2 

is the same as

awk -F\: '{print $2}'

---

