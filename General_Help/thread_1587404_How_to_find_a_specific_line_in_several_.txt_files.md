---
title: "How to find a specific line in several .txt files ?"
date: 2010-10-03
forum: General Help
---

### Post by manco1911 on 2010-10-03
Hi, first of all im still new on the CLI, but trying to improve.. 
I installed a ubuntu server at home on which i configured ssh so the only way i can interact is via Terminal. 

What i want to do:
find all .txt files in a directory.
read all lines of the .txt files.
find a specific word on those lines.
obtain the whole line and know on which file (full path) was found.


What i tried: 

#find *.txt | grep magic_word | tee results.txt

Of course with no positive results. 

I think what i need to do would be something like this (but i cant make it work):

#find *.txt | cat "something" | grep magic_word | tee results.txt

The thing is that i dont know how to cat all the *.txt results from the find command. 

Any advice ?

---

### Post by linux-hack on 2010-10-03
Well you could try sed ... 

and for you command I think it should be like this :

```
(find / -type f -name "*.txt" -exec cat {} \; | grep magic_word) > result.txt
```

---

### Post by ragtag on 2010-10-03
Wouldn't this work?

```

find *.txt -exec grep -Hn magic_word {} \;

```


You can also use grep -Rn to recursively grep through files and folders.

---

### Post by btindie on 2010-10-03
Try this:
```
find /path/ -name '*.txt' -exec grep -Hn magic_word '{}' \;
```

---

### Post by manco1911 on 2010-10-03
linux-hack, your line didnt exactly pulled it off, but is simillar to the following ones, which did the job. 
Thanks anyway.

ragtag & btindie, thanks, that was what i was looking for. 

For others to know, the results on their commands is:


path/file_name.txt:number_of_line_of_magic_word:line_with_magic_word


Thanks a lot guys. 
-------------------------------------------------------------
edit
Just to know,  "-exec" what exactly does in there?

Just read man file.. i should do this more often. 
Thanks guys for your responses.

---

### Post by The Cog on 2010-10-03
How about:
**grep magic_word *.txt**

---

### Post by epicoder on 2010-10-03
Another useful method that is nice to know is 
for file in *.txt; do cat $file | grep magic_word; done

---

