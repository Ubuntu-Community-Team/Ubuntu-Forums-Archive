---
title: "Need help with a bash script"
date: 2010-05-27
forum: General Help
---

### Post by m6a2x6 on 2010-05-27
Hi!

I need help with some sh script I would like to run. I have a folder1/ which contains few hundreds of folder1/subfolder1/file1.

I want all files within subfolders so they are all like folder1/file1 and I can delete all subfolders.

So i would need a script which does like that (pseudocode):

> 
for each folder in folder1
{
    for each file in folder
    {
        mv folder/file folder1/
    }
    rm folder
}


Problem is, i know nothing about bash scripts and I don't want to mess this one :-p

Anyone could point me on how to do such a thing?

---

### Post by -humanaut- on 2010-05-27
[http://tldp.org](http://tldp.org) <--- Plenty of helpful articles here to help you write a bash script.

---

### Post by geirha on 2010-05-27
I'm not entirely sure I understand what you want to do, but it sounds like you want:
```

cd folder1 && 
for file in ./*/*; do
  echo mv -iv "$file" .
  echo rmdir -v "${file%/*}"
done

```
(Added echos in front of the commands so it doesn't actually move or remove anything, just prints the commands it would've run if those echos weren't there)

As a beginner, stay away from the Advanced bash-scripting guide and the other bash guides at [http://tldp.org](http://tldp.org)

I recommend:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

EDIT: Actually the code I posted above is silly. You just need two commands

```

cd folder1
mv -vi ./*/* .
rmdir -v ./*/

```

---

### Post by lostinxlation on 2010-05-27
No need to write a script.. Back quotation is your friend.
But you need to make sure the file names don't conflict otherwise some of them would be overridden. 
 
cp `find <full path to directory1> -name "*" -print` <full path to directory1>
 
It will give you warnings about copying directory, but it's harmless as long as you don't put a -r option to cp command. **I wouldn't recommend to use mv command in this method**.

---

### Post by m6a2x6 on 2010-05-27
Thank you!

Worked perfectly! I'll learn a little about those so useful scripts ;-) saved me LOTS of time :-p

---

### Post by geirha on 2010-05-27
> **lostinxlation said:**
> No need to write a script.. Back quotation is your friend.
But you need to make sure the file names don't conflict otherwise some of them would be overridden. 
 
cp `find <full path to directory1> -name "*" -print` <full path to directory1>
 
It will give you warnings about copying directory, but it's harmless as long as you don't put a -r option to cp command. **I wouldn't recommend to use mv command in this method**.

That's terrible advice; it will break for files containing whitespace and glob characters. It might work in a simple case, but learning a proper way is much better.

---

