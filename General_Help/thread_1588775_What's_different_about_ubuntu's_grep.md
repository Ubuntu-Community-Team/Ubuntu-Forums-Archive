---
title: "What's different about ubuntu's grep?"
date: 2010-10-05
forum: General Help
---

### Post by dewdrop_world on 2010-10-05
I have endless problems with the grep version provided with ubuntu. If it's anything other than a simple, fixed string, it finds nothing.

E.g., I have a file where several lines start with a bunch of tabs, followed by _name: "something",_. Easy to pull them out, right?

grep -e [:space:]+name -f (file)

Failed. "grep: Invalid regular expression"  Quoting the expression:

grep -e '[:space:]+name' -f (file)

... produces an empty result. (_[:space:]_ comes from *man grep* -- that couldn't be a mistake, could it?)

It's weird. I've used grep successfully in other platforms but on my ubuntu 10.04 box, I just cannot get it to work. It's not that I'm doing super-complex regexp's... really confused.

Thanks.
James

PS I could get sort of what I wanted with _[^\(]name_ but it *isn't* what I wanted! I wanted lines with *only* whitespace preceding "name". Grrrrrr....

---

### Post by amauk on 2010-10-05
you need to escape the +

```
grep -e '[:space:]\+name' -f (file)
```

*edit*
plus, [:space:] will only match spaces, not tabs

---

### Post by dewdrop_world on 2010-10-05
> **amauk said:**
> you need to escape the +

```
grep -e '[:space:]\+name' -f (file)
```

I want + to be used in the sense of "match one or more." Wouldn't escaping it match a literal plus sign? The lines I want to see have no plus signs in them, so I think your suggestion isn't right.

> *edit*
plus, [:space:] will only match spaces, not tabsSo, how DO you match tabs then? Online docs say to use \t but... with this input file:

```
            name: "xyz",
            (name: \fail)
```(tabs, not spaces - html conversion, yuk)

I get:

```
grep \t greptest.txt
(no matches)

grep '\t' greptest.txt
(no matches)

grep '[\t]' greptest.txt
            (name: \fail)
```IOW, what's supposed to match a tab (according to docs) actually turns into a character class matching the \!

You see my frustration. :)

TIA -
James

---

### Post by Ayuthia on 2010-10-05
Does
```

grep '\tgreptest.txt'

```
work?

---

### Post by dewdrop_world on 2010-10-05
> **Ayuthia said:**
> Does
```

grep '\tgreptest.txt'

```work?

greptest.txt is the name of the file. Why would I include it in the regexp?

---

### Post by Ayuthia on 2010-10-05
I have no idea what I was thinking about at the time.  Sorry about that.  How about trying doing:
```

grep '<control v><tab>' greptest.txt

```
In other words, inside the quotes, press control-v and then press the tab button.  It doesn't seem that this version of grep likes the plain tab or the \t.

---

### Post by amauk on 2010-10-05
> **dewdrop_world said:**
> I want + to be used in the sense of "match one or more." Wouldn't escaping it match a literal plus sign? The lines I want to see have no plus signs in them, so I think your suggestion isn't right.No, plus on it's own is literal
you need to escape it to give it it's regex matacharacter meaning

Why are you interested about the tabs, though
surely it's easier to just do
```
grep 'name: "[^"]\+"'
```

---

### Post by dewdrop_world on 2010-10-05
> **Ayuthia said:**
> I have no idea what I was thinking about at the time.  Sorry about that.  How about trying doing:
```

grep '<control v><tab>' greptest.txt

```In other words, inside the quotes, press control-v and then press the tab button.  It doesn't seem that this version of grep likes the plain tab or the \t.

OK, that does it, thanks!

I'm still puzzled, though, why documented features of regular expressions simply don't work (don't match). For instance, in the same original file post last night (not the two line example), other lines have in them "3 word" where word could be something different in each line. According to man grep, [:space:] should be a character class matching a space. But, grep '3[:space:]' file.txt matches nothing.

Sure, in that example, it's simpler to use '3 ' as the regular expression (and that works). But the issue is, there are things in the documentation that do not behave as advertised, and I have no idea how to find out which regexp features are "real" and which are fake.

Hoping somebody has some insight.

James

---

### Post by dewdrop_world on 2010-10-05
> **amauk said:**
> No, plus on it's own is literal
you need to escape it to give it it's regex matacharacter meaning

OK, I see now, that's a difference between basic and extended regular expressions. In extended re's you don't have to escape it.

I guess I will stick with extended re's from now on. It's very, very weird to me that a backslash, in basic re's, would usually indicate a character that should be treated as literal, except for some "special" ones. It seems more intuitive to me that characters would always have their operator meanings unless indicated otherwise by backslash... which is why we have commandline options :)

> Why are you interested about the tabs, though
surely it's easier to just do
```
grep 'name: "[^"]\+"'
```Easier but that has a different meaning. I meant what I wrote initially. There are other lines containing _name: "something"_ where that string is preceded by something other than pure white space, and I don't want to see those.

```
            name: "should match",
            bpCmd: (name: "should not match", ...)
```Your option would not let me distinguish between those two.

James

---

