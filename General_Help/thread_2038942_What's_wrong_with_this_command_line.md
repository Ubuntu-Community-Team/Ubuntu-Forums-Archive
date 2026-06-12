---
title: "What's wrong with this command line???"
date: 2012-08-07
forum: General Help
---

### Post by rhss6-2011 on 2012-08-07
Hello there everyone,
I'm trying to create a script that **makes an inventory** of certain files in a directory. The files have **multiple extensions** and I want to **list them** while f**ollowing the directory tree**, instead of file type. The **output** of said command is to go **into a** set **TXT file** **in my home directory.**
My issue is that I can do what I want by searching for file type a, file type b, file type c etc.

**FOR EXAMPLE**:
What I have now
find /path/to/directory -iname "*.a" > $HOME/01_INVENTORY.txt
find /path/to/directory -iname "*.b" >> $HOME/01_INVENTORY.txt
find /path/to/directory -iname "*.c" >> $HOME/01_INVENTORY.txt

**The new code that doesn't work**:
find /path/to/directory "*.{a|b|c|d|f|g|h|i}" > $HOME/01_INVENTORY.txt

**I have also tried various kinds of brackets**:
{files}
(files)
[files]

**Can anyone give me a way to fix this?**

---

### Post by Toz on 2012-08-07
> The new code that doesn't work:
find /path/to/directory "*.{a|b|c|d|f|g|h|i}" > $HOME/01_INVENTORY.txt

You dropped -iname in this example. Typo?

This works for me:
```
find /path/to/directory -iname "*.[a|b|c]" > $HOME/01_INVENTORY.txt
```

---

### Post by steeldriver on 2012-08-07
short answer I think is that 'find -iname' doesn't really do regular expressions - you could *maybe* do something exotic like

```
find /path/to/directory -regex '.*\.\(a\|b\|c\|d\|e\)'
```(don't quote me!) or more pragmatically just 'or' them on the find command line directly

```
find /path/to/directory \( -iname '*.a' -o -iname '*.b' -o -iname '*.c' \) -print

```Also you should be wary of using double quotes in your find patterns - the shell is free to glob them, which can give unpredictable results. Single quotes are safer.

---

### Post by Vaphell on 2012-08-07
i think *-(i)name* is simply all about standard shell globs wrapped up in quotes to prevent immediate expansion
in this specific case *-name '*.[abcde]'* would work

no idea if extended globs would work though - EDIT: just tested, they don't work in find.
```
$ shopt -s extglob
$ echo @(*.sh|*.py)
<bunch of filenames>
$ find -iname '@(*.sh|*.py)'
$
```
so it's either *-regex ...* or *-name ... -o -name ... -o -name ...*


> This works for me:
Code:

```
find /path/to/directory -iname "*.**[a|b|c]**" > $HOME/01_INVENTORY.txt
```
[a|b|c] = a or | or b or | or c
in other words |'s are completely unnecessary

---

### Post by steeldriver on 2012-08-07
OK I (probably wrongly) assumed the OP wasn't talking about literal .a , .b , .c etc file extensions - the regex / iregex predicate seems to also handle things like this:

```
steeldriver@desk01-vm:~/Documents$ find whatever -iregex '.*\.\(txt\|csv\)'
whatever/file.TXT
whatever/file.csv
whatever/FILE.CSV
whatever/file.txt
```

---

### Post by Vaphell on 2012-08-07
i think that even if OP was talking about literal a, b, c, general solution should be found and [abc] doesn't offer that because it's too specific.
-regex looks like the best solution here.

---

### Post by rhss6-2011 on 2012-08-08
Well, I got that to work before with the " -o " and the issue I'm having is this:
**The folders** are not in alphanumerical order, **and the files are** also **not in alphanumerical order**.
The whole point of the script is for me to have a list of files in a folder, already sorted for me.

Any advice for the sorting - perhaps I can use grep or cat to do that after the file already has it's entries?

---

### Post by Vaphell on 2012-08-08
you can sort find output too
```
find ... | sort > out.txt
```

---

### Post by rhss6-2011 on 2012-08-09
Thank you, that did it ;)
I wasn't familiar with the "sort" command - thanks for reminding me.

---

