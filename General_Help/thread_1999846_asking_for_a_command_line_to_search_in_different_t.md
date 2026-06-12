---
title: "asking for a command line to search in different text file and..."
date: 2012-06-08
forum: General Help
---

### Post by SidebySide on 2012-06-08
I illustrate what I need!

there is a pack of different text files:
a.txt
b.txt
c.html
d.cfg
I want to gather some phrases located within these files. The intended phrases are between [COLOR=Red][ ][/COLOR]. I want to gather them including [COLOR=Red][ ][/COLOR] into a new output text file! I used grep, but it gathers a full line, means:  "[COLOR=Magenta]morning[/COLOR] [COLOR=Red][work, work, work][/COLOR] [COLOR=Magenta]night[/COLOR]"
I just need to [COLOR=Red][work, work, work][/COLOR] part of that line; nothing before/after []!
[] may also be this form: [COLOR=Red][work, work,[/COLOR] (INTER)
[COLOR=Red]work][/COLOR]
How?

---

### Post by steeldriver on 2012-06-08
not sure what you mean by (INTER) - have you looked at all the grep options?

```
       -o, --only-matching
              Print  only  the  matched  (non-empty) parts of a matching line,
              with each such part on a separate output line.

```

or you could use sed of course...

 if you mean the [ and ] might be split across lines that's quite a  bit harder I think (in fact it could almost be homework...)

---

### Post by MG&amp;TL on 2012-06-08
You can use *awk *to print between lines[I]:

[/I]```
cat * | awk '$0=$2' FS=[ RS=] > output.txt
```

Explanation:

cat * - concatenate everything.

awk '$0=$2' FS=[ RS=]  - print everything that's between [ and ]

> output.txt and put it in output.txt

Hope that helps. Had to google the awk a lot, I'm not that much of a ninja.

---

### Post by Vaphell on 2012-06-08
nifty...

including [] would be '$0=$2 { print"["$0"]" }'

---

### Post by fatalGlory on 2012-06-08
This should do the job:

```
grep -o -e '\[[^]]\+]' *
```

I had two files (test_regex.txt and test_regex1.txt), I get this output:

```
test_regex1.txt:[phrase1abc]
test_regex1.txt:[phrase2def]
test_regex1.txt:[phrase3ghi]
test_regex1.txt:[phrase4jkl]
test_regex.txt:[phrase5abc]
test_regex.txt:[phrase6def]
test_regex.txt:[phrase7ghi]
test_regex.txt:[phrase8jkl]
```

---

### Post by SidebySide on 2012-06-09
[COLOR=#000000][FONT=Arial][FONT=Tahoma]surprising!
[/FONT][/FONT][/COLOR]```
[COLOR=#000000]
grep -o -e '\[[^]]\+]' *[/COLOR]
```@[fatalGlory]("http://ubuntuforums.org/member.php?u=134392")

Can you explain the last part? => '\[[^]]\+]'
because [] is not absolute! i should search for [COLOR=Red]( )[/COLOR], [COLOR=Red]" "[/COLOR], ..., too.
```

cat * | awk '$0=$2{print"["$0"]"}' FS=[ RS=] > output.txt
```The files aren't in one folder, so "cat" can't read all files!

> not sure what you mean by (INTER)Sorry,
[COLOR=#000000][FONT=Arial][FONT=Tahoma]orthography: [/FONT][/FONT][/COLOR]Enter (one of the keyboard keys)
Ex:
[COLOR=Red][word1, word2,
word3][/COLOR]

>  > output.txt and put it in output.txtA useful tip! :)

---

### Post by MG&amp;TL on 2012-06-09
> **SidebySide said:**
> [COLOR=#000000][FONT=Arial][FONT=Tahoma]surprising![/FONT][/FONT][/COLOR]
```

cat * | awk '$0=$2{print"["$0"]"}' FS=[ RS=] > output.txt
```The files aren't in one folder, so "cat" can't read all files!

A useful tip! :)

So...if you tell us roughly where the files are, we can do that too. Syntax is basically 

```
cat <files>
```Edit: If you want the thing to read over multiple lines, delete the newline characters first.
```
cat * | tr -d '\n' | awk '$0=$2{print"["$0"]"}' FS=[ RS=] > output.txt
```tr -d (delete specified character)

---

### Post by SidebySide on 2012-06-09
> **MG&TL said:**
> if you tell us roughly where the files are, we can do that too.
[COLOR=DarkRed]/home/sidebyside[/COLOR][COLOR=Red]/MumFolder[/COLOR][COLOR=Olive]/Folder1/[/COLOR]a.txt
[COLOR=DarkRed]/home/sidebyside[/COLOR][COLOR=Red]/MumFolder[/COLOR][COLOR=Olive]/Folder1/subfolder/[/COLOR]b.txt
[COLOR=DarkRed]/home/sidebyside[/COLOR][COLOR=Red]/MumFolder[/COLOR][COLOR=Olive]/Folder2/[/COLOR]c.txt
[COLOR=DarkRed]/home/sidebyside[/COLOR][COLOR=Red]/MumFolder[/COLOR][COLOR=Olive]/Folder3/[/COLOR]a.html
...

I want to execute the command in MumFolder and gather some data from text files which are placed in different folders(branch) of [COLOR=Red]MumFolder[/COLOR].

---

### Post by MG&amp;TL on 2012-06-09
```
cat [COLOR=Black]$(find [/COLOR][COLOR=Black]/home/sidebyside[/COLOR][COLOR=Black]/MumFolder) | [/COLOR]tr -d '\n' | awk '$0=$2{print"["$0"]"}' FS=[ RS=] > output.txt
```

$(find /home/sidebyside/MumFolder) ---finds all files in subdirectories of ~/MumFolder

---

### Post by Vaphell on 2012-06-09
> Edit: If you want the thing to read over multiple lines, delete the newline characters first.
```
cat * | tr -d '\n' | awk '$0=$2{print"["$0"]"}' FS=[ RS=] > output.txt
```

it would work either way without tr, but it would preserve the multiline status of matches in the output. Probably OP doesn't need these patterns broken up to pieces though.


> I want to execute the command in MumFolder and gather some data from text files which are placed in different folders(branch) of MumFolder.

how about
```

while read -r file
do
  awk '....' "$file"
  #or
  cat "$file" | tr ... | awk ...
done < <( find /home/sidebyside/MumFolder \( -iname '*.txt' -o -iname '*.html' \) -type f ) > out.txt
```
output of find is used to fuel the while loop, which goes through data line by line and reads it to the variable(s) given.

> because [] is not absolute! i should search for ( ), " ", ..., too.
that makes it a complete pain in the ... back.
what should be the output in case of aaa(aaa"bbbbbb[ccccccc"ddd)dddd]?

---

### Post by SidebySide on 2012-06-09
Tanx guys! awk works great

I'm also [COLOR=#000000][FONT=Arial][FONT=Tahoma]curious about this:[/FONT][/FONT][/COLOR]```
[COLOR=#000000]grep -o -e '\[[^]]\+]' *[/COLOR]
```It search for [COLOR=Red][phrase][/COLOR], How can I search for something else like [COLOR=Magenta]((phrase))[/COLOR] using the above line? I couldn't understand its last part: [COLOR=SeaGreen]'\[[^]]\+]'[/COLOR]

> **Vaphell said:**
> what should be the output in case of aaa(aaa"bbbbbb[ccccccc"ddd)dddd]?
What's wrong? 
[COLOR=RoyalBlue]aaa**(aaa"bbbbbb[ccccccc"ddd)**dddd][/COLOR] => when I'm searching for [COLOR=Red](phrase)[/COLOR], so **(aaa"bbbbbb[ccccccc"ddd)** will be the result and it's ok.

[COLOR=Magenta]
[/COLOR]

---

### Post by Vaphell on 2012-06-09
'\[[^]]\+]'
\[ = literal [
[^]] = any char that is not ]
\+ = + is 1-or-more of the stuff before it (1-or-more of anything but ]), but requires escaping in 'normal' grep mode 
] = literal ]

i prefer to switch to extended or perl mode when regex related chars don't require escaping to function (only if we want them literally, like [] and () in example below) - it makes using *,+,?, grouping and alternatives much easier without all these \. In 'normal' mode in case of remotely complex regex there are boatloads of \ and it's not easy on the eyes.

```
$ echo "a b [cde] ((fgh)) ijk" | grep -oP '[COLOR="DarkGreen"]\[[^[]+\][/COLOR]|[COLOR="Blue"]\(\([^(]+\)\)[/COLOR]'
[COLOR="DarkGreen"][cde][/COLOR]
[COLOR="Blue"]((fgh))[/COLOR]
```

---

### Post by steeldriver on 2012-06-09
> **SidebySide said:**
> How can I search for something else like [COLOR=Magenta]((phrase))[/COLOR] using the above line? I couldn't understand its last part: [COLOR=SeaGreen]'\[[^]]\+]'[/COLOR]

**Vaphell has beaten me to the punch but since I already wrote this and it breaks the expression down a little further:**

It's  a *regular expression* (aka regex or regexp) describing algorithmically the sequence you are trying to match in your text - in this case it's a rather tricky one because the [ and ] characters normally have a special meaning in regex syntax, so those need to be 'escaped' with backslashes in order to be interpreted as literal [ and ] characters - the non-escaped [ and ] are enclosing a character set, specifically

[abc] means match any single character a,b, or c

[^a] means match any single character *except* a

[^]] means match any single character except ]

[^]]\+ means match 1 or more consecutive characters excluding ] (but see ** below)

\[[^]]\+\] means match literal [ followed by 1 or more non-] characters followed by literal ] - the final ] maybe doesn't need to be escaped since ] without the matching [ preceding it doesn't have special meaning, however it's probably good practice to escape it for clarity

** Another quirk: for historical reasons grep  treats + as literal *unless* it's escaped; egrep does the opposite i.e.

```
egrep -o "\[[^]]+\]"
```is equivalent to

```
grep -o "\[[^]]\+\]"
```Hope I got that right! I told you it was a rather complicated one - anyhow you get the picture - there are several good intros on the web, e.g. 

[http://www.codeproject.com/Articles/939/An-Introduction-to-Regular-Expressions](http://www.codeproject.com/Articles/939/An-Introduction-to-Regular-Expressions)

Have fun - personally I would use MG&TL's awk expression ;)

---

