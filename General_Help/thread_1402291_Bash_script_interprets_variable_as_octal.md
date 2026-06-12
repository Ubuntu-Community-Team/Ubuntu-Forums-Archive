---
title: "Bash script interprets variable as octal"
date: 2010-02-09
forum: General Help
---

### Post by InkyDinky on 2010-02-09
I have a script where I write the date to a variable and decrement for a period:
```

datedaystring=`date +%F | cut -c9-10`
....
datedaystring_twodigitformat=$(printf "%02d" $datedaystring);
....
let "datedaystring -=1"

```
Today I stumbled upon the problem that I get this error:
```

 printf: $datedaystring: invalid number
...
let: 08: value too great for base (error token is "08")
printf: 08: invalid octal number

```
It appears that somehow it is interpreting todays date (the 8th) as octal when I stick it in two digit date format.  Is there a way to make it so that it doesn't interpret the variable as an octal set?  It works fine for other numbers. I can artificially set datedaystring to a number greater than or less than 8 and it works. 

I've tried using double and single quotes. All I can find in the bash manual is about converting *to* octal but it doesn't talk about preventing conversion to octal. I imagine that 08 is telling it to convert to octal. So how do I prevent conversion to octal and just have it stay as a number occupying to decimal places?

---

### Post by chewearn on 2010-02-09
I am not sure I understand your code.

[1] 
This:
```
datedaystring=`date +%F | cut -c9-10`
```can be accomplished in a simpler manner by:
```
datedaystring=`date +%d`
```[2]
This:
```
datedaystring_twodigitformat=$(printf "%02d" $datedaystring);
```appears to be redundant, since [1] above already is two digit format.

And btw, when "datedaystring=08" or any other number preceed by 0, I got a different error message from [2]

```
$ ds=08
$ dst=$(printf "%02d" $ds)
bash: printf: 08: invalid number
```

---

### Post by falconindy on 2010-02-09
The problems as I see it are this:
1) Unnecessary use of cut. "date +%d" gets right to the point.
2) Avoid printf for simple formatting. Also, you're already getting the date as zero padded by the date command.
3) Let is old and terrible. If you're trying to be portable, Awk might be a better choice.

```
$ datedaystring=$(date +%d)
$ echo $datedaystring
09
$ awk "BEGIN { printf(\"%02d\", $datedaystring - 1)}"
08
```

Semi-related: If you ever really need to zero pad, you're better off using a simple trick like this:
```
$ num=9
$ echo 0$num | tail -c3
09
$ num=20
$ echo 0$num | tail -c3
20
```
If you need to strip leading zeroes:
```
$ num=08
$ num=$(seq $num $num)
$ echo $num
8
```

---

### Post by InkyDinky on 2010-02-10
I needed to force interpretation as base 10 instead of octal.

Taken from the bash hackers wiki: [http://www.bash-hackers.org/wiki/doku.php/syntax/arith_expr]("http://www.bash-hackers.org/wiki/doku.php/syntax/arith_expr")
```
If you have a constant set in a variable, like:

x=03254

this is interpreted as octal value. If you want it to be interpreted as decimal value, you need to expand the parameter and specify base 10:

# this is interpreted decimal:
echo $(( 10#$x ))

```

---

