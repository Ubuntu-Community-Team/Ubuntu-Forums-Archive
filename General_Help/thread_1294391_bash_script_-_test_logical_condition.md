---
title: "bash script - test logical condition"
date: 2009-10-18
forum: General Help
---

### Post by dandeliondream on 2009-10-18
I have the following bash script. When I run the script, it returns "passed logical condition" which is not what i wanted. Please advise.

#!/usr/bin/bash
A=3
B=5
if (test $A=3) && (test $B=3)
then
  echo "passed logical condition."
else
  echo "failed logical condition."
fi

---

### Post by falconindy on 2009-10-18
[[ $A -eq 3 ]] && [[ $B -eq 3 ]]

the equals sign is used for string compares, not numerical.

You also might be getting odd results because bash is typically in /bin, not /usr/bin.

---

### Post by Sam on 2009-10-18
This might be a good read: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

---

### Post by dandeliondream on 2009-10-18
> **falconindy said:**
> [[ $A -eq 3 ]] && [[ $B -eq 3 ]]

the equals sign is used for string compares, not numerical.

You also might be getting odd results because bash is typically in /bin, not /usr/bin.

this is useful. thank u :P

---

### Post by dandeliondream on 2009-10-18
> **Sam said:**
> This might be a good read: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

thanks! i'll check it out.

---

### Post by kaibob on 2009-10-18
You can also combine tests as follows:

```
#!/bin/bash

A=5
B=3

if [ $A -eq 3 -a $B -eq 3 ] ; then
  echo "passed logical condition."
else
  echo "failed logical condition."
fi
```

---

### Post by dandeliondream on 2009-10-18
> **kaibob said:**
> You can also combine tests as follows:

```
#!/bin/bash

A=5
B=3

if [ $A -eq 3 -a $B -eq 3 ] ; then
  echo "passed logical condition."
else
  echo "failed logical condition."
fi
```

cool...seems easier. thanks! :KS

---

### Post by laceration on 2009-10-18
This is the stupidest part of bash.  It frustrated me when I was learning bash -- which is to say it still frustrates me.  It is so over complicated compared to other languages. 
if [ $A -eq 3 ] && [ $B -eq 3 ]
would work, the double brackets are only necessary for a more complicated comparison like
if [[ $arg4 =~ "+d" ]]
They are your higher horsepower comparison operators.  Bash has some fuzzy rules.
Be careful, this will not work:
if [$A -eq 3] && [$B -eq 3]

If you can deal with the comparison cruft, which is doable, bash is great.

---

### Post by falconindy on 2009-10-18
> **laceration said:**
> This is the stupidest part of bash.  It frustrated me when I was learning bash -- which is to say it still frustrates me.  It is so over complicated compared to other languages. 
if [ $A -eq 3 ] && [ $B -eq 3 ]
would work, the double brackets are only necessary for a more complicated comparison like
if [[ $arg4 =~ "+d" ]]
They are your higher horsepower comparison operators.  Bash has some fuzzy rules.
Be careful, this will not work:
if [$A -eq 3] && [$B -eq 3]

If you can deal with the comparison cruft, which is doable, bash is great.
Double square brackets are different from single square brackets, but not for the reason you've mentioned. Single square brackets launch a new program (do `man [`), whereas double square brackets are a built-in functionality of Bash. If you're using solely Bash... that is, without regard for portability to other shells, there's no reason to use the single brackets.

I found Bash to be a little tedious at first. Now that I've been scripting with it for a few months, it's fantastic.

---

### Post by laceration on 2009-10-18
@falconindy

```
$ type '['
[ is a shell builtin
```
You are right '[' is a standalone program, but bash does not use it.  The convention for most bash scripts seems to be the single [.  If you are doing more than a simple or ordinary comparison and don't get the results you expect you should try '[['.

Interesting that '[[' is technically not a builtin!
```
$ type '[['
[[ is a shell keyword
```

---

### Post by falconindy on 2009-10-18
> **laceration said:**
> @falconindy

```
$ type '['
[ is a shell builtin
```
You are right '[' is a standalone program, but **bash does not use it**.  The convention for most bash scripts seems to be the single [.  If you are doing more than a simple or ordinary comparison and don't get the results you expect you should try '[['.

Interesting that '[[' is technically not a builtin!
```
$ type '[['
[[ is a shell keyword
```
Wrong. Bash will honor the single bracket and call the external program. The "unexpected" results you speak of are because you're using different methods to test your expression (test versus bash). I wrote a simple loop to test this:
```
#!/bin/bash

COUNT=0

while [ $COUNT -le 100000 ]; do
        echo $COUNT > /dev/null
        COUNT=$(($COUNT + 1))
done
```
Ran that a couple times and averaged the execution time. Did it again with double brackets. In real and user time, double brackets took roughly a half second less. There was a drop of roughly 3s to 2.5 on real time and 2.5 to 2.0 seconds on user time. System time consumed was closer, but still in favor of double brackets.

---

### Post by laceration on 2009-10-18
A speed test only proves speed, it might make sense that a builtin is faster, but it isn't necessarily so.

The unexpected(to you) results were done in a bash shell using another bash builtin command(type).  If you put it in a script you will get the same result.

and
```

$ type -a '['
[ is a shell builtin
[ is /usr/bin/[

```
the -a option to type identifies keywords and builtins, and also locates system commands with identical names.

from man [
> 
NOTE: your shell may have its own version of test and/or [, which usually supersedes the version described here.


```
$ type -a test
test is a shell builtin
test is /usr/bin/test
```

---

### Post by kaibob on 2009-10-18
> **falconindy said:**
> <snip>
```
#!/bin/bash

COUNT=0

while [ $COUNT -le 100000 ]; do
        echo $COUNT > /dev/null
        COUNT=$(($COUNT + 1))
done
```
Ran that a couple times and averaged the execution time. Did it again with double brackets. In real and user time, double brackets took roughly a half second less. There was a drop of roughly 3s to 2.5 on real time and 2.5 to 2.0 seconds on user time. System time consumed was closer, but still in favor of double brackets.

You must have a fast computer. The single- and double-bracket bash script took 7.1 and 5.9 seconds real time on my computer, respectively. The real speed demon was dash with single brackets at 1.8 seconds. Dash, of course, does not support double brackets. In the real world, I suspect this doesn't mean much but interesting anyways.

EDIT:

I eliminated the redirection to /dev/null and changed the loop to 100,000. I then reran the tests, and the results were 14.67 seconds for bash with the single brackets, 13.0 seconds for bash with double brackets, and 4.3 seconds for dash. I can see why they changed to dash for the default system shell.

---

### Post by falconindy on 2009-10-18
> **laceration said:**
> A speed test only proves speed, it might make sense that a builtin is faster, but it isn't necessarily so.

The unexpected(to you) results were done in a bash shell using another bash builtin command(type).  If you put it in a script you will get the same result.

and
```

$ type -a '['
[ is a shell builtin
[ is /usr/bin/[

```the -a option to type identifies keywords and builtins, and also locates system commands with identical names.

from man [


```
$ type -a test
test is a shell builtin
test is /usr/bin/test
```
Ok? [ and test are both builtins, whereas [[ is a keyword. Great. Your original premise is that [[ is only used as a wrapper for anything more than a "simple or ordinary" expression. I think I've disproved that with my script. Other than speed, there's not really any other tangible benefit as long as you conform to the syntax in order to get the desired results.

> If you put it in a script you will get the same result.
But my test WAS done in a script? I executed it as `time test.sh`. I'm not really sure how to interpret this other than that you're implying different results in a shell other than Bash (i.e. /bin/sh). Well, I've based all my statements in the context of Bash since that's what this thread's topic is regarding. Performance in other shells is based on those other shells and not really relevant here. Might as well open up a new topic called "What's the best Shell?"

---

### Post by falconindy on 2009-10-18
> **kaibob said:**
> You must have a fast computer. The single- and double-bracket bash script took 7.1 and 5.9 seconds real time on my computer, respectively. The real speed demon was dash with single brackets at 1.8 seconds. Dash, of course, does not support double brackets. In the real world, I suspect this doesn't mean much but interesting anyways.
Sure, and Dash is meant to be fast, not full-featured like Bash. Thanks for doing this. I was about to as soon as I got off this live CD (resizing my boot drive). I suspect it doesn't mean much, as its rare you'll come across a loop that equates to this much processing power in every day shell scripting. Still, I'm the curious type with a heavy logical/mathematical inclination, so these things are always of interest to me.

FYI, my rig is a 3.16ghz E8500 Wolfdale (core2duo). Last I checked, it's benchmarked as being about 110th in order of raw CPU power. I'd like to think the time I spend optimizing and compiling my own kernels isn't entirely wasted.

---

### Post by laceration on 2009-10-18
Falconindy,

I did not have a premise, I just stated when it is necessary to use the doubles and when its not to.  Quit arguing with me.  You wrote I was wrong when you were.  Bfd, I and probably most others have been wrong about things on ubuntuforums.  Stop being so defensive.  The important thing is trying to figure stuff out.

---

### Post by falconindy on 2009-10-18
Apologies if I'm coming off as defensive. I'm merely disagreeing with you. I've noted a performance improvement using the keyword over the built-in, and in my experiences, I've not seen a difference in output. Based on that, my first discovery of double square brackets lead me to rewrite the majority of my bin folder. Please, if I'm missing something, I'd love to know more.

My interest here is merely educational. Its not my intent to be aggressive.

---

### Post by laceration on 2009-10-18
You are being disagreeable, but I do not see where the disagreement is.  I never said using [ is better than [[.  You have shown that [[ is faster.  That being said, I have written a good amount of bash lately(see program in signature) and do not see where it would make a difference.  If I ever write a script that goes through my entire file system using conditionals, I'll be sure to use the doubles!

---

### Post by lswb on 2009-10-18
Another significant difference between [ expression ] and [[ expression ]] is that no filename globbing is done
inside [[  ]].

---

