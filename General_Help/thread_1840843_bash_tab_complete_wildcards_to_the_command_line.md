---
title: "bash: tab complete wildcards to the command line"
date: 2011-09-08
forum: General Help
---

### Post by pzs on 2011-09-08
I used to be a zsh user, but I need to use bash in my new job.

In zsh, if you use a wildcard in a file argument on the command line and hit tab, it completes the full list onto the command line for you. This is useful for, for example, deleting all but a small number of files. You do "rm *<tab>" and then edit the command to remove the files you want to keep.

Does anybody know how to set bash to do this?

---

### Post by Habitual on 2011-09-08
```
rm [tab tab]
```

There are several tricks for NOT deleting file(s) by extension in a wildcard delete  It is ```
rm !(*.txt)
```

google search for "delete all except" should list your options.

---

### Post by pzs on 2011-09-08
I know there are other ways to do "delete all except", but wildcard expansion on the command line is still something I find useful. Does anybody know how to do this in bash?

---

### Post by Bodsda on 2011-09-08
> **pzs said:**
> I know there are other ways to do "delete all except", but wildcard expansion on the command line is still something I find useful. Does anybody know how to do this in bash?
 
I don't really understand what you mean. I can do this
 
```

rm tem<tab><tab>

```
This would then list (for example)
```

temp
temp1
temporary
temporary1
template
temple

```
 
I could then type
```

rm templ<tab><tab>

```
to list
```

template
temple

```
 
Is that what you mean?
 
Bodsda

---

### Post by pzs on 2011-09-08
If I type "ls *<tab>", rather than listing the files, the files are added directly to my current command line so I can edit that command line before I execute it. In bash, it just lists the files below the command line, without putting them on it.

So if I had a directory that contained P01, P02... all the way up to P10 and I wanted to remove them all except P02 and P07 I could do:

```
ls P*<tab>
```

and it would make my command line look like this:

```
ls P01 P02 P03 P04 P05 P06 P07 P08 P09 P10
```

Then I could edit it to say

```
ls P01 P03 P04 P05 P06 P08 P09 P10
```

before hitting return. It's the completion followed by the ability to edit that I'm after.

---

### Post by carolinason on 2011-09-08
> You do "rm *<tab>" and then edit the command to remove the files you want to keep.

weird way to say that 'remove files.. you want to keep.'

use your arrows keys to position the cursor and then use the backspace and delete key to delete the characters in the file names you want to keep. as far as negating the names i don't know. perhaps using ```
rm -i
``` to confirm the deletion maybe.

---

### Post by pzs on 2011-09-08
> **carolinason said:**
> weird way to say that 'remove files.. you want to keep.'


You understood me, so it can't have been that strange. Hopefully my example made it clearer. Does that mean that somebody will be able to answer my question?

---

### Post by sisco311 on 2011-09-08
Alt+Shift+8

See:
```
man bash | less +/"^ +Completing"
```

---

### Post by pzs on 2011-09-09
That was the answer I was looking for. Thank you very much, sisco311.

---

### Post by sisco311 on 2011-09-09
> **pzs said:**
> That was the answer I was looking for. Thank you very much, sisco311.

You're welcome!

If you use it a lot, you probably want to create a more convenient shortcut for it. You can do it by editing the ~/.inputrc.file to something like:
```

#Ctrl+a:
Control-a: insert-completions
#Alt+s:
"\es": insert-completions

```

Oh, and don't forget to mark this thread as [SOLVED].

---

