---
title: "What is the real name of my files for the terminal?"
date: 2010-01-29
forum: General Help
---

### Post by abelito8 on 2010-01-29
I messed up with Ubuntu and now I have so little space that I cannot start GUI
I am trying to delete some files through the terminal 
the easiest thing is to delete video files so I went into the Videos directory but I am unable to delete anything for it says "no such file or directory" rm

now I have files like "Tropa de Elite" or "Easy Virtue (2008)" and I understand that blank spaces or brackets are not liked by the terminal...what should I type instead?

thank you

---

### Post by coral66 on 2010-01-29
I assume that the command ls returns the files you want to delete. If the file name contains spaces use rm "file name to delete" (the file name enclosed in quotes.

If ls does not return the name of the files, try this ...
# cd to the top directory
cd /
# use the find command to locate your file
find -iname "*crud*"

where crud is part of the file name, this should return all occurrences. 

Also check your /tmp directory, that could have files you don't need.

---

### Post by llawwehttam on 2010-01-29
To delete folders you need the rf args so to delete all my videos it would be:
```
rm -rf ~/Videos
```
 
**NAME**

rm - remove files or directories 
**SYNOPSIS**

**rm** [*OPTION*]... *FILE*... 
**DESCRIPTION**

This manual page documents the GNU version of **rm**. **rm** removes each specified file. By default, it does not remove directories. If a file is unwritable, the standard input is a tty, and the *-f* or *--force* option is not given, **rm** prompts the user for whether to remove the file. If the response does not begin with `y' or `Y', the file is skipped. 

**OPTIONS**


Remove (unlink) the FILE(s). **-d**, **--directory** unlink FILE, even if it is a non-empty directory (super-user only) **-f**, **--force** ignore nonexistent files, never prompt **-i**, **--interactive** prompt before any removal **-r**, **-R**, **--recursive** remove the contents of directories recursively **-v**, **--verbose** explain what is being done **--help** display this help and exit **--version** output version information and exit 
To remove a file whose name starts with a `-', for example `-foo', use one of these commands: **rm** **--** -foo **rm** ./-foo Note that if you use rm to remove a file, it is usually possible to recover the contents of that file. If you want more assurance that the contents are truly unrecoverable, consider using shred.

---

### Post by 3rdalbum on 2010-01-29
> **abelito8 said:**
> now I have files like "Tropa de Elite" or "Easy Virtue (2008)" and I understand that blank spaces or brackets are not liked by the terminal...what should I type instead?

Three suggestions:

1. Put a backslash before any character that the terminal won't like:

```
rm Easy\ Virtue\ \(2008\).avi
```

2. Enclose the filename in brackets:

```
rm "Easy Virtue (2008).avi"
```

3. Type 'rm' and then drag the file to the terminal to fill in the file name automatically.

---

### Post by llawwehttam on 2010-01-29
> **3rdalbum said:**
> Three suggestions:
 
1. Put a backslash before any character that the terminal won't like:
 
```
rm Easy\ Virtue\ \(2008\).avi
```
 
2. Enclose the filename in brackets:
 
```
rm "Easy Virtue (2008).avi"
```
 
3. Type 'rm' and then drag the file to the terminal to fill in the file name automatically.
 
you can also use tab to auto complete.
 
Type ```
rm -rf  Easy
```the hit tab and it should auto complete tha name.

---

### Post by abelito8 on 2010-01-29
it worked thank you! Now I freed enough space to start the GUI again...
run to buy an external HDD now, to avoid this happening again...

---

