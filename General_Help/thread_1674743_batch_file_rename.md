---
title: "batch file rename"
date: 2011-01-24
forum: General Help
---

### Post by sn0m on 2011-01-24
hi chaps, can someone help me rename a batch of files.
ie:
I've got about 12 jpeg files that I have been playing with rename, obviously they all have wired names now. My aim is to rename them with numbers, ie 1 2 3 ...12 and use them in the xml script to create a rotating background. 
I'm trying the following option: rename -v 's/./1-12' *
but it is not working.
Can someone spare me any further pain and tell me how to get perl to rename them with numbers 1-12.
Thanks
Sokol

---

### Post by asmoore82 on 2011-01-24
I'll have to confess that I don't know Perl and I only use the real `rename` tool off of
the example in the manpage to go from uppercase to lowercase.

But you can do this with the BASH shell:
```
count="0"
for file in *.jpg
do
    mv -iv "$file" "$((++count)).jpg"
done
```

P.S. Here's a little fancier version
to avoid colliding with existing filenames:
```
count="1"
for file in *.jpg
do
    while [ -f "$count.jpg" ]
    do
        ((++count))
    done
    mv -iv "$file" "$count.jpg"
    ((++count))
done
```

---

