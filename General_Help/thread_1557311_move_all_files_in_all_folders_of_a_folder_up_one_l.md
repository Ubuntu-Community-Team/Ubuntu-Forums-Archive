---
title: "move all files in all folders of a folder up one level"
date: 2010-08-20
forum: General Help
---

### Post by shortridge11 on 2010-08-20
I've got a folder called Foo.  In foo, there are 20 folders called bar1, bar2, bar3,...,bar20. In each of those barXX folders there are 2 files. How can i move those 2 files up one level into Foo with one command?

---

### Post by scorp123 on 2010-08-20
Hmmm ... maybe something like this?

```
cd /location/where/Foo/is
find ./bar* -type f -exec cp {} /path/to/new/location \;

```

What it does:

The first line is supposed to go into the ***"Foo"*** folder that you mentioned.

The second line then executes a ***"find"*** command: it searches all local ***"bar-something"*** (= *'./bar*'* in Unix lingo; *'./'* means *'here'*, and *'bar*'* means *'bar-something'*) for ***"type f"*** = regular normal files; if it finds anything those files are then forwarded to the ***"exec"*** parameter which basically says: *"Copy the results to the new location"* ... The curly brackets ***{}*** are a place holder for the results and the ***\;*** symbolises a keystroke with the 'Enter' key (so "find" knows that the command ends there).

I hope this helped ... ? :)

---

### Post by scorp123 on 2010-08-20
BTW, you could of course also use the GUI. If you know what the files are named like you can tell your file manager to search for them and then just drag & drop them to their new location ...

---

### Post by Rinzwind on 2010-08-20
edit: not what was asked :D sorry

---

### Post by shortridge11 on 2010-08-20
this machine is headless, no gui

---

### Post by guyshoxton on 2010-08-20
look at this image..

[IMG]http://ipic.tk/s/rur.png[/IMG]

---

### Post by shortridge11 on 2010-08-20
scorp123 that command worked perfectly, just changed cp to mv because these are large files.

---

### Post by ratcheer on 2010-08-20
I have always had success with the much simpler "mv bar* .."

Tim

---

### Post by scorp123 on 2010-08-22
> **ratcheer said:**
> I have always had success with the much simpler "mv bar* .." 

In this case this would only move those "bar-something" directories around, but not move the files underneath them to the new location. So if you really just want the contents underneath of each "bar-something" directory then there is no way around the "find" command.

:)

---

### Post by geirha on 2010-08-22
I'd go with:
```
mv bar*/* .
```

---

### Post by ratcheer on 2010-08-22
> **scorp123 said:**
> In this case this would only move those "bar-something" directories around, but not move the files underneath them to the new location. So if you really just want the contents underneath of each "bar-something" directory then there is no way around the "find" command.

:)

I am sorry, you are correct.  I thought we were talking about files in a directory, not subdirectories in a directory. I guess I need to read things more closely.

Tim

---

