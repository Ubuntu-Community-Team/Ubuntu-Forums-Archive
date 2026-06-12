---
title: "bash syntax TEST command"
date: 2009-11-17
forum: General Help
---

### Post by mo.reina on 2009-11-17
can anyone explain the difference between these two constructs?

```
if [ xxxxxx ] 
```

```
if [[ xxxxxx ]]
```

when do you use the single brackets and when the double?

---

### Post by emigrant on 2009-11-17
[SIZE=3]**[] vs. [[]]**[/SIZE] 

Contrary to *[*, *[[* prevents word splitting of variable values.  So, if VAR="var with spaces", you do not need to double quote $VAR in a test - eventhough using quotes remains a good habit.  Also, *[[* prevents pathname expansion, so literal strings with wildcards do not try to expand to filenames.  Using *[[*, *==* and *!=* interpret strings to the right as shell glob patterns to be matched against the value to the left, for instance: *[[ "value" == val* ]]*.

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_02.html)

---

### Post by mo.reina on 2009-11-17
coincidence, that's exactly the manual i've been using and the reason i asked this question is because i was looking at the code above the description.  however, it doesn't completely answer my question.

for ex. there are certain arguments that work with [[ ]] that don't work with [ ].  does it boil down to the pathname expansion? the quoting seems to be a minor thing, why create additional syntax in the form of [[ ]] just to avoid quoting if you're using [ ]?

to take an example from the above guide:

```
gender="female"
mo@mo-laptop:~/scripts$ if [[ "$gender" == f* ]]
> then echo "pleasure to meet you madame."; fi
pleasure to meet you madame.
mo@mo-laptop:~/scripts$
```

if i use [ ] instead of [[ ]] nothing happens:
```
if [ "$gender" == "f*" ]; then echo "pleasure to meet you madame."; fi
mo@mo-laptop:~/scripts$ 
```

i quoted f* in the second example, but there is no output.

---

### Post by kjohri on 2009-11-17
[[ expression ]] is a compound command, that returns a 0 or 1. [ ] is the *test* built-in command; [ expr ] also returns a status of 0 or 1 based on the expr. The operators in the two cases are different. I case of [[ ]] one uses && for and and || for or. In case of test (that is, [ ]), one uses -a for and and -o for or. Also, string operators work differently in [[  ]], as the right string is considered a pattern and pattern matching rules are used.

---

### Post by kaibob on 2009-11-17
The following FAQ has a good explanation of the differences:

[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

My scripts tend to be very simple, and I like to use dash whenever possible. Dash does not support [[ so I always use [.

---

### Post by mo.reina on 2009-11-17
ok so basically pattern and regex matching isn't present in [ ], correct?

the faq is great by the way, thanks.

---

