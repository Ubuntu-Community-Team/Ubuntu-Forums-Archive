---
title: "Beyond my bash(or google)-fu - Upper case letters regex"
date: 2010-03-26
forum: General Help
---

### Post by nothingspecial on 2010-03-26
I just did this
```

#!/bin/bash
for f in *; do
g=`expr "xxx$f" : 'xxx\(.*\)' | tr '[A-Z]' '[a-z]'`
mv "$f" "$g"
done 
```

to rename a load of mp3 files that were completly upper case to lower case. Worked a treat. :p

So, 
THE STRANGLERS - ALWAYS THE SUN.mp3

has become

the stranglers - always the sun.mp3

and many thousands of others.

I would like to change the first letter of each word back to uppercase.

ie

The Stranglers - Always The Sun.mp3

But the regular expression is beyond me. Any help?

Thanks.

---

### Post by falconindy on 2010-03-26
The perl based rename utility is what you're looking for.

```
rename 's/(\b\S+)/\u$1/g' *
```
You can add the -n flag to look over the output before committing to it.

---

### Post by nothingspecial on 2010-03-26
Thanks alot.

Brilliant.

I`d be grateful if you could explain the syntax.

I don`t mind if you don`t have time though because when I have time I can find out myself.

Again, thanks ever so much for that.

---

### Post by falconindy on 2010-03-26
It's actually fairly simple. I don't know perl regex all that well, but I know a few good reference sites and I was able to scrape this together with a little bit of tinkering (and some luck). The standard form of the regex is as follows:

s/find/replace/

's' for search. The 'g' at the tail end means global. Without the g, it would stop searching after it found and replaced the first valid instance of the pattern.

\b finds word boundaries: spaces (and i think newlines as well).
\S finds a single letter
+ is a modifier that signifies that we want to match 1 to many of the expression (letters, in this case).

\u translates the next letter to uppercase.
$1 is a replacement for the pattern we captured in the the find expression (wrapped by parenthesis).

---

### Post by nothingspecial on 2010-03-26
> **falconindy said:**
> It's actually fairly simple. I don't know perl regex all that well, but I know a few good reference sites and I was able to scrape this together with a little bit of tinkering (and some luck). The standard form of the regex is as follows:

s/find/replace/

's' for search. The 'g' at the tail end means global. Without the g, it would stop searching after it found and replaced the first valid instance of the pattern.

\b finds word boundaries: spaces (and i think newlines as well).
\S finds a single letter
+ is a modifier that signifies that we want to match 1 to many of the expression (letters, in this case).

\u translates the next letter to uppercase.
$1 is a replacement for the pattern we captured in the the find expression (wrapped by parenthesis).

Thanks again.

I almost get it - I think.

I`m going to have a play.

Once again, thanks.

---

### Post by picpak on 2010-03-28
Doing some forum searching, I found this:

[http://ubuntuforums.org/showpost.php?p=460602&postcount=4](http://ubuntuforums.org/showpost.php?p=460602&postcount=4)

Wow, what a life-saver!

---

