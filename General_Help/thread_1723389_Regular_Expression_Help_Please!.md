---
title: "Regular Expression Help Please!"
date: 2011-04-07
forum: General Help
---

### Post by eraye1 on 2011-04-07
Hey everyone,

I have a file that is a list of words.  I want to remove any lines that have characters other than a small set of characters that I specify.  

For example,

set{a,b,c}

on

aa
ab
cc
df
ad
ff

Would result in:

aa
ab
cc

only.  

How should I do this?  Can I use sed or awk?  Or should I script this somehow.  Any help would be greatly appreciated!

---

### Post by LewRockwellFAN on 2011-04-07
I'm sure you could do this with a word processor macro. I'm pretty sure I could do it with ZenWord but I doubt if you have that since it was current when MS-DOS 3.2 was new, a 10 mb hard drive was a big deal, and Al Gore hadn't invented the internet. But if ZW could do it I'd be surprised if Open Office can't. You need to search for every character that is forbidden and delete the lines they occur on. There are other ways you could do this, probably more sophisticated ways involving if statements and so on but that is a quick an dirty approach that should work.

PS edit to make this clear. I mean you write a macro to do the above, not do it manually. Then you tell it to do the macro a gazillion times and it quits when it runs out of stuff to do.

---

### Post by nothingspecial on 2011-04-07
I'm not sure I understand you propperly.

To remove any line that contains any letter other than a, b or c but may include them
```

$ cat blag.txt

aa
ab
cc
df
ad
ff
abcabcabc
abcdbc
efgf
efbfg

$ sed '/[d-z]/d' blag.txt 

aa
ab
cc
abcabcabc
```

To keep any line that has an a or b or c in it but can contain other letters

```
$ sed '/[a-c]/!d' blag.txt 
aa
ab
cc
ad
abcabcabc
abcdbc
efbfg
```

---

