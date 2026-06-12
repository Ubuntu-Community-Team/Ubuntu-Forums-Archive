---
title: "rm directories only, not files, when doing rm -r foo*"
date: 2011-02-28
forum: General Help
---

### Post by InkyDinky on 2011-02-28
How do I delete just directories and not files when performing a "rm -r foo*" command? 
E.G. I have  foobar.txt foofoo.o foorebar.jpg and foo/ foonuggets/ and footemp/ in a directory.  
In one fell swoop how do I delete just the directories and preserve the files?
Is this possible?

Seeing as how I only use the -r switch when removing directories I accidentally ran this command and removed files that I wanted (luckily nothing vital).  Lesson learned now I want to prevent ever doing that on files that *are* vital.

Thanks.

---

### Post by vanadium on 2011-02-28
With "rmdir", provided the directories foo* are empty. You may probably empty these directories first with a command like

rm -rf foo*/*

BE CAREFUL WITH THAT COMMAND

---

### Post by InkyDinky on 2011-02-28
Thanks for the reply but I'm looking for more of a one-stop command.
Any other suggestions out there?

---

### Post by TeoBigusGeekus on 2011-02-28
```
find . -type d -name "foo*" -exec rm -r {} \;
```
Replace . with the path of your choice.

---

### Post by sisco311 on 2011-02-28
I would write a function:
```
rmdirs ()
{
  for file in "$@"; do
    if [ -d "$file" ]; then
      **echo** rm -rf -- "$file"
    fi
  done
}

```

But, if you whish,  you can use find:
```
find ./ -maxdepth 1 -name 'foo*' -type d -exec **echo** rm -rf -- '{}' +
```

---

### Post by smurphy_it on 2011-02-28
I would use the find command like TeoBigusGeekus stated, however, it may go a few levels down and remove some directories you don't want.  You can help mitigate that by using the -maxdepth flag.

find -maxdepth 2 -type d -name "foo*" -exec rm -r {} \;

---

### Post by TeoBigusGeekus on 2011-02-28
> **smurphy_it said:**
> I would use the find command like TeoBigusGeekus stated, however, it may go a few levels down and remove some directories you don't want.  You can help mitigate that by using the -maxdepth flag.

find -maxdepth 2 -type d -name "foo*" -exec rm -r {} \;

Yes, of course, sorry about that. My code could go to an irrelevant folder, find a foo* folder in it and erase it.
Use smurphy's variation (or sisco's).

---

### Post by vanadium on 2011-03-01
> **InkyDinky said:**
> Thanks for the reply but I'm looking for more of a one-stop command.

What is a one-stop command?

rm -rf foo*/* && rmdir foo*

could also be a one stop command. Any sequence of commands can be combined in a script. The power of linux lies in combining utilities that each do a single task. So what do you mean with a "one-stop" command? Anyway, there are several ways to achieve your goal and I think that by now you have some inspiration.

---

### Post by InkyDinky on 2011-03-01
@vanadium
I guess my lazy self was hoping for a single command to perform what I desired.  It didn't want two steps to get me where I wanted to go. I didn't mean to poo-poo your help.  I was just being the bratty kid trying to kick and scream till he got what he wanted.

So I'll just have to write up a bash script & alias with all these awesome suggestions to give that bratty kid just what he wants.

Thanks Ubuntuers!

---

