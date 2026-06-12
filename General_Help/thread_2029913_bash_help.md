---
title: "bash help"
date: 2012-07-20
forum: General Help
---

### Post by Drenriza on 2012-07-20
Hey guys.

I have a command and output as follows.

SUP-STB10-25-eclipse-2009:~# /bin/df |grep -i -v filesystem |/bin/grep %
(se picture for output)

How can i do so the output i get is
58%
0%
6%
0%
63%
63%
63%
63%

in a single line.

the issue is i cant say awk '{print $5}'
since that would print
58%
0%
6%
0%
/v
/v
/t
/a

because of the blank tab in some of the lines.

Thanks on advance.
Kind regards.

---

### Post by steeldriver on 2012-07-20
why not replace both greps with

```
grep -Eo "[0-9]+%"
```

(match the regular expression 'one or more digits followed by %' and then print only the matching text)

---

### Post by sudodus on 2012-07-20
Try this one (it finishes without a new line, but that could be fixed afterwards)

```
df |grep -Eo "[0-9]+%" |tr '\n' ' '
```

---

### Post by Drenriza on 2012-07-20
> **sudodus said:**
> Try this one (it finishes without a new line, but that could be fixed afterwards)

```
df |grep -Eo "[0-9]+%" |tr '\n' ' '
```

Thats pretty sweet. Gives the following output.
SUP-STB10-25-eclipse-2009:~# df |grep -Eo "[0-9]+%" |tr '\n' ' '
58% 0% 6% 0% 63% 63% 63% 63% SUP-STB10-25-eclipse-2009:~#

If their is an easy way to split the output on the space onto a newline that would be Awesome!

#Steeldriver
I'am not super hot to bash ,) so i would not know how to do such fancy things :D

I know just enough (for the most time) to get around.

---

### Post by sudodus on 2012-07-20
For example
```
df |grep -Eo "[0-9]+%" |tr '\n' ' ';echo  ' '
```
gives a new line at the end

---

### Post by Drenriza on 2012-07-20
> **sudodus said:**
> For example
```
df |grep -Eo "[0-9]+%" |tr '\n' ' ';echo  ' '
```
gives a new line at the end

Ow yea but i ment
so it would stand
58% 
0% 
6% 
0% 
63% 
63% 
63% 
63%

instead of 
58% 0% 6% 0% 63% 63% 63% 63%

---

### Post by sudodus on 2012-07-20
Sorry, I thought you wanted it on the same line (horizontally). I think the command by Steeldriver in post #2 does exactly what you want when piping from df

```
df |grep -Eo "[0-9]+%"
```

---

### Post by Drenriza on 2012-07-20
> **sudodus said:**
> Sorry, I thought you wanted it on the same line (horizontally). I think the command by Steeldriver in post #2 does exactly what you want when piping from df

```
df |grep -Eo "[0-9]+%"
```

Thanks guys!

---

