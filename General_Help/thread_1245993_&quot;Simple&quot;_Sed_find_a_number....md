---
title: "&quot;Simple&quot; Sed??? find a number..."
date: 2009-08-21
forum: General Help
---

### Post by justleen on 2009-08-21
Say, I have a string "Abcd 12345" and I want to keep only the digits of that string. 
I'd would have thought this to be straight forward, using sed with [0-9], but I cant get this right!

Can anyone help me? what I've tried so far:
```

echo "Abcd 12345" |sed 's/.*\([0-9]*\)/\1/'
echo "Abcd 12345" |sed 's/.*\([0-9][0-9]*\)/\1/'
echo "Abcd 12345" |sed 's/.*\([0-9][0-9]+\)/\1/'
echo "Abcd 12345" |sed 's/.*\([0-9]+\)[^0-9]|$/\1/'
etc...

```
One that works, but I dont like (because of the 'hardcoded' space)"
```
 echo "Abcd 12345" | sed 's/\(.*\) \([0-9]\)/\2/' 
```



Edit: no "Mark as Solved" Button any more?

---

### Post by DaithiF on 2009-08-21
Hi,
one way:
echo "Abcd 12345 other" | sed 's/[^0-9]*\([0-9]\+\).*/\1/'

or using tr is a little bit neater:
 echo "Abcd 12345" | tr -dc '[0-9]'

-d = delete
-c = complement the set
so delete everything that isn't in the set [0-9]

---

### Post by justleen on 2009-08-21
Ahumm! Thans a bunch.. !

Can you explain why you start off with the [^0-9]?
As in, i know you match the opposite of 0-9, thus all non digits, but how is that different to  /.*\([0-9]*\).*/\1/   ?  Why does this only match correctly when using the whole thing??

---

### Post by DaithiF on 2009-08-21
Hi,
well if you start the pattern with .*, and the rest of the pattern consists of optional ('*') elements, then that first .* is going to greedily match **everything**, leaving nothing to be matched by the pattern in parentheses.  (Theres no equivalent to 'non-greedy' matching in sed unfortunately, so instead just match everything **except** that which you want to keep.)

Note that if you had used some non-optional qualifiers like +, or {m}, {m,n} in the later patterns, then you could still use the .* pattern at the start, since the later ones would 'defeat' the greediness of the first .* pattern.  (Not a good explanation, so some examples below instead:)

ABCD 12345
s/.*\([0-9]*\)/\1/    # no output, as .* at start matches everything
s/.*\([0-9]\+)/\1/    # 5 output, \+ means match at least one digit
s/.*\([0-9]\{5\}\)/\1/   # 12345 output, since we match 5 digits.

but since you presumably don't know how many digits you want to match, I think better to match all the non-digits at the start using the [^0-9]*.

---

### Post by justleen on 2009-08-21
Ahhhh, so basicly, your "faking" a non-greedy match, by defining what the greedy match should not match?
(hmmm.. terminology is a bit ocward this way)


Thanks a lot, this was very usefull info! (not just for this case..)

---

