---
title: "Bash script to create folders from file names"
date: 2011-09-21
forum: General Help
---

### Post by r34ch on 2011-09-21
Hey everyone, newbie at the site. 

Been using Ubuntu on and off for a year now. While I usually take a hands on approach to learning this stuff, my new external HD has just arrived and I want to back everything up in a semi organised fashion asap.


I want to create a script to read the contents of a directory and create folders in that directory from the named files within and then move the corresponding files to their new folder.
i.e.

Desktop/Folder 1
file 1.doc
file 2.xls

would become

Desktop/Folder 1/file 1/
file 1.doc
Desktop/Folder 1/file 2/
file 2.xls

I tried this in Windows and the script collapsed when it ran into files named with spaces i.e "file 1.doc" creating a folder "file" and obviously not moving the corresponding file.

I tried the search function in the forums and of course google, but surprisingly for such a trivial (or so I thought) task I found very little.

Can anyone help me?

Cheers,
r34ch

---

### Post by sanderd17 on 2011-09-21
something like this:

```

for file in $( ls /home/user/Desktop/Folder ) 
do
    mkdir "/home/user/Desktop/Folder/${file%.*}"
    mv "/home/user/Desktop/Folder/$file" "/home/user/Desktop/Folder/${file%.*}/$file"
done

```

I did not test this. So tell me if you get errors, and try it on a test directory first.

---

### Post by nothingspecial on 2011-09-21
> **sanderd17 said:**
> something like this:

```

for file in $( ls /home/user/Desktop/Folder ) 
do
    mkdir "/home/user/Desktop/Folder/${file%.*}"
    mv "/home/user/Desktop/Folder/$file" "/home/user/Desktop/Folder/${file%.*}/$file"
done

```

I did not test this. So tell me if you get errors, and try it on a test directory first.

Well, the first line is Bash Pitfall no 1

see here

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

I'll leave sisco311 to explain the rest when he gets here later because no doubt I'll get it wrong anyway. :D

---

### Post by TeoBigusGeekus on 2011-09-21
It won't be the first time Sisco makes me look like a total hobgoblin so I'll give it a go:
[PHP]#!/bin/bash
find . -type f ! -name "*script*" | while read file;
do
    f=$(basename "$file")
    f1=${f%.*}
    mkdir "$f1"
    mv "$f" "$f1"
done[/PHP]
Name is as script, put it in the folder with the files you want moved, make it executable
```
chmod +x script
```
and run it
```
./script
```

---

### Post by TeoBigusGeekus on 2011-09-21
> **TeoBigusGeekus said:**
> It won't be the first time Sisco makes me look like a total hobgoblin...
:lolflag:

---

### Post by r34ch on 2011-09-21
> **TeoBigusGeekus said:**
> I'll give it a goSeems to work perfectly, thanks! :)

---

### Post by r34ch on 2011-09-22
Ok thanks everyone, you've now wet my whistle. :)

I want to learn a bit more on bash scripting and make a script myself that replaces "."s in a file name with spaces, except the last "." for the extension.

Where is a good site to start and what are a good few terms to google?

Cheers,
r34ch

---

### Post by nothingspecial on 2011-09-22
[This]("http://mywiki.wooledge.org/BashGuide") is the best place to start.

---

### Post by AlexOnVinyl on 2012-05-07
Is there anyway to make this compatible with Nautilus scripts - for an simple right-click and run?

I was looking for a script just like this for a while the only part that irritates me is I can't find one that will work with Nautilus.

> ex: ~/.gnome2/nautilus-scripts - then I can execute it by right clicking the file I want a directory made after.

PS. Sorry for reviving an old thread. Just looking for my answer and then I'll leave it to rest.

---

### Post by codemaniac on 2012-05-07
> **nothingspecial said:**
> [This]("http://mywiki.wooledge.org/BashGuide") is the best place to start.

I would also like to add abs guide to the list .A bit tough of a nut for a beginner though , still it has a array of tips and tricks in its bag .

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

