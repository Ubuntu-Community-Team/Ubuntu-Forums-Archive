---
title: "Regular Expressions wildcard question"
date: 2011-07-01
forum: General Help
---

### Post by jhargis1012 on 2011-07-01
Hi there. I'm trying to become familiar with the commandline (self-studying with a book) and ran into something that confused me. If I understand this correctly, the asterisk (*) functions as a repetition indicator and the period (.) functions as a wild card for any character in regular expressions. So, for example, a.*b would be anything with "a" in the beginning and "b" at the end.

Despite this, in various locations I am seeing the * representing any number of any characters by itself, without the period preceeding it (as in *.conf). How do you tell if a program (or any other situation) uses regular expressions (necessitating the period before the star) or just plain asterisks for wildcards?

Thanks for any clarification.

---

### Post by nothingspecial on 2011-07-01
Let me say first that I stand to be corrected on this. This is my understanding only......

bash and regex handle a * differently.

regex interprets the * as none or more occurrences of the proceeding character so, in regex .* means any string of any length comprised of any characters. The * needs a proceeding character to act upon.

bash, however interprets the * as .* (in a regex), because . has a different meaning in bash - the current working directory.

I would like to be informed wether or not I am right about this.

---

### Post by sisco311 on 2011-07-01
Yes nothingspecial, you are right.

Globs and regular expressions are well explained at [Greg's Wiki]("http://mywiki.wooledge.org/"):
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)
[http://mywiki.wooledge.org/RegularExpression](http://mywiki.wooledge.org/RegularExpression)

---

### Post by jhargis1012 on 2011-07-01
Thanks for the response.

That wiki was helpful as well. Thank you.

---

### Post by nothingspecial on 2011-07-01
$ cat b.txt 
adfrbhyu
dsfajubhy
bghya
ahgftb
afgtb
gdfrajuyb
okhgbtga
ajhb
$ grep **a*b b.txt** 
adfrbhyu
dsfajubhy
bghya
ahgftb
afgtb
gdfrajuyb
okhgbtga
ajhb
$ **grep a.*b b.txt** 
adfrbhyu
dsfajubhy
ahgftb
afgtb
gdfrajuyb
ajhb
$ **grep ^a.*b b.txt** 
adfrbhyu
ahgftb
afgtb
ajhb


notice the ^ anchors the a to the beginning.

---

### Post by jhargis1012 on 2011-07-01
> **nothingspecial said:**
> $ cat b.txt 
adfrbhyu
dsfajubhy
bghya
ahgftb
afgtb
gdfrajuyb
okhgbtga
ajhb
$ grep **a*b b.txt** 
adfrbhyu
dsfajubhy
bghya
ahgftb
afgtb
gdfrajuyb
okhgbtga
ajhb
$ **grep a.*b b.txt** 
adfrbhyu
dsfajubhy
ahgftb
afgtb
gdfrajuyb
ajhb
$ grep ^a.*b b.txt 
adfrbhyu
ahgftb
afgtb
ajhb

Okay, now that doesn't make sense to me. Why did grep return "okhgbtga" for a*b but not for a.*b?

---

### Post by sisco311 on 2011-07-01
> **jhargis1012 said:**
> Okay, now that doesn't make sense to me. Why did grep return "okhgbtga" for a*b but not for a.*b?

The asterisk indicates there are **zero** or more of the preceding element. So a*b matches "b", "ab", "aab", "aaab" and so on.

---

### Post by sisco311 on 2011-07-01
Oh, and the regular expression must be interpreted by the command (grep) and not the shell, so you have to quote it in single quotes otherwise  the shell will try to expand it:
```
sisco@acme:~/xtmp$ cat file 
aaaabbbbb
axyzzzzzb

sisco@acme:~/xtmp$ > assssb
sisco@acme:~/xtmp$ grep a*b file
sisco@acme:~/xtmp$ grep 'a*b' file
aaaabbbbb
axyzzzzzb

```

---

### Post by jhargis1012 on 2011-07-27
Thanks for the help!

---

### Post by sisco311 on 2011-07-27
You're welcome!

---

