---
title: "Bash commands to rename files and contents"
date: 2011-05-18
forum: General Help
---

### Post by joshuachoo on 2011-05-18
What bash command can I use to rename or change the extension or name
of a batch of files (for example, from .php to .html)?

Furthermore, is there a simple bash or python script/command that can
be used to open a batch of plain text files one-by-one, search for all
instances of a specific word, and replace all of those instances with
another word?

---

### Post by Telengard C64 on 2011-05-18
I think this does what you want.

```
foo$ ls
1.php  2.php  3.php  4.php  5.php  6.php  7.php  8.php  9.php
foo$ for i in *php ; do mv -iv "$i" "${i%php}"html ; done
`1.php' -> `1.html'
`2.php' -> `2.html'
`3.php' -> `3.html'
`4.php' -> `4.html'
`5.php' -> `5.html'
`6.php' -> `6.html'
`7.php' -> `7.html'
`8.php' -> `8.html'
`9.php' -> `9.html'
foo$ ls
1.html  2.html  3.html  4.html  5.html  6.html  7.html  8.html  9.html
```

Also see [man 1 rename](http://manpages.ubuntu.com/manpages/natty/en/man1/prename.1.html) for another possible solution.

HTH

---

### Post by Telengard C64 on 2011-05-18
> **joshuachoo said:**
> Furthermore, is there a simple bash or python script/command that can
be used to open a batch of plain text files one-by-one, search for all
instances of a specific word, and replace all of those instances with
another word?

Suppose you want to replace all instances of "chuck" with "duck".

```
foo$ cat tongue-twister.txt
How much wood could a woodchuck chuck if a woodchuck could chuck wood?
foo$ while read -r ; do echo -E "${REPLY//chuck/duck}" ; done < tongue-twister.txt
How much wood could a woodduck duck if a woodduck could duck wood?
foo$
```

Also see [man 1 sed](http://manpages.ubuntu.com/manpages/natty/en/man1/sed.1posix.html) and [man 1 awk](http://manpages.ubuntu.com/manpages/natty/en/man1/awk.1posix.html) for other possible solutions.

---

### Post by jamesjenner on 2011-05-18
to rename a group of files in bash you type in:
> mv *.<extension> *.<new extension>

Test it though with some test files to be safe if it's a lot of files, or copy them into another folder as a backup first.

Note that you cannot just use * as it will get all files including files that are being renamed on the fly (or used to in versions of unix I have used in the past).

As for changing stuff, look up sed, you can process your file or group of files via sed and use the command "0,Gs/<text to replace/<new text>/g". Pretty sure that's close. Havn't got a box in front of me to test it sorry.

:edit:

Note, the above is incorrect, do not use. Working examples are below.

---

### Post by DaithiF on 2011-05-18
> **jamesjenner said:**
> to rename a group of files in bash you type in:
```

mv *.<extension> *.<new extension> 			 		

```

No, thats wrong.  you can't use mv in this way.

I would use rename, as suggested by Telengard C64.

```
rename -n 's/\.php$/.html/' *.php
```
to preview what will be renamed, and then drop the -n to run it for real.

---

### Post by jamesjenner on 2011-05-18
> **DaithiF said:**
> No, thats wrong.  you can't use mv in this way.

Hmm your right. Getting confused with DOS. I should have said something along the lines of:

```
for i in `ls *.avi`; do echo `basename $i .avi`.mpg; done
```

The above will rename every file with an extension of avi to have an extension of mpg in the current directory. beware that if your doing recursion that basename trims off paths from memory.

I've tested the replace option now i'm home and what you want to do is:

```
find . -name "*.txt" -exec sed -i 's/white/blanc/g' {} \;
```

That will do the trick. The text to search for in the above example is 'white' and the replacement is 'blanc'.

Sorry for any confusion above, been a while since I did shell scripting so i'm a tad rusty.

Cheers, 

James.

:edit:

I like DaithiF's example for the rename, easier to test, though both his and mine are correct. His is simpler.

---

### Post by nothingspecial on 2011-05-18
> **jamesjenner said:**
> 

```
find . -name "*.txt" -exec sed -i 's/white/blanc/g' {} \;
```



Bear in mind that will do every .txt file in every directoty in the current directory and all the directories in those directories, and so on ................

If that is what you want then fine, but if you only want to change the ones in the directory you are in then use the *.txt method.

I just wouldn't want you to do something catastrophic by mistake.

---

### Post by nothingspecial on 2011-05-18
> **nothingspecial said:**
>  use the *.txt method.




As in ```
sed -i 's/white/blanc/g' *.txt
```

without the 'find' bit

---

### Post by jamesjenner on 2011-05-18
> **nothingspecial said:**
> Bear in mind that will do every .txt file in every directoty in the current directory and all the directories in those directories, and so on ................

If that is what you want then fine, but if you only want to change the ones in the directory you are in then use the *.txt method.

I just wouldn't want you to do something catastrophic by mistake.

That's a very good point, presumed knowledge is always a problem :)

you can try the -maxdepth 1 to get around this problem if you just wish to apply it to the current directory. That would change it to:
```
find . -name "*.txt" -maxdepth 1 -exec sed -i 's/white/blanc/g' {} \;
```
Note I haven't tested it, but it should work. You can always do it via:
```
find . -name "*.txt" -maxdepth 1 -print
```
the above will print out the file names instead of executing the sed command in the prior one.

Man this is fun, brings back old memories :)

:edit:

ahh yes, good point, removing the find will do the trick of course. I'm so used to using find cause many years ago I had to merge what was effectively three different forked projects, so find became second nature to handle the directory structure ;)

---

### Post by Telengard C64 on 2011-05-18
> **nothingspecial said:**
> I just wouldn't want you to do something catastrophic by mistake.

The **find** command is one of the best examples I've ever seen of the addage, "With great power comes great responsibility." Many people seem to forget that **find** is *recursive by default*. Few people seem to fully comprehend the implications of using **-exec** and **-execdir**.

TLDR version: **find** is one of the easiest ways to lose all your data.

:P

---

### Post by jamesjenner on 2011-05-18
> **Telengard C64 said:**
> The **find** command is one of the best examples I've ever seen of the addage, "With great power comes great responsibility." Many people seem to forget that **find** is *recursive by default*. Few people seem to fully comprehend the implications of using **-exec** and **-execdir**.

TLDR version: **find** is one of the easiest ways to lose all your data.

:P

Oh yes, or damage it to make it extremely difficult to recover to the point it was before hand. Hence why I generally use -print before using -exec to find out what files will be acted upon. Normally I will make a temporary backup of the data just to be safe (if practical).

:)

---

### Post by nothingspecial on 2011-05-19
> **Telengard C64 said:**
> The **find** command is one of the best examples I've ever seen of the addage, "With great power comes great responsibility." Many people seem to forget that **find** is *recursive by default*. Few people seem to fully comprehend the implications of using **-exec** and **-execdir**.

TLDR version: **find** is one of the easiest ways to lose all your data.

:P

Well said.

I once attempted to to move all the my photos out of all the subdirectories of my Pictures directory into the Pictures directory. A / instead of a . caused me to move every single file in the whole system into /  ](*,)

This is also a good example of why you shouldn't do non root tasks as root.

Another potential disasterous aspect of **find** is that it completes the actions on each file/directory it finds before moving on to the next one. 

So, for example,  never use find to create subdirectories recursively, unless you know exactly what you are doing, because after it has created a subdirectory in a directory it finds, it will find that subdirectory and create a subdirectory in that........... and then create one in that..........


.........and so on and so on until your computer blows up.

#-o

---

### Post by joshuachoo on 2011-05-20
Thanks all for the help! It works wonderfully :D

---

