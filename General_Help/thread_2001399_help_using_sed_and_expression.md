---
title: "help using sed and expression"
date: 2012-06-10
forum: General Help
---

### Post by spiritech on 2012-06-10
i have a a file, each line is along the format of-

name-of-file.avi
name-of-file.flv
name-of-file.mkv

there are quiet a few lines. i am using sed to try and automatically detect and replace the occurrence  of . followed by any number of letters or numbers. the code i am using is shown below, and is not working.

sed 's/\..{0,}$/\.mp4/g' input

i have used the first part     's/\.     to be literal dot, then the next part     .{0,}    to be followed by 'any' number of characters greater than 0    and of course the    $     to indicate the end of line. i was not sure if i needed something between the two dots, to make the second dot mean any instaed of literal.

spiritech

---

### Post by papibe on 2012-06-10
Hi spiritech.

I have the impression that your problem could be easier to solve using bash parameter substitution than using 'sed'.

However as now, I don't understand what you are trying to do. Could you post an example of the input, and the desired output.

Regards.

---

### Post by spiritech on 2012-06-10
all in all i would like to replace the last occurrence of . (and any number, type of characters.) of each line of the file, with, well whatever i want.

i would like to achieve it through sed and regular expression.

if i do it manually by putting .avi or .mkv into the first // it works. i just can not figure out the expression for . (any number , type of character)

---

### Post by papibe on 2012-06-10
An idea showing parameter substitution.
```
while read -r var
do
    echo "normal: $var"
    echo "nodots: ${var//./}
done < input
```
Hope it helps,
Regards.

---

### Post by SeijiSensei on 2012-06-10
By default sed does not use "extended" regular expressions.  I had a problem similar to yours the other day and discovered I needed to use the "-r" switch to get sed to recognize the regex I was using.  However I'd probably use a slightly more stringent regex in your case:

```
sed -r 's/\.[a-zA-Z]+$/.mp4/g'
```

That requires that there be at least one alphabetic character after the dot and before the end of the string.

In the specific case you describe, all the extensions have three letters.  So an even more stringent test would be:

```
sed -r 's/\.[a-zA-Z]{3}+$/.mp4/g'
```

You can also avoid the problem of case sensitivity like this:

```
tr 'A-Z' 'a-z' < /path/to/some/file | sed -r 's/\.[a-z]{3}$/.mp4/g' > /path/to/some/newfile
```

That forces all the lines to lower case before applying sed.

---

### Post by Vaphell on 2012-06-10
expanding on papibe's idea of bash solution, substitution of ".(3 chars)" would look like this:
```
ext="mp4"
while read -r var
do
    echo "normal: $var"
    echo "new ext: ${var%.???}.$ext"
    echo "new ext(2): ${var%.[a-zA-Z][a-zA-Z][a-zA-Z0-9]}.$ext"
done < input
```

> ```
sed -r 's/\.[a-zA-Z]{3}[COLOR="Red"]+[/COLOR]$/.mp4/g'
```
obviously a typo

---

### Post by kjohri on 2012-06-11
sed "s/\...*/replacement-string/" <input-filename>

---

### Post by spiritech on 2012-06-11
> **SeijiSensei said:**
> By default sed does not use "extended" regular expressions.  I had a problem similar to yours the other day and discovered I needed to use the "-r" switch to get sed to recognize the regex I was using.  However I'd probably use a slightly more stringent regex in your case:

```
sed -r 's/\.[a-zA-Z]+$/.mp4/g'
```That requires that there be at least one alphabetic character after the dot and before the end of the string.


thank you. the -r option solved my problem. my code was correct.

sed -r 's/\..{0,}$/\.mp4/g' input

---

### Post by SeijiSensei on 2012-06-11
> **spiritech said:**
> thank you. the -r option solved my problem. my code was correct.

sed -r 's/\..{0,}$/\.mp4/g' input

That's fine as long as you realize that the regex you're using will match anything that ends in a dot followed by a non-zero bunch of characters.  Since you know what the source file contains, it's not going to matter in this case, but it would if you had a file where you wanted to rewrite entries that end in ".mkv" but not ".exe".  Then you'd need something a lot more specific.

---

### Post by spiritech on 2012-09-25
i have marked this thread as unsolved as after testing a little further the solution below does not work.

sed -r 's/\..{0,}$/\.mp4/g' file

the above command should match a . followed by any number and type of character at the end of a string. instead when i run the command on the file, it matches the first occurrence of a . followed by any number and type of character.

---

### Post by steeldriver on 2012-09-25
That would be because sed always does a 'greedy' match, I think - you could get around it by replacing the . (any char) with [^.] (any char except literal dot - doesn't need escaping inside a [ ] character list)

```
$ echo "file.part.xyx" | sed -r 's/\.**[COLOR=Red].[/COLOR]**{0,}$/\.mp4/g'
file.mp4
$
$ echo "file.part.xyz" | sed -r 's/\.**[COLOR=Red][^.][/COLOR]**{0,}$/\.mp4/g'
file.part.mp4

```Personally I would probably use the old school * instead of {0,} just to make it a bit more compact - also afaik you don't need the 'g' if each filename is on a separate line

```
$ echo "file.part.xyz" | sed -r 's/\.[^.]*$/\.mp4/'
file.part.mp4
```

---

### Post by HiImTye on 2012-09-25
this should work:
```
... | sed 's|\..*$|.whatever_you_want|g' | ...
```

---

### Post by spiritech on 2012-09-27
> Personally I would probably use the old school * instead of {0,} just to make it a bit more compact - also afaik you don't need the 'g' if each filename is on a separate line

```
$ echo "file.part.xyz" | sed -r 's/\.[^.]*$/\.mp4/'
file.part.mp4
```

thankyou steeldriver.

this option worked for me. 

while we are on the subject of file substitution, what is best for ram strings, sed, tr. or another substitution program.

example

cat file | sed 's/word/another-word' | sed 's/^/"/' | and so on

---

### Post by steeldriver on 2012-09-27
sry, what are ram strings?

---

### Post by Vaphell on 2012-09-27
maybe raw?
either way - it's good to know all common text mod programs as they lend themselves to different scenarios, eg
- fuel script with data stored in a file - bash (while read)
- quickly remove/replace particular chars - tr
- modify text lines and optionally reuse their parts - sed
- awk - full blown programming language that can do all of the above and more, but can be more verbose than specialized tools in some scenarios

---

### Post by spiritech on 2012-09-27
> **steeldriver said:**
> sry, what are ram strings?

the reason i called it ram strings is the fact you can string text together in the ram, instead of manipulating the file itself.
unless this is traditionally called something else.

---

### Post by spiritech on 2012-09-27
below is an example of code i am using to change a text file.

cat file | sed -r 's/word/new-word/' | sed -r 's/^/"/' | sed -r 's/$/"/'

is there a way i can do the sed substitutions without writing sed -r every time.

so something like this

cat file | sed -r 's/word/new-word/' then  's/^/"/' then 's/$/"/'

---

### Post by spiritech on 2012-09-27
> **Vaphell said:**
> maybe raw?
either way - it's good to know all common text mod programs as they lend themselves to different scenarios, eg
- fuel script with data stored in a file - bash (while read)
- quickly remove/replace particular chars - tr
- modify text lines and optionally reuse their parts - sed
- awk - full blown programming language that can do all of the above and more, but can be more verbose than specialized tools in some scenarios

thankyou, i will have a look at awk.

and thakyou to everyone else who has helped me. :)

---

### Post by steeldriver on 2012-09-27
specifically related to your previous q, you might want to look at the -e and -f options to sed (also note there's no need to cat the file - sed can take the input file name as an argument):

```
sed -r -e '*expression*' -e '*another expression*' -e '*yet another expression*' file
``````
sed -r -f *expressionfile *file
```where expressionfile contains a list of expressions, i.e.

```
*expression*
*another expression*
*yet another expression*
```or even create an interpreted sed script

```
#!/bin/sed -f

*expression*
*another expression*
*yet another expression*
```

---

### Post by HiImTye on 2012-09-27
on *ram strings*, you mean stdin/stdout. anything that processes stdin/stdout is sufficient, so long as it meets your other needs.

---

### Post by HiImTye on 2012-09-27
> **spiritech said:**
> cat file | sed -r 's/word/new-word/' | sed -r 's/^/"/' | sed -r 's/$/"/'
this can be rewritten as
```
sed -r 's/word/new-word/;s/^/\"/;s/$/\"/' file
```but you might want to use the 'g' option, if you want to repeat the process at each instance, eg.
```
sed -r 's/word/new-word/g;s/^/\"/g;s/$/\"/g' file
```I always use pipes instead of slashes, to avoid picket fencing, eg.
```
sed -r 's|word|new-word|g;s|^|\"|g;s|$|\"|g' file
```as you can see, it's much easier to read escaped characters without the picket fencing

---

