---
title: "comparing regex in a file to a given pattern"
date: 2011-01-11
forum: General Help
---

### Post by moody_mark on 2011-01-11
Hi, I have a file full of regex patterns that I want to check against a given text string or strings. For example:

patterns: 

12.0(30)SZ11
12.0(32)S15

regex: 

(12\.0\(.*\).*)

Now I can use egrep to specify a file where the regex is and compare this to a file where the pattern is like so

```

egrep -f regex pattern 
12.0(30)SZ11
12.0(32)S15
```

As you can see it returns the patterns that match. What I want to do is list the regexs that match not the pattern. In the case i'm using I have a very large number of regexes that I want to compare against a given pattern or patterns, so I can identify which regexes are incorrect. I dont think looking at the egrep man page I can do this but I could be wrong. Can anyone help? Thanks

---

### Post by bodhi.zazen on 2011-01-11
Try grep -v

---

### Post by moody_mark on 2011-01-12
Thanks, but grep -v will just return any entries in the "pattern" file that are not matching, for example

```
$ cat pattern 
12.0(30)SZ11
12.0(32)S15
12.1(33)S14

$ egrep -v -f regex pattern 
12.1(33)S14

```

---

### Post by bodhi.zazen on 2011-01-12
> **moody_mark said:**
> Thanks, but grep -v will just return any entries in the "pattern" file that are not matching, for example <clip>

I guess I do not understand what you want. From your first post you were asking for a list of what does not match, now you say this is not what you want.

> **moody_mark said:**
> What I want to do is list the regexs that match not the pattern.

grep [pattern] returns matches
grep -v [pattern] returns what does not

Between those two you should have what you seek, no /

:confused:

---

### Post by Vaphell on 2011-01-12
if i am not mistaken he wants to list the regex patterns that don't match anything in the file.

grep -c returns number of matches - if it's 0 then you have your malformed regex pattern
how do you test these regexes? shell script with a loop?

---

### Post by moody_mark on 2011-01-14
Sorry if I have confused anyone. I wanted to list the regexes that DO match, but not the pattern, the regex itself.

For example usually when we use grep we say:

```
grep "<regex>" <file>
```

this looks for lines in the file which match <regex>. Using grep -v will return anything that does not match. The results however are from the <file>. In this case this is not what im looking for. I would like to see <regex> for every match. Of course in the case of the above I would see <regex> all the time which is predictable. However lets say I have a few hundred lines each with a regex and I wanted to see which lines matched a given expression. I need something like:

```
grep <each regex in my file> <expression>

grep -f myregexlist 12.0(33)S
```

Now the file "myregexlist" could contain the following:

```
12.*
12\.0
12\.0.*
```

Of these only entries 1 and 3 would match I need to see which of these match, grep however will only show me the pattern not the regex:

```
$ cat regex 
12.*
12\.0
12\.0.*

$ cat pattern 
12.0(33)S

$ grep -f regex pattern 
12.0(33)S
```

I dont think grep is what I require here, any ideas?

---

### Post by SPr on 2011-01-14
```

#!/bin/bash
for regex in $(cat regex); do
	count=$(cat pattern| grep -c $regex)
	if [ $count -eq 0 ]
		then echo $regex
	fi
done

```
Is the closest I can get. The filenames ("regex" and "pattern") are hard coded.

---

### Post by bodhi.zazen on 2011-01-14
so you want basically to format the output so that you see something along the lines of:

```
Output:

patten foo
foo.1
foo.3
abc.foo

pattern bar
bar.5
barcode
```

I would script that, should be rather easy. You could use a bash script, perl, awk, or probably a number of other tools.

---

### Post by SPr on 2011-01-14
I thought you wanted a list of the regexs that don't match.
This one prints out the matching regular expressions:
```


#!/bin/bash
for regex in $(cat regex); do
	count=$(cat pattern| grep -c $regex)
	if [ $count -ne 0 ]
		then echo $regex
	fi
done

```

---

### Post by moody_mark on 2011-01-18
Thanks folks! Especially SPr, the script seems to have hit the nail on the head. Cheers!

---

