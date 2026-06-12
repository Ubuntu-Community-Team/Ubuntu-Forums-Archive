---
title: "help with sed/grep/awk"
date: 2011-08-24
forum: General Help
---

### Post by Avidanborisov on 2011-08-24
I need to use sed or grep or awk (or any other that can achieve this task) to scan stdout for smart single quotes like this:
```
&#8216;&#8217;
```
and replace it with regular single quote like this:
```
'
```
and in the end pipe back to stdout.
I tried doing this myself but bash gave me errors. Any Ideas?

---

### Post by WorMzy on 2011-08-24
```
[COLOR="Red"]previous command[/COLOR] | sed "s/&#8216;&#8217;/'/g"
```

EDIT: changed slightly, should have tested before I posted

---

### Post by Avidanborisov on 2011-08-24
I get:

2: Syntax error: Unterminated quoted string

---

### Post by WorMzy on 2011-08-24
I edited my post shortly after posting due to that. You shouldn't get it with the updated command.

And I just noticed that I hadn't updated the closing quote mark.

---

### Post by sisco311 on 2011-08-24
```
sed 's/&#8216;&#8217;/'\''/g'
```

---

### Post by Avidanborisov on 2011-08-24
Tried your updated suggestion, still the same error.

EDIT:
sisco311, thank you! your suggestion works!

---

### Post by WorMzy on 2011-08-24
Yeah, I'm not doing very well here, haha. :redface:

I didn't even notice that the "smart quotes" were different to apostrophes. Now that I've taken the time to understand the situation, I just need to check one thing: are the smart quotes around text? If so, this should do the trick:

```
sed "s/‘\(.*\)’/'\1'/g"
```

---

### Post by Avidanborisov on 2011-08-24
Actually I used sisco331 solution (and chaged it a bit) so now it looks like this:
```
| sed 's/&#8216;/'\''/g' | sed 's/&#8217;/'\''/g' |
```

---

### Post by sisco311 on 2011-08-24
> **Avidanborisov said:**
> Actually I used sisco331 solution (and chaged it a bit) so now it looks like this:
```
| sed 's/&#8216;/'\''/g' | sed 's/&#8217;/'\''/g' |
```

You don't need to use two sed commands. The g at the end of the command means: replace all instances in a line.

---

### Post by Vaphell on 2011-08-24
probably he couldn't figure out how to do replace &#8216;-or-&#8217; at once so he did it in two steps

OP, try this
```
echo &#8216;omg&#8217; wtf &#8216;bbq&#8217; | sed 's/[&#8216;&#8217;]/'\''/g'
'omg' wtf 'bbq'
```

---

### Post by Avidanborisov on 2011-08-24
^ Thanks for the improvement!

EDIT:

if already talking about improvements, this was a part from a this large command:

```
xsel -bo | egrep -v "^([0-9]*):( $|$)" | sed 's/^[0-9]*://; s/^ //' | sed -r 's/[&#8220;&#8221;]/"/g' | sed 's/[&#8216;&#8217;]/'\''/g' | xsel -bi
```

if anyone knows how to improve it, I will be thankful!

---

### Post by Vaphell on 2011-08-25
to replace all types of quotes at once
```
echo &#8220;&#8221;&#8216;&#8217; | sed 'y/&#8220;&#8221;&#8216;&#8217;/""'\'\''/'
""''
```
first segment consists of chars to replace, second one has the chars that should be used instead.

```
egrep -v "^([0-9]*):( $|$)"
```
can be shortened to
```
egrep -v "^[0-9]+: *$"
```
? = 0-or-1, + = 1-or-more, * = 0-or-more
i changed * to + (at least 1 digit) and simplified the alternative of ' $'-or-'$' using *.

```
sed 's/^[0-9]*://; s/^ //'
```
you can trim both line number and spaces at once
```
sed -r 's/^[0-9]+: *//'
```

---

