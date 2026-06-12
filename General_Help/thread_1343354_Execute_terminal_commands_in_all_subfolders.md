---
title: "Execute terminal commands in all subfolders"
date: 2009-12-01
forum: General Help
---

### Post by chezzo on 2009-12-01
Basically, I've got a load of files here, all organised into a large number of folders, and all with underscores in their filenames instead of spaces. I want to replace all the underscores with spaces, just because I happen to like it better that way, and I've worked out how to do this using the command

> rename "s/_/ /g" *

However, I can't for the life of me work out if there's any way I can use the command once and have it execute in all subfolders of the folder I've navigated to.

I've tried various variants on the find command. The closest I've got is with

> find "[folder path]" -type f -name "*" | rename -v "s/_/ /g"

This gives me a (correct) list of filepaths of all the files in the folder and subfolders, with each one followed by an *incorrect* file path with underscores in and the phrase "No such file or directory". For example, say I enter the command, 

> find "/home/a folder/another folder/" -type f -name "*" | rename -v "s/_/ /g"

it returns a list of messages such as

> Can't rename /home/a folder/another folder/yet another folder/file_name.txt /home/a folder/another_folder/yet_another_folder/file_name.txt: No such file or directory

What am I doing wrong?!

---

### Post by audiomick on 2009-12-01
Hallo.
I am afraid I can't help, only ask a cautioning question: Are you sure you really want to do that?

As far as I know, if you are moving around your file system in the terminal, the underscores are a godsend, because the terminal file commands cant deal with spaces.
If your GUI craps out and you want to save stuff out using the terminal, I believe you can only get at files with no spaces in the names.

This may be outdated.

If it still true, however, and you have your files all nicely named without spaces, I would suggest leaving it like that.:D

Michael

---

### Post by chezzo on 2009-12-01
Thanks for the advice, but I don't really see any reason why I'd want to navigate round the files in a terminal rather than in Gnome... they're mostly music and video files. And they're all on an external hard disk too, so my GUI breaking isn't really an issue.

---

### Post by blur xc on 2009-12-01
> **audiomick said:**
> Hallo.
I am afraid I can't help, only ask a cautioning question: Are you sure you really want to do that?

As far as I know, if you are moving around your file system in the terminal, the underscores are a godsend, because the terminal file commands cant deal with spaces.
If your GUI craps out and you want to save stuff out using the terminal, I believe you can only get at files with no spaces in the names.

This may be outdated.

If it still true, however, and you have your files all nicely named without spaces, I would suggest leaving it like that.:D

Michael

I don't think that's true, but it's a pita to have spaces in file names.  Paths must be in quotation marks, and when using find commands there's a --print0 or some crap like that you ahve to do to make it ignore the spaces and separte paths with a null character or some junk...

Anyway, I'm no expert, and underscores make life easier, even if file names don't "look" as nice.

To the op- this might be help for you- [http://content.hccfl.edu/pollock/unix/findcmd.htm](http://content.hccfl.edu/pollock/unix/findcmd.htm)

Seems like the | might not be what you want, maybe the exec argument or the xargs...  Like I said, I'm no expert, but have dabble w/ the find command- and wiped out half my music directory in the process (and that was from doing a move command on recent files) :D...

BM

---

### Post by mo.reina on 2009-12-01
```
 find . -type f -name test_1_2 -exec rename -v "s/_/ /g" {} \;

```

you need to use **-exec **or **xargs** when using *find*

---

### Post by audiomick on 2009-12-01
> **blur xc said:**
> I don't think that's true, but it's a pita to have spaces in file names.  Paths must be in quotation marks, and when using find commands there's a --print0 or some crap like that you ahve to do to make it ignore the spaces and separte paths with a null character or some junk...

Anyway, I'm no expert, and underscores make life easier, even if file names don't "look" as nice.


Yes, I had another look in my reference book, and it is more like what you said than what I thought.:redface:

---

### Post by chezzo on 2009-12-01
> **mo.reina said:**
> ```
 find . -type f -name test_1_2 -exec rename -v "s/_/ /g" {} \;

```

you need to use **-exec **or **xargs** when using *find*

sorted! thank you so much!

---

### Post by mo.reina on 2009-12-01
no prob.  please set the thread as solved, makes it easier for those who are looking for solutions to similar problems

---

