---
title: "Command Line"
date: 2010-10-20
forum: General Help
---

### Post by Pumma on 2010-10-20
Hi all,

First time poster and new to Ubuntu. A bit about me, I was a long time Windows user, recently I downloaded Ubuntu and I love it. First saw it in my Information Systems class. I am not a computer whiz, but I am learning. As in the process of learning questions do come up and I hope this community of users can help me along the process. Anyways I have been using Ubuntu for about a month, and I just recently (last night) started using the command line and I absolutely love it! 

My question:

I have come across a problem, before Ubuntu I named a lot of me files in such a manner ex: My Homework

Now with using the command line i realize it does not pick up "spaces" so my question is how can I get rid of the space in all my files in a specific folder? Without having to go to each file (like i would on windows) or is there anyway to get passed the space? by inserting any character?

Thanks guys, looking forward to answers!

---

### Post by sisco311 on 2010-10-20
Welcome to the forums and Ubuntu!

Spaces are field delimiters so you have to escape them with quotes. i.e.:
```
cd "foo bar"
```
or
```
cd foo\ bar
```

You can use tab completion:
```
cd foo<hit tab>
```

See:```
man bash | less +/^QUOTING
```

---

### Post by SuaSwe on 2010-10-20
Either put quotes around the folder name or escape the space with a \.

cd "My Homework"
cd My\ Homework

... should both work. :)

---

### Post by Pumma on 2010-10-20
Thanks a lot for the quick responses guys :)

One more question: Is there a command that will search through a folder and eliminate all spaces without me having to do each file separately? Or is there a way to replace a space for lets say a period?

---

### Post by sisco311 on 2010-10-20
> **Pumma said:**
> Thanks a lot for the quick responses guys :)

One more question: Is there a command that will search through a folder and eliminate all spaces without me having to do each file separately? Or is there a way to replace a space for lets say a period?

Well... yes but be careful and test it before you run it:
```
find **path/to/dir** -depth -name "* *" | while read file; do **echo** mv -i "${file}" "${file// /_}"; done
```

The above command just shows what files would have been renamed. To actually rename the files remove the **echo** command. 

IMHO there is no reason for removing the spaces from the file names. Well written scripts can handle them anyway. But I would remove the "My " prefixes from the directory names....

---

### Post by sisco311 on 2010-10-20
> **Pumma]Hi Sisco311,

Could you maybe help me understand that command that you sent me a little better?

find **path/to/dir** -depth -name "* *" | while read file said:**
> 

[QUOTE=Pumma]
Now what is -depth?

-depth means "process each directory's contents before the  directory  itself". Otherwise the command may rename a directory first then it will fail to rename the files in it because the path to the files no more exists. 
```
man find | less +2/-depth
```

[QUOTE=Pumma]
and i am assuming -name "* *" is look for the space (though why are we putting stars there?).[/quote]
"* *" is a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression"). it matches any file (directories are file too) with a space in their names.

[QUOTE=Pumma]
Now the next part I see is the connection of input and output. What does it mean?[/quote] 
| is a [pipe]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-4.html").

[QUOTE=Pumma]
While read file?
[/quote]
while read file = [while is a loop]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-4.html") and read assigns each file name, one by one to the *file* [variable]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html").

[quote=Pumma]
now what are all the brackets, dollar signs, slashes, all about?[/quote]

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html)

---

