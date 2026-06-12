---
title: "Math in sh = fail"
date: 2011-02-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-05
```
echo "$((30/60*120))" && gcalctool -s 30/60*120
0
60
```

---

### Post by Habitual on 2011-02-05
Split a Car Rental and a Hotel Bill for a week with a co-worker?

```
echo -n $;echo "scale=2; 408.55+1008.56/2" | bc
```

$912.83

or
```

expr `echo "digits_go_here" | sed -e 's/[0-9]/ + &/g' -e 's/^ +//g'`
```

Simple addition and subtraction problems:

```
echo "1+1" | bc
```
or
```
echo $(( 1+1 ))
```

---

### Post by slakkie on 2011-02-05
That's funny..

```

$ echo "30 / 60 * 120" | bc           
0
$ echo "scale = 1; 30 / 60 * 120" | bc
60.0

```

---

### Post by fabricator4 on 2011-02-05
There's no floating point in sh maths, so the product of 30/60 = 0

```

echo "$((120/60*30))"

```

Chris

---

### Post by fabricator4 on 2011-02-05
> **Habitual said:**
> 

```
echo -n $;echo "scale=2; 408.55+1008.56/2" | bc
```

$912.83


Eeek!

```

echo -n $;echo "scale=2; (408.55+1008.56)/2" | bc
$708.55


```

---

### Post by pqwoerituytrueiwoq on 2011-02-05
I can i round the output to a integer?

---

### Post by fabricator4 on 2011-02-05
> **pqwoerituytrueiwoq said:**
> I can i round the output to a integer?

The output of sh will always be an integer, an so will the arguments.  If you want to use bc as slakkie and Habitual showed you then use scale = 0:

sh
```

echo "$((95/3))"
31

```

bc scale 4
```

echo "scale=4; (95/3)" | bc
31.6666

```

bc scale 0
```

echo "scale=0; (95/3)" | bc
31

```


C

---

### Post by pqwoerituytrueiwoq on 2011-02-05
> **fabricator4 said:**
> The output of sh will always be an integer, an so will the arguments.  If you want to use bc as slakkie and Habitual showed you then use scale = 0:

sh
```

echo "$((95/3))"
31

```bc scale 4
```

echo "scale=4; (95/3)" | bc
31.6666

```bc scale 0
```

echo "scale=0; (95/3)" | bc
31

```
C
scale=0 gives me 0

```
echo "scale=0; (30/60*120)" | bc
0
```
i did find something with google that worked
```
echo "scale=10; 30/60*120" | bc | awk '{print int($1)}'
```

---

### Post by fabricator4 on 2011-02-05
Or as I said the first time:

```

echo "$((120/60*30))"
60

```

Chris

---

### Post by pqwoerituytrueiwoq on 2011-02-05
> **fabricator4 said:**
> Or as I said the first time:

```

echo "$((120/60*30))"
60

```Chris
opps missed that
anyway not that easy to reorder numbers in a equation when all the numbers are variables that run off user input and unknown variables

---

### Post by slakkie on 2011-02-06
Tbh, the answer could never be 60.

30 / 60 * 120 == 30 / ( 60 * 12) == 30 / 7200 != 60

The notation should be different, eg (30/60) * 120.

---

### Post by AlphaLexman on 2011-02-06
never mind

---

### Post by asmoore82 on 2011-02-06
> **slakkie said:**
> Tbh, the answer could never be 60.

30 / 60 * 120 == 30 / ( 60 * 12) == 30 / 7200 != 60

The notation should be different, eg (30/60) * 120.
[http://en.wikipedia.org/wiki/Order_of_operations](http://en.wikipedia.org/wiki/Order_of_operations)
The answer is **always** 60, unless you **change** the expression to 30 / (60*120)

But on the computer side of things, this is **not** fail.
**Integer Arithmetic.** This is how computers work.

True, it is a shortcoming of the CPU's binary nature. But a good
programmer understands how to use it to one's advantage. Integer arithmetic
is shockingly more efficient than "floating" decimal calculations.

Integer Arithmetic is the only way to deal with tangible, real world objects.
You just have to remember to always multiply first! - or you'll get truncated.

"Rounding" with decimals is a form of data loss - unacceptable in some situations.
Money, for example, should always be represented digitally as an Integer
value of pennies. Or a Integer pair of dollars and cents. Never a decimal
value of dollars. Multi-million dollar deals can't lose a few thousand here or
there to rounding.

To keep 100% accuracy with whole Integers, you can calculate a remainder
by using the modulus operator %. It turns out that this calculation is trivially
easy for CPU's. It's like the great old math class teachings -
"solve these equations of fractions and show your work!"

Another great trick for **faster** code is that even if you know
ahead of time that rounding error is acceptable, use Integers anyway!
Multiply the original value by 100, then remember that your
final result will be in whole hundredths.

For example, how big is this file in MB?
```
du -b Patent_Absurdity_HQ_768kbit.ogv
167094804	Patent_Absurdity_HQ_768kbit.ogv
```

`du` says:
```
du -h Patent_Absurdity_HQ_768kbit.ogv 
160M	Patent_Absurdity_HQ_768kbit.ogv
```

Integer Arithmetic says:
```
echo $(( 167094804 /1024 /1024 ))
159
```
fail? --
Lets make Integer Arithmetic accurate to 4 decimal places:
```
echo $(( 167094804 *1**0000** /1024 /1024 ))
159**3540**
```
^our *accurate* answer is 159.3540 MB

Does gcalctool concur?:
```
gcalctool -s "167094804 /1024 /1024"
159.35402298
```
^YES!

---

### Post by slakkie on 2011-02-08
> **asmoore82 said:**
> [http://en.wikipedia.org/wiki/Order_of_operations](http://en.wikipedia.org/wiki/Order_of_operations)
The answer is **always** 60, unless you **change** the expression to 30 / (60*120)


I guess I have been calculating stuff incorrectly since '92, since I used different math-rules. In '92 they changed the order. Guess no high-school teacher wanted to tell me this :D

---

