---
title: "Complicated text file manipulation"
date: 2010-09-26
forum: General Help
---

### Post by oldmankit on 2010-09-26
Hi people,

I have a task that looks unfeasibly complicated to me, but I'm hoping it won't be for someone else.  I have a large (>10mb) text file containing the data for a Thai dictionary.  I'm trying to format it to go on my kindle.  The biggest challenge is that the data contains Thai characters, which I need to be able to search.  The kindle can't search in any characters other than Roman ones.  Hence, I need to transliterate all of the main entries from Thai into English.  Transliteration can be done online easily enough.

Here's a sample of the file:

**&#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;&#3586;&#3657;&#3634;&#3591;&#3605;&#3657;&#3609;**
<eentry>abovementioned</eentry>
*(PRON)*
<tsyn>&#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;</tsyn>
<tsample>&#3627;&#3609;&#3656;&#3623;&#3618;&#3591;&#3634;&#3609;&#3586;&#3629;&#3591;&#3648;&#3619;&#3634;&#3626;&#3634;&#3617;&#3634;&#3619;&#3606;&#3619;&#3633;&#3610;&#3610;&#3607;&#3610;&#3634;&#3607;&#3652;&#3604;&#3657;&#3648;&#3611;&#3655;&#3609;&#3629;&#3618;&#3656;&#3634;&#3591;&#3604;&#3637; &#3605;&#3634;&#3617;&#3626;&#3616;&#3634;&#3614;&#3588;&#3623;&#3634;&#3617;&#3614;&#3619;&#3657;&#3629;&#3617;&#3604;&#3657;&#3634;&#3609;&#3605;&#3656;&#3634;&#3591;&#3654; &#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;&#3586;&#3657;&#3634;&#3591;&#3605;&#3657;&#3609;</tsample>


**&#3585;&#3634;&#3619;&#3591;&#3604;&#3629;&#3629;&#3585;&#3648;&#3626;&#3637;&#3618;&#3591;**
<eentry>abstention</eentry>
*(N)*
<tant>&#3585;&#3634;&#3619;&#3629;&#3629;&#3585;&#3648;&#3626;&#3637;&#3618;&#3591;</tant>
<tdef>&#3585;&#3634;&#3619;&#3652;&#3617;&#3656;&#3649;&#3626;&#3604;&#3591;&#3588;&#3623;&#3634;&#3617;&#3648;&#3627;&#3655;&#3609;&#3605;&#3634;&#3617;&#3626;&#3636;&#3607;&#3608;&#3636;</tdef>


**&#3605;&#3634;&#3617;&#3585;&#3598;&#3627;&#3617;&#3634;&#3618;**
<eentry>according to law</eentry>
*(ADV)*
<tenglish>according to the law; legally</tenglish>
<tsyn>&#3650;&#3604;&#3618;&#3594;&#3629;&#3610;&#3604;&#3657;&#3623;&#3618;&#3585;&#3598;&#3627;&#3617;&#3634;&#3618;</tsyn>
<tsample>&#3627;&#3609;&#3633;&#3591;&#3626;&#3639;&#3629;&#3621;&#3634;&#3629;&#3629;&#3585;&#3586;&#3629;&#3591;&#3609;&#3634;&#3618;&#3614;&#3619;&#3614;&#3592;&#3609;&#3660;&#3618;&#3633;&#3591;&#3652;&#3617;&#3656;&#3607;&#3633;&#3609;&#3617;&#3637;&#3612;&#3621;&#3605;&#3634;&#3617;&#3585;&#3598;&#3627;&#3617;&#3634;&#3618; &#3648;&#3619;&#3639;&#3656;&#3629;&#3591;&#3619;&#3634;&#3623;&#3585;&#3655;&#3592;&#3610;&#3621;&#3591;&#3648;&#3626;&#3637;&#3618;&#3585;&#3656;&#3629;&#3609;</tsample>
<tdef>&#3606;&#3641;&#3585;&#3605;&#3657;&#3629;&#3591;&#3605;&#3634;&#3617;&#3585;&#3598;&#3627;&#3617;&#3634;&#3618;</tdef>


**&#3648;&#3607;&#3588;&#3650;&#3609;&#3650;&#3621;&#3618;&#3637;&#3626;&#3617;&#3633;&#3618;&#3651;&#3627;&#3617;&#3656;**
<eentry>advanced technologies</eentry>
*(N)*
<tsyn>&#3648;&#3607;&#3588;&#3650;&#3609;&#3650;&#3621;&#3618;&#3637;&#3607;&#3633;&#3609;&#3626;&#3617;&#3633;&#3618;</tsyn>
<tant>&#3648;&#3607;&#3588;&#3650;&#3609;&#3650;&#3621;&#3618;&#3637;&#3619;&#3640;&#3656;&#3609;&#3648;&#3585;&#3656;&#3634;</tant>
<tsample>&#3588;&#3629;&#3617;&#3614;&#3636;&#3623;&#3648;&#3605;&#3629;&#3619;&#3660;&#3648;&#3611;&#3655;&#3609;&#3611;&#3633;&#3592;&#3592;&#3633;&#3618;&#3626;&#3635;&#3588;&#3633;&#3597;&#3651;&#3609;&#3585;&#3634;&#3619;&#3614;&#3633;&#3602;&#3609;&#3634;&#3648;&#3607;&#3588;&#3650;&#3609;&#3650;&#3621;&#3618;&#3637;&#3626;&#3617;&#3633;&#3618;&#3651;&#3627;&#3617;&#3656;&#3648;&#3585;&#3639;&#3629;&#3610;&#3607;&#3640;&#3585;&#3594;&#3609;&#3636;&#3604;</tsample>
<tnum>&#3594;&#3609;&#3636;&#3604;</tnum>

The text in double asterisks is the stuff that needs transliterating.  I suppose it would be easy enough to delete all lines that don't contain  double asterisks, run it through the online transliteration, but then -- **how do I get the transliteration back into the original file, in the correct place?**  As you can see, these dictionary entries contain varying numbers of lines.

I'm completely stumped.  Doing this manually could take a very long, painful time.

All suggestions appreciated!

---

### Post by amauk on 2010-09-26
This should be possible if you could provide a complete list of Thai characters, along with the latin characters to substitute

then, you can use tr to substitute one set for the other set

This is obviously wrong, as I don't know the language, but as an example
```
tr '&#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;' 'abcde'
```
this will replace each character in the first set with the corresponding character in the second set

---

### Post by amauk on 2010-09-26
actually, sed may be better than tr

very rough script (probably can be improved a lot, but seems to work)
Fill in all thai characters and latin counterparts in the 2 arrays THAI & LATIN

```
#!/bin/bash

THAI=(
    &#3585;
    &#3634;
    &#3619;
    &#3591;
    &#3604;
    &#3629;
    &#3629;
    &#3585;
    &#3648;
    &#3626;&#3637;
    &#3618;
    &#3591;
)

LATIN=(
    a
    b
    c
    d
    e
    f
    g
    h
    i
    j
    k
    l
)

THAI_TRANS=$(cat "$1")
NUM_CHARS=${#THAI[*]}

for ((i=0; i<$NUM_CHARS; i++)); do
    while [ -n "$(echo "$THAI_TRANS" | grep "\*\*.*${THAI[$i]}.*\*\*")" ]; do
        THAI_TRANS=$(echo "$THAI_TRANS" | sed "s|\(\*\*.*\)${THAI[$i]}\(.*\*\*\)|\1${LATIN[$i]}\2|")
    done
done

echo "$THAI_TRANS"
```

Assuming thai dictionary is "thai_dict.txt", and you want to output translated file as "thai_trans.txt", run with
```
./thai_translate thai_dict.txt > thai_trans.txt
```

thai_dict.txt```
**&#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;&#3586;&#3657;&#3634;&#3591;&#3605;&#3657;&#3609;**
<eentry>abovementioned</eentry>
*(PRON)*
<tsyn>&#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;</tsyn>
<tsample>&#3627;&#3609;&#3656;&#3623;&#3618;&#3591;&#3634;&#3609;&#3586;&#3629;&#3591;&#3648;&#3619;&#3634;&#3626;&#3634;&#3617;&#3634;&#3619;&#3606;&#3619;&#3633;&#3610;&#3610;&#3607;&#3610;&#3634;&#3607;&#3652;&#3604;&#3657;&#3648;&#3611;&#3655;&#3609;&#3629;&#3618;&#3656;&#3634;&#3591;&#3604; &#3637; &#3605;&#3634;&#3617;&#3626;&#3616;&#3634;&#3614;&#3588;&#3623;&#3634;&#3617;&#3614;&#3619;&#3657;&#3629;&#3617;&#3604;&#3657;&#3634;&#3609;&#3605;&#3656;&#3634;&#3591;&#3654; &#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;&#3586;&#3657;&#3634;&#3591;&#3605;&#3657;&#3609;</tsample>


**&#3585;&#3634;&#3619;&#3591;&#3604;&#3629;&#3629;&#3585;&#3648;&#3626;&#3637;&#3618;&#3591;**
<eentry>abstention</eentry>
*(N)*
<tant>&#3585;&#3634;&#3619;&#3629;&#3629;&#3585;&#3648;&#3626;&#3637;&#3618;&#3591;</tant>
<tdef>&#3585;&#3634;&#3619;&#3652;&#3617;&#3656;&#3649;&#3626;&#3604;&#3591;&#3588;&#3623;&#3634;&#3617;&#3648;&#3627;&#3655;&#3609;&#3605;&#3634;&#3617;&#3626;&#3636;&#3607;&#3608;&#3636;</tdef>
```

thai_trans.txt```
**e&#3633;da&#3621;&#3656;b&#3623;&#3586;&#3657;bd&#3605;&#3657;&#3609;**
<eentry>abovementioned</eentry>
*(PRON)*
<tsyn>&#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;</tsyn>
<tsample>&#3627;&#3609;&#3656;&#3623;&#3618;&#3591;&#3634;&#3609;&#3586;&#3629;&#3591;&#3648;&#3619;&#3634;&#3626;&#3634;&#3617;&#3634;&#3619;&#3606;&#3619;&#3633;&#3610;&#3610;&#3607;&#3610;&#3634;&#3607;&#3652;&#3604;&#3657;&#3648;&#3611;&#3655;&#3609;&#3629;&#3618;&#3656;&#3634;&#3591;&#3604; &#3637; &#3605;&#3634;&#3617;&#3626;&#3616;&#3634;&#3614;&#3588;&#3623;&#3634;&#3617;&#3614;&#3619;&#3657;&#3629;&#3617;&#3604;&#3657;&#3634;&#3609;&#3605;&#3656;&#3634;&#3591;&#3654; &#3604;&#3633;&#3591;&#3585;&#3621;&#3656;&#3634;&#3623;&#3586;&#3657;&#3634;&#3591;&#3605;&#3657;&#3609;</tsample>


**abcdeffaijkd**
<eentry>abstention</eentry>
*(N)*
<tant>&#3585;&#3634;&#3619;&#3629;&#3629;&#3585;&#3648;&#3626;&#3637;&#3618;&#3591;</tant>
<tdef>&#3585;&#3634;&#3619;&#3652;&#3617;&#3656;&#3649;&#3626;&#3604;&#3591;&#3588;&#3623;&#3634;&#3617;&#3648;&#3627;&#3655;&#3609;&#3605;&#3634;&#3617;&#3626;&#3636;&#3607;&#3608;&#3636;</tdef>
```

---

### Post by oldmankit on 2010-09-27
Amauk,  thanks so much for your work on this.  At first I thought this approach wouldn't work, as the process of parsing Thai is considered quite difficult.  Vowels appear both before, above, under and after a consonant (and of course in combination), and consonants change depending on whether they're at the beginning or the end of a syllable.  Also because of the lack of spaces it is sometimes unclear when one word or part of word ends, and the next begins.

But then I realised I'm not trying to get an accurate phonetic transliteration, just something that I can use to search.  And what you've given will do that.

It's quite important for me to retain the original Thai word (the one in double asterisks) plus the transliterated, Roman version, for searching (preferably on the same line).  Is there a way to do this?

---

### Post by amauk on 2010-09-27
> **oldmankit said:**
> At first I thought this approach wouldn't work, as the process of parsing Thai is considered quite difficult.  Vowels appear both before, above, under and after a consonant (and of course in combination), and consonants change depending on whether they're at the beginning or the end of a syllable.  Also because of the lack of spaces it is sometimes unclear when one word or part of word ends, and the next begins.

But then I realised I'm not trying to get an accurate phonetic transliteration, just something that I can use to search.  And what you've given will do that.
The array elements don't have to be single characters, you can use sequences of characters

If you can fill in the 2 arrays with every possible variant of characters (both single characters and groups) together with a corresponding latin character sequence, then it should be fine

> **oldmankit said:**
> It's quite important for me to retain the original Thai word (the one in double asterisks) plus the transliterated, Roman version, for searching (preferably on the same line).  Is there a way to do this?Yep, can do that
```
#!/bin/bash

THAI=(
    &#3585;
    &#3634;
    &#3619;
    &#3591;
    &#3604;
    &#3629;
    &#3629;
    &#3585;
    &#3648;
    &#3626;&#3637;
    &#3618;
    &#3591;
)

LATIN=(
    a
    b
    c
    d
    e
    f
    g
    h
    i
    j
    k
    l
)

THAI_TRANS=$(cat "$1")
NUM_CHARS=${#THAI[*]}

[COLOR="Red"]THAI_TRANS=$(echo "$THAI_TRANS" | sed 's|\*\*\(.*\)\*\*|**\1** \1|')[/COLOR]

for ((i=0; i<$NUM_CHARS; i++)); do
    while [ -n "$(echo "$THAI_TRANS" | grep "\*\*.*${THAI[$i]}.*\*\*")" ]; do
        THAI_TRANS=$(echo "$THAI_TRANS" | sed "s|\(\*\*.*\)${THAI[$i]}\(.*\*\*\)|\1${LATIN[$i]}\2|")
    done
done

echo "$THAI_TRANS"
```

---

### Post by amauk on 2010-09-27
Addendum,
Just thought

If you use multiple characters in the arrays, then ordering will be important

Put the longest sequences first
(else a shorter sequence may be incorrectly matched & replaced instead of the correct longer sequence)

---

### Post by oldmankit on 2010-10-06
Allright!  I've finally done it!

It's taken me a while, partly because the conversion from text to mobi takes several hours and I've needed to do this several times before the final, searchable version, came out right.  I'm really excited about this.

When it is fully tuned I will post the finished .mobi file  to several Thai language websites, as it really is valuable for learners of Thai.

I would like to say a big thanks to amauk for all your hard work.

I have a final question.  At the moment, the transliterated text is appearing between the double asterisks.  After the markup to .mobi the double asterisks make what's inside them bold.  I would really like this to be the original Thai script, with the transliteration directly after.  Just for cosmetic reasons...

---

### Post by amauk on 2010-10-06
> **oldmankit said:**
> I would like to say a big thanks to amauk for all your hard work.No problem, glad I could help

> **oldmankit said:**
> I have a final question.  At the moment, the transliterated text is appearing between the double asterisks.  After the markup to .mobi the double asterisks make what's inside them bold.  I would really like this to be the original Thai script, with the transliteration directly after.  Just for cosmetic reasons...Untested, but this should flip the original and translated text, so orig is in double asterisks, and translated follows on same line without double asterisks.
```
THAI_TRANS=$(cat "$1")
NUM_CHARS=${#THAI[*]}

THAI_TRANS=$(echo "$THAI_TRANS" | sed 's|\*\*\(.*\)\*\*|**\1** \1|')

for ((i=0; i<$NUM_CHARS; i++)); do
    while [ -n "$(echo "$THAI_TRANS" | grep "\*\*.*${THAI[$i]}.*\*\*")" ]; do
        THAI_TRANS=$(echo "$THAI_TRANS" | sed "s|\(\*\*.*\)${THAI[$i]}\(.*\*\*\)|\1${LATIN[$i]}\2|")
    done
done

[COLOR="Red"]THAI_TRANS=$(echo "$THAI_TRANS" | sed 's|\*\*\(.*\)\*\* \(.*\)|**\2** \1|')[/COLOR]

echo "$THAI_TRANS"
```

---

### Post by rnerwein on 2010-10-06
hi folks
if any body can tell me how to solve this problem - tell me ( my wife is thai ).
that are the no spaces between the words is the littlest problem. thai is written in a diffent way - ( v is not v ) it's
a matter on what any body want to tell you ( pronancation ).
but - may pen ray , jai len len.
i thought about this problem too - but give up.
have luck
ciao

---

### Post by oldmankit on 2010-10-13
> **rnerwein said:**
> hi folks
if any body can tell me how to solve this problem - tell me ( my wife is thai ).
that are the no spaces between the words is the littlest problem. thai is written in a diffent way - ( v is not v ) it's
a matter on what any body want to tell you ( pronancation ).
but - may pen ray , jai len len.
i thought about this problem too - but give up.
have luck
ciao

I'm not quite sure what you're asking. Could you rephrase the question?  

Reading Thai is not as hard as people think. Pronunciation is in many ways harder.

---

