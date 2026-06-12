---
title: "bulk change filenames to &quot;cat names-list.txt&quot;"
date: 2010-03-29
forum: General Help
---

### Post by cyprys on 2010-03-29
I'm looking for something like:
```
for x in *.mkv; do rename "$x" "${line_from_filenames.txt}.mkv"; done;
```

ls -1 ~/kids/movies/*.mkv
```
00.20080903fckdlowp.mkv
01.20080911fckdl2fd.mkv
02.20080925fckdlgrs.mkv
03.20081026fckdlbh7.mkv
04.20081206fckdli90.mkv
05.20090214fckdmkni.mkv
06.20090301fckdmer5.mkv
```

cat filenames.txt
```
back horse riding
maria's first steps
going school
the birthday
santa is coming to town
valentine's day
boys playing ninjas
```

**wc -l < filenames.txt**
equals to
**ls ~/kids/movies/*.mkv | wc -l**

---

### Post by sisco311 on 2010-03-29
try something like:
```
i=0
for file in ~/kids/movies/*.mkv; do 
  ((i++))
  echo mv -b "$file" "$(sed -n ${i}p /path/to/filenames.txt)"
done
```

---

### Post by cyprys on 2010-03-29
Thanks, it worked. There was a bunch of files ended with "\r" after I tried it but quick command fixed it. Putting it here for other users:
```
rename 's/\r/.avi/' ~/kids/movies/*
```
(perl-based *rename* might be not installed on other distributions)


edit: What does "((" and "))" make? I'm marking this thread solved. Thanks again.

---

### Post by sisco311 on 2010-03-29
> **cyprys said:**
> Thanks, it worked. There was a bunch of files ended with "\r" after I tried it but quick command fixed it. Putting it here for other users:
```
rename 's/\r/.avi/' ~/kids/movies/*
```
(perl-based *rename* might be not installed on other distributions)


edit: What does "((" and "))" make? I'm marking this thread solved. Thanks again.

You're welcome!

[http://www.softpanorama.org/Scripting/Shellorama/arithmetic_expressions.shtml](http://www.softpanorama.org/Scripting/Shellorama/arithmetic_expressions.shtml)

```
man bash | less +/^ARITHMETIC\ EVALUATION
```
```
man bash | less +/"((expression))"
```

Sorry, it's 01:50am here, i think, the link and the man pages will explain the meaning of  "((expression))" better than me...  :)

EDIT: it increments i, it's a C style bashism. :evil:

---

### Post by cyprys on 2010-03-29
I'ts 01:03am here ;) I'll gladly read man in the morning. Thanks for the kick in the right direction.

Oh, so you use "**((i++))**" as an equivalent to "**let i++**" - got it.

---

### Post by kaibob on 2010-03-29
Cisco311's solution is simplest and thus best, and the thread is solved, but I wanted to give this a try anyways.

```
#!/bin/bash

IFS=$'\n'

newfile=( $(<filenames.txt) )

i=0

for file in *.mkv ; do 
   cp $file ${newfile[$i]}
   i=$((i+1))
done
```

---

### Post by cyprys on 2010-04-03
Works like a charm. I just gave it a try changing names of 500+ photos. I also added numbering from '001' like below:

```
#!/bin/bash

IFS=$'\n'
newfile=( $(<comments.txt) )

i=0

for photo in *.JPG ; do
   if [ $i -lt 9 ]; then x=00; elif [ $i -lt 99 ]; then x=0; else x=''; fi;
   mv "$photo" "$x$((i+1)) - ${newfile[$i]}.jpg"
   ((i++))
done
```

---

### Post by kaibob on 2010-04-03
In another thread, geirha used a file descriptor, which was a new concept to me. I studied this topic a bit and decided to see if it might be applicable here. I wrote the following shell script, and it does seem to work. This is another--but not necessarily better--way to perform the task at hand.  

```
#!/bin/bash

count=001

exec 3< comments.txt

for photo in *.jpg ; do
   read -r -u 3 newphoto
   mv "$photo" "${count} - ${newphoto}.jpg"
   count=$(printf "%03d" $((count+1)))
done
```

---

