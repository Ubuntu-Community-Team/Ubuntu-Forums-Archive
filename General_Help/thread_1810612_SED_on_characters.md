---
title: "SED on characters?"
date: 2011-07-23
forum: General Help
---

### Post by zero2xiii on 2011-07-23
Hay all.

I have a simple problem:

I want to use a script to "scramble" a text file's content using a "algorithm" file with sed. But I can t figure out how to swap characters instead of words within the file.

I want to do this for example:

```

Algorithm:
a > b
c > e
t > z

Input:
Cat C A T Cats

Output:
ebz e b z ebzs

```

I can swap out entire words, but this is not practical for my usage.

How can the SED syntax be formatted to do this? The commands will be in a text file called by sed with the -f flag..

Thanks in advance.

---

### Post by zero2xiii on 2011-07-31
Bump

---

### Post by idoitprone on 2011-07-31
```
echo "Cat C A T Cats" | sed -e 's/C/e/gi' -e 's/a/b/gi' -e 's/t/z/gi'
ebz e b z ebzs


```

---

### Post by zero2xiii on 2011-07-31
Nope,

The output file is blank?

Here is the script snippit I use:

```

cp $file $file.enc
	file=$file.enc
		
	while [ $times -gt 0 ]
	do 
	#echo $times
	sed -e -f algo_en.txt $file > $file.enc
	#mv $file.enc $file
		times=$(($times - 1))
	done

```

And the file algo_en.txt:

```

s/a/b/gi
s/b/c/gi
s/c/d/gi
s/d/e/gi
s/e/f/gi
s/f/g/gi
s/g/h/gi
s/h/i/gi
s/i/j/gi
s/j/k/gi
s/k/l/gi
s/l/m/gi
s/m/n/gi
s/n/o/gi
s/o/p/gi
s/p/q/gi
s/q/r/gi
s/r/s/gi
s/s/t/gi
s/t/u/gi
s/u/v/gi
s/v/w/gi
s/w/x/gi
s/x/y/gi
s/y/z/gi
s/z/a/gi

```


What am I missing?

---

### Post by zero2xiii on 2011-07-31
Appon creating a test script:

```
#!/bin/bash

read file

sed -f  algo_en.txt $file > $file.enc

```

With input:

```
test
jk
j
```

I get output:

```
aaaa
aa
a
```

This is the only way I got output (removing the -e from the command).

When I include -e it gives me error:

```
sed: -e expression #1, char 1: unknown command: `-'
```

:confused:


I now changed the algo_en.txt file to include the -e operant:

```
-e 's/a/b/gi'
-e 's/b/c/gi'
-e 's/c/d/gi'

and so forth
```

now i get error

```
sed: file algo_en.txt line 1: unknown command: `-'

```

---

### Post by idoitprone on 2011-07-31
> **zero2xiii said:**
> Nope,

The output file is blank?

Here is the script snippit I use:

```

cp $file $file.enc
    file=$file.enc
        
    while [ $times -gt 0 ]
    do 
    #echo $times
    sed -e -f algo_en.txt $file > $file.enc
    #mv $file.enc $file
        times=$(($times - 1))
    done

```And the file algo_en.txt:

```

s/a/b/gi
s/b/c/gi
s/c/d/gi
s/d/e/gi
s/e/f/gi
s/f/g/gi
s/g/h/gi
s/h/i/gi
s/i/j/gi
s/j/k/gi
s/k/l/gi
s/l/m/gi
s/m/n/gi
s/n/o/gi
s/o/p/gi
s/p/q/gi
s/q/r/gi
s/r/s/gi
s/s/t/gi
s/t/u/gi
s/u/v/gi
s/v/w/gi
s/w/x/gi
s/x/y/gi
s/y/z/gi
s/z/a/gi

```What am I missing?

[http://www.grymoire.com/Unix/Sed.html#uh-20](http://www.grymoire.com/Unix/Sed.html#uh-20)

two things i have to say. s/y/z/**gi **
the last two letters are the global flag and ignore case. Remeber that even you make a script next time. Look at that link. This looks like a homework assignment so i not doing everything for you

---

### Post by zero2xiii on 2011-07-31
> This looks like a homework assignment so i not doing everything for you

Haha I wish it was? But I dont expect you to do everything for me. I've used the -f flag before to call a file as arguments, I just cant get it to work on replacing the single characters instead of the entire word.

> [http://www.grymoire.com/Unix/Sed.html#uh-20](http://www.grymoire.com/Unix/Sed.html#uh-20)

I am looking at it, reading it, but this is what I am doing, it's just not responding as I expect it to be?

I will fiddle some more, maybe my syntax is somewhere errorous.

---

### Post by zero2xiii on 2011-07-31
Oka.

Script
> #!/bin/bash
read file
sed -f algo_en.txt <$file > $file.enc

using algo_en.txt:
```
s/t/a/g
s/j/b/g
```

on file test.txt:
```
test
jk
j
```

yields test.txt.enc:
```
aesa
bk
b
```

which is correct.

But substituting the algo_en.txt file for the one posted firs (with all the letters a - z) gives the output of:

```
aaaa
aa
a
```

This is what I cant get to work?

I assume this is what is happening:
Input "abcd"

Then, "a" gets changed to "b"
then, "bb" gets changed to "cc"
then, "ccc" gets changed to "ddd"
then, "dddd" gets changed to "eeee"
then, "eeee" gets changed to "ffff"
and so forth until:
"zzzz" gets changed to "aaaa" and the sed commands are done.

Thus the output is "aaaa" as in this example.

This is where my problem comes in. Is what I want to do then possible with sed? Seems like a loop error?

---

### Post by AlphaLexman on 2011-07-31
```
echo 'the quick brown fox jumps over the lazy dog' | sed 'y/abcdefghijklmnopqrstuvwxyz/bcdefghijklmnopqrstuvwxyza/'
```

---

### Post by zero2xiii on 2011-07-31
```
sed 'y/abcdefghijklmnopqrstuvwxyz/bcdefghijklmnopqrstuvwxyza/'
```

Thats much closer to what I want to do. Thanks :)

Will look if this works in context of the entire program

Edit:
Awesome! Works perfectly, even on multiple passed and other SED commands putten inbetween passes :).. Thanks alot. Dont know how I missed that, but I looked up the meaning of the "y" and it does EXACTLY what I want it to...

---

