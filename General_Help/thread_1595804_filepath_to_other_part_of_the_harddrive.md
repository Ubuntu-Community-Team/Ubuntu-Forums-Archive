---
title: "filepath to other part of the harddrive"
date: 2010-10-13
forum: General Help
---

### Post by nearlymagicman on 2010-10-13
Hey,


i have 4 different harddriveparts (i hope that is the correct translation), on my PC, one for the OS (ubuntu) and 3 others for programms and documents for example. But now i need to go in a folder on another part in the console.

The other part has the id E61441A014417519, so i would guess that the order you have to enter would be: "cd \media\E61441A014417519\folder" and then i would be "in" the folder, but the console said that there is not even a folder named "E61441A014417519". What am i doing wrong?

Thanks for your time and help

---

### Post by Vaphell on 2010-10-13
are these partitions mounted automatically? do you see them in 'Places' menu and can you access them with filebrowser?

---

### Post by nearlymagicman on 2010-10-13
yes i can, that is how i got the exact filepath copied, i am trying to use:"/media/E61441A014417519/Uni/AufgabenSetI/Aufgabe 1.2(build.xml)" But the console doesn't recognize it.

---

### Post by nearlymagicman on 2010-10-13
I guess i fixed it, sadly the console cannot work with spaces or brackets.

Thanks for your time anyways. You guys are fast and helpfull for newbies like me.

---

### Post by btindie on 2010-10-13
In the console type
```
cd /media
ls
```
Is the directory listed? If so, type
```
cd <insert_directory_name>
```
Repeat the above to get to the directory you require.
 
What do you mean by
> i am trying to use...
What are you typing into the console??

---

### Post by nearlymagicman on 2010-10-13
I guess i fixed it, sadly the console cannot work with spaces or brackets.

Thanks for your time anyways. You guys are fast and helpfull for newbies like me.


> What do you mean by
Quote:i am trying to use... 

What are you typing into the console??

Just wanted to express that i am trying to excess this folder but not beeing very successfull :)

---

### Post by Vaphell on 2010-10-13
console works with spaces but you need to escape those spaces that are parts of a path or any other parameter in general
you need to put \ before the space (\ = 'next sign is not to be treated as anything of logical meaning when parsing the command')
altenatively you can use "" on the whole path - spaces inside "" won't be treated as a separators.

and the best thing about console is that it autocompletes names/hints valid possibilities for you when you press tab once/twice. With that extremely useful feature you can write your long path with maybe 10 keypresses max and all the spaces will be escaped automatically, no risk of single typo ruining your 60-char long path typed in manually.

---

