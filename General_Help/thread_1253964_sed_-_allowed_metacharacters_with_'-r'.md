---
title: "sed - allowed metacharacters with '-r'?"
date: 2009-08-30
forum: General Help
---

### Post by itmozart on 2009-08-30
I'm looking for the metacharacter usable in sed regular expression, but seems like around the net there is no description.

this standard regex (I suppose it's perl syntax):

[FONT=Courier New]text    = 12345aaa~~
search  = (\d+).*
replace = \1
[/FONT]
returns 12345.

but sed doesn't support it, as the following:

[FONT=Courier New]echo '12345aaa~~' | sed -r 's/(\d+).*/\1/'[/FONT]

returns the entire string.

Now, I tried this:

[FONT=Courier New]echo '12345aaa~~' | sed -r 's/(\w+).*/\1/'[/FONT]

which works, but of course I need a digit wildcard.

So until now, I'm assuming that '\w' is supported, while '\d' isn't.
Is this true? Where can I find the specs for the supported regexes?

Thanks,
Saverio

---

### Post by DaithiF on 2009-08-31
Hi,
assuming GNU sed then:
[http://www.gnu.org/software/sed/manual/sed.html#Regular-Expressions](http://www.gnu.org/software/sed/manual/sed.html#Regular-Expressions)
and
[http://www.gnu.org/software/sed/manual/sed.html#Extended-regexps](http://www.gnu.org/software/sed/manual/sed.html#Extended-regexps)
and
[http://www.gnu.org/software/sed/manual/sed.html#Escapes](http://www.gnu.org/software/sed/manual/sed.html#Escapes)

Regular expression support is pretty basic, there is no \d, [:digit:] etc.  \w and \W are one of the few that do work.  So to match digits, use the [0-9] range instead.

```
echo '12345aaa~~' | sed -r 's/([0-9]+).*/\1/'
12345

```(or, without the -r flag )  
```
echo '12345aaa~~' | sed 's/\([0-9]\+\).*/\1/'

```

---

### Post by itmozart on 2009-08-31
thank you. I must have overlooked them, possibly hoping this wasn't the solution :-)

saverio

---

