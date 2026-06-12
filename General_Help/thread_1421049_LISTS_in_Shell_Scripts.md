---
title: "LISTS in Shell Scripts"
date: 2010-03-03
forum: General Help
---

### Post by squareff255 on 2010-03-03
I've been trying to figure this out forever and I can't seem to figure out if there's a way to do this. Let's say I have a text file that just has a bunch of file names in it. For example:
```

~/Desktop/hello.txt
~/Videos/asdf.ogv
~/yourface.txt
etc.....html

```
So what if I wanted to pass that list into a command like the rm command? If I wanted to delete a bunch of files and they are scattered around. Like for instance, I used avg on my windows-box and >> to a file. So this file has a bunch of filenames from my windows partition and I wanted to grep the lines that say "Trojan horse" and send them to the rm command. IS THAT POSSIBLE?

Thanks all you geniuses!

---

### Post by bodhi.zazen on 2010-03-03
rm < file

---

### Post by Agent ME on 2010-03-03
> **bodhi.zazen said:**
> rm < file
rm doesn't read standard input.

You can do something like this, where you can substitute 'echo "file.txt"' for whatever command you want that lists files.
```
echo "file.txt" | while read line; do rm "$line"; done
```

If "list.txt" is a list of files to delete (one file per line), then this will do the trick:
```
cat list.txt | while read line; do rm "$line"; done
```
or alternately:
```
while read line; do rm "$line"; done < list.txt
```

---

### Post by kaibob on 2010-03-03
> **squareff255 said:**
> So what if I wanted to pass that list into a command like the rm command? If I wanted to delete a bunch of files and they are scattered around. Like for instance, I used avg on my windows-box and >> to a file. So this file has a bunch of filenames from my windows partition and I wanted to grep the lines that say "Trojan horse" and send them to the rm command. IS THAT POSSIBLE?

The following command uses grep to find lines that match a specified string and then pipes that line to the rm command. You may want to substitute echo for rm until you are sure that all is working well. 

```
grep "Trojan horse" file.txt | while read line ; do rm "$line" ; done
```

BTW, I didn't quite understand the part about your Windows partition, since all the files appear to be in your home directory.

EDIT:
The above command appears not to properly expand the tilde, so this command will not work if the text file is as shown. You could preprocess the text file with sed to substitute your actual home directory for ~ but that's a bit of a kludge. I'll look into this a bit more.

---

### Post by falconindy on 2010-03-03
> **Agent ME said:**
> rm doesn't read standard input.

You can do something like this, where you can substitute 'echo "file.txt"' for whatever command you want that lists files.
```
echo "file.txt" | while read line; do rm "$line"; done
```

If "list.txt" is a list of files to delete (one file per line), then this will do the trick:
```
cat list.txt | while read line; do rm "$line"; done
```
or alternately:
```
while read line; do rm "$line"; done < list.txt
```
Or simply:
```
rm $(cat file)
```

No need to make things more complex than they need to be.

---

### Post by kaibob on 2010-03-03
Deleted by kaibob

---

### Post by Agent ME on 2010-03-03
> **falconindy said:**
> Or simply:
```
rm $(cat file)
```
That won't delete files that have spaces in their names. Doing 'rm "$(cat file.txt)"' instead will delete a single file with a space in its name, but fails if file.txt has more than one file listed in it.

> **kaibob said:**
> The following command uses grep to find lines that match a specified string and then pipes that line to the rm command. You may want to substitute echo for rm until you are sure that all is working well. 

```
grep "Trojan horse" file.txt | while read line ; do rm "$line" ; done
```
That line doesn't look right. Do the files you want to delete have "Trojan horse" as part of their filename? If not that won't work. Can you give an example of what file.txt looks like?

---

### Post by kaibob on 2010-03-03
> **Agent ME said:**
> That line doesn't look right. Do the files you want to delete have "Trojan horse" as part of their filename? If not that won't work. Can you give an example of what file.txt looks like?
In his post, the OP states:

> ...I used avg on my windows-box and >> to a file. So this file has a bunch of filenames from my windows partition and I wanted to grep the lines that say "Trojan horse" and send them to the rm command. IS THAT POSSIBLE?

I assumed that AVG actually renamed the files by appending "Trojan horse", although in retrospect I agree that it does seem unlikely. An example of the text file showing the context of the string, Trojan horse, would certainly be helpful.

---

### Post by asmoore82 on 2010-03-03
> **falconindy said:**
> Or simply:
```
rm $(cat file)
```

No need to make things more complex than they need to be.

:lolflag:
when you are going to make such a huge mistake, it's always best to do it with `rm`

As already mentioned, this breaks badly if filenames have spaces or any IFS characters in them.
It wouldn't be quite as amusing if it weren't followed by the "complex" statement.

---

### Post by squareff255 on 2010-03-04
WOW! Thanks guys! That's awesome! :)

---

### Post by squareff255 on 2010-03-17
btw, rm $(cat files.txt) worked the best. I had a file called files.txt and each line in the file was a different file name and it deleted all of them. Thanks for everything guys.

---

