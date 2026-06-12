---
title: "cat * when theres sub directories"
date: 2012-09-11
forum: General Help
---

### Post by andthewicked on 2012-09-11
I use cat * all the time but when theres subdirectories it goes all jfqoifjeoafjeaop on me and this seems so dumb that I dont know the answer but I know you can use a global operator with subdirectories when you know the file extention like cat *.txt or whatever but what if you want to cat all the files and not the directories why cat trys to cat a directory is beyond my level of understanding but I tryed searching for an answer couldn't find one but I'm sure somebody knows and its probably pretty simple just never gets talked about thanks

my mistake cat doesn't try to cat directories but it does try to cat compile programs and the such witch gives me all the ajdsklfa;slfjsdlk weird text on the screen 

so the real question is how do you cat * when theres unreadable to human files in the same directory

---

### Post by dodo3773 on 2012-09-11
cat really was not designed to work that way. You could write a script to do this but it would be pointless because of the time it would take to execute probably. You're best bet is to find another way of accomplishing what you want. Not very helpful I know. If you want to see text inside of binaries you can always use "strings" instead of cat though. That should get rid of the gibberish. Why do you want to cat out directories full of binaries?

---

### Post by andthewicked on 2012-09-11
I didn't know you could do that with binaries. That is interesting I'll def check that out

I don't want to cat a diretory full of binaries tho I just want cat to exclude them when I use cat * 

I just want to cat all the text files reguardless of type and excluding any binaries, is that possible?

---

### Post by spjackson on 2012-09-11
Something like this will do it.
```

cat $(file * | egrep ' .*text' | cut -d: -f1)

```
This isn't a perfect solution, but it's probably a good enough starting point.

---

### Post by andthewicked on 2012-09-11
> **spjackson said:**
> Something like this will do it.
```

cat $(file * | egrep ' .*text' | cut -d: -f1)

```This isn't a perfect solution, but it's probably a good enough starting point.

that works great thanks for the info was wondering if you could break down whats going on here I'm just confused with the file * , '.*text' , and the  -d: -f1 part. any info would be apreciated thanks for the help bro

---

### Post by spjackson on 2012-09-11
file is a command that has rules that help it determine what sort of files its arguments are. For text files, it outputs a string containing 'text'.

The egrep expression filters the results of file so that we are only left with ones containing the string 'text'. This is a bit of a weakness because if we have 'text' as part of the filename, then it will pick those up even if they are not text. The ' .*text' expression requires there to be at least one space somewhere before the string 'text'. Now we won't pick up 'text' as part of the filename, unless there also happens to be a space in the filename.

Finally, 'file' outputs the filename followed by a colon then the description so, we use cut to trim this down to just the filename. The -d: tells cut to treat a colon as the field separator and -f1 tells it to just output the first field.

---

### Post by andthewicked on 2012-09-11
> **spjackson said:**
> file is a command that has rules that help it determine what sort of files its arguments are. For text files, it outputs a string containing 'text'.

The egrep expression filters the results of file so that we are only left with ones containing the string 'text'. This is a bit of a weakness because if we have 'text' as part of the filename, then it will pick those up even if they are not text. The ' .*text' expression requires there to be at least one space somewhere before the string 'text'. Now we won't pick up 'text' as part of the filename, unless there also happens to be a space in the filename.

Finally, 'file' outputs the filename followed by a colon then the description so, we use cut to trim this down to just the filename. The -d: tells cut to treat a colon as the field separator and -f1 tells it to just output the first field.


amazing the power of linux is that makes sence I didn't even know the file command existed learn something new everyday, thanks for the explanation that really helps. 

hate to pester but you woldn't happen to know if I could pipe in a ls -R in there somehwere so I could view all my text files at once would ya I tried just adding it the the start to no avail. last question I promise. thanks again for the help

---

### Post by spjackson on 2012-09-12
> **andthewicked said:**
> 
hate to pester but you woldn't happen to know if I could pipe in a ls -R in there somehwere so I could view all my text files at once would ya I tried just adding it the the start to no avail. last question I promise. thanks again for the help

You can't use ls -R directly because the directory name and the file name are output on separate lines. The "find" command does a similar job, but then the files are not necessarily in the same order.
```

cat $(find . -print0 | xargs -0 file  | egrep ' .*text' | sort | cut -d: -f1)

```As is usually the case with shell one-liners, they become much more unwieldy as extra requirements appear.

Note that the above "find" command will include files whose names begin with a dot, whereas *, ls, ls -R exclude these. You can get "find" to exclude these but that's even more complexity.

---

