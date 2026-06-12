---
title: "How to rename Folder [space]"
date: 2010-02-28
forum: General Help
---

### Post by CatchItBaby on 2010-02-28
How to rename folder which contain space in foldername

Path : /root/Documents/untitled folder

I want to replace space with undersope how to do that

Output : /root/Documents/untitled_folder

through terminal any idea ?

---

### Post by Miyavix3 on 2010-02-28
There is no rename function, but you can use the 'mv' command.

mv is move, but if you just move one file name to a different one, it works.

$: mv /root/Documents/untitled\ folder /root/Documents/untitled_folder

"\ " is used to write a space for file names, in the terminal.

---

### Post by CatchItBaby on 2010-02-28
Is there any way we can replace space character with underscop from folder / subfolders / files recursively

---

### Post by asmoore82 on 2010-02-28
You can also just use quotation marks...

```
ls "Documents and Settings"
```
...

There is a "rename" utility but its behavior is probably not what you'd expect.
It is sort of a mass or batch renamer by design but it requires a Perl expression to tell it what to do.

This should do a dry run of what you want:
```
find . -iname "* *" -print0 | xargs -0 rename -n 's/ /_/g'
```

if that looks like it will do the trick without mangling anything,
take out the ``-n'' near the end to make it go for it.

**P.S.** forgot to mention that this command needs to be run from inside the directory
that you want to recurse. If you would like to point it at a directory instead,
replace that first ``.'' with the location, for example ...
```
find "/home/asmoore82/Documents" -iname "* *" -print0 | xargs -0 rename -n 's/ /_/g'
```

**P.P.S.** Just thought of another hiccup, if you want to run this on files in a restricted area,
you'll have to be sure to use `sudo` on both sides of the pipeline ``|'' ...
```
**sudo** find "/root" -iname "* *" -print0 | **sudo** xargs -0 rename -n 's/ /_/g'
```

---

### Post by CatchItBaby on 2010-02-28
Thanks ... :)

---

### Post by asmoore82 on 2010-02-28
Another hiccup ...

```
find . -iname "* *" -print0 | xargs -0 rename 's/ /_/g'
```

The left side of the pipeline is searching through files and folders and
the right side is renaming them concurrently.

This may cause renaming of files to fail if they are in a folder that was
just renamed because the right side is still processing the results
of the original search.
The problem is illustrated below:
```
**user@hostname$** mkdir test
**user@hostname$** mkdir "test/new folder"
**user@hostname$** touch "test/new folder/new file"
**user@hostname$** find test -iname "* *"
test/new folder
test/new folder/new file
**user@hostname$** mv "test/new folder" "test/new_folder"
`test/new folder' -> `test/new_folder'
**user@hostname$** mv "test/new folder/new file" "test/new_folder/new_file"
[COLOR="Red"]**mv: cannot stat `test/new folder/new file': No such file or directory**[/COLOR]
**user@hostname$**
```

[B][COLOR="Blue"]The Quick and Dirty solution to this problem is to run the
command multiple times until it produces no errors.[/COLOR][/B]

A true solution is much trickier than what meets the eye.
using the ``-depth'' option for find only reverses the same problem:
```
**user@hostname$** find test -depth -iname "* *"
test/new folder/new file
test/new folder
**user@hostname$** mv "test/new folder/new file" "test/new_folder/new_file"
`test/new folder/new file' -> `test/new_folder/new_file'
**[COLOR="Red"]mv: cannot move `test/new folder/new file' to `test/new_folder/new_file': No such file or directory[/COLOR]**
**user@hostname$** mv "test/new folder" "test/new_folder"
`test/new folder' -> `test/new_folder'
**user@hostname$**
```

---

### Post by geirha on 2010-02-28
This should handle it safely.
```
find . -depth -name "* *" -execdir bash -c 'for f; do mv -v "$f" "${f// /_}"; done' _ {} +
```

EDIT: Well not 100% safe. If the destination file already exists, it will overwrite it without asking. Add the -i option to mv if that is an issue.

---

### Post by CatchItBaby on 2010-02-28
Awsume! Works

Thanks :)

---

### Post by CatchItBaby on 2010-03-01
How i can use this command for adding suffix and preffix

[http://ubuntuforums.org/showpost.php?p=8896732&postcount=7](http://ubuntuforums.org/showpost.php?p=8896732&postcount=7)

---

### Post by geirha on 2010-03-01
> **CatchItBaby said:**
> How i can use this command for adding suffix and preffix

[http://ubuntuforums.org/showpost.php?p=8896732&postcount=7](http://ubuntuforums.org/showpost.php?p=8896732&postcount=7)

It only requires a few minor changes.
```

searchterm="*bla*"
suffix=".txt"

find . -depth -name "$searchterm" -execdir bash -c 'for f; do mv -v "$f" "$f$suffix"; done' _ {} +

```
For prefix, just change $f$suffix to $prefix$f.

EDIT: Apologies, I messed up this one. The suffix variable isn't passed to the mini-script properly. This should do it properly:

```
find . -depth -name "$searchterm" -execdir bash -c 'suffix=$1; shift; for f; do mv -v "$f" "$f$suffix"; done' _ "$suffix" {} +
```

---

### Post by Neezer on 2010-03-01
Is there a reason that nobody has suggested nautilus???? can't you just go to a folder, right click -> rename and presto...change the name?

---

### Post by derrick81787 on 2010-03-01
> **Neezer said:**
> Is there a reason that nobody has suggested nautilus???? can't you just go to a folder, right click -> rename and presto...change the name?

You can, but I think he asked how to do it through the command line.

---

### Post by luigi_mb on 2010-03-01
> **derrick81787 said:**
> You can, but I think he asked how to do it through the command line.

Install detox. It's in the repos.

"Detox is a utility designed to clean up filenames. It replaces difficult to work with characters, such as spaces, with standard equivalents. It will also clean up filenames with UTF-8 or Latin-1 (or CP-1252) characters in them.

Features:

 * Removal or replacement of upper ASCII Latin-1 (ISO 8859-1) characters
 * Removal or replacement of UTF-8 encoded Unicode characters.
 * Removal or replacement of spaces and other potentially tricky haracters
 * Trimming of excessive "_" and "-"s
 * Directory recursion, dry runs, verbose listings

It is designed with safety in mind. It won't overwrite a file that already
exists, and it doesn't touch special files if not requested."


/luigi

---

### Post by swapii on 2011-10-11
Can we rename a folder without any text i.e. unnamed folder like ' ' ????:?:

---

### Post by coffeecat on 2011-10-11
This is an old thread.

@swapii, you would be better off starting your own thread with an appropriate title.

Thread closed.

---

