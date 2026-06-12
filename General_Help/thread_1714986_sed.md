---
title: "sed"
date: 2011-03-26
forum: General Help
---

### Post by pizet on 2011-03-26
Hello, if I have an input string:
{something}{some character}{n}
how can I replace it for:
{something}{other character}{n}?

So for example:
input: asdfjoaaaa
ouput: asdfjobbbb.

I hope it's not too silly question. :)

Thank you for help.

---

### Post by TeoBigusGeekus on 2011-03-26
Does your input string follow some pattern?
Do you want to replace the string "aaaa" or the last 4 characters of your input?

---

### Post by amauk on 2011-03-26
Will replace 'aaaa' with 'bbbb', if 'aaaa' are the last 4 characters of input

```
echo 'asdfjoaaaa' | sed 's|\(.*\)a\{4,4\}$|\1bbbb|'
```

---

### Post by pizet on 2011-03-26
Well, to be more percise I want to replace *n* characters from the back of the string with *n* other characters. The problem is, that I don't know how to write a correct replacement string for sed to solve this. Maybe it requires something I'm not aware of yet. Thanks.

---

### Post by pizet on 2011-03-26
> **amauk said:**
> Will replace 'aaaa' with 'bbbb', if 'aaaa' are the last 4 characters of input

```
echo 'asdfjoaaaa' | sed 's|\(.*\)a\{4,4\}$|\1bbbb|'
```

Ok, sorry ... I thought it was obvious, that I *don't know percisely,* how many characters am I going to replace.

---

### Post by amauk on 2011-03-26
Ok, then it's a little more complex and will probably need to be done in a script

Something like
```
#!/bin/bash

if [ -z "$1" ] || [ -z "$2" ]; then
	exit 1
fi

IFS=$'\n'
END_CHARS=$(echo "$1" | grep -o "[$2]\+$")
BEG_INPUT=$(echo "$1" | sed "s|${END_CHARS}$||")
END_CHARS=$(echo "$END_CHARS" | sed "s|$2|$3|g")
echo "${BEG_INPUT}${END_CHARS}"
```

Arg1 = Your string
Arg2 = end character to replace
Arg3 = Replacement character

```
./end_char_replace "asdfjoaaaaaaaaaaaa" a b
asdfjobbbbbbbbbbbb
```

---

### Post by cipherboy_loc on 2011-03-26
Mine is:

```

echo 'asdfjoaaaa' | sed "s/a\{1,\}\$/$(echo 'asdfjoaaaa' | grep -io '[a]\{1,\}$' | sed 's/a/b/g')/g"

```

You will have to replace it twice, but if you use an environment variable, you could do something like this:

```

STRING='asdfjoaaaa'
echo $STRING | sed "s/a\{1,\}\$/$(echo $STRING | grep -io '[a]\{1,\}$' | sed 's/a/b/g')/g"

```



Cipherboy

---

### Post by pizet on 2011-03-26
Ok, thanks to all.

---

### Post by DaithiF on 2011-03-27
```
$ echo "asdfjoaaaa" | sed -e :a -e 's/a\(a*\)$/b\1/;ta'
asdfjobbbb

```

---

