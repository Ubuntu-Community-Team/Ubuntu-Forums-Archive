---
title: "Bash script to delete files"
date: 2012-08-26
forum: General Help
---

### Post by DeMus on 2012-08-26
Hi, I have 1 folder, with 4 sub-folders, with each a whole lot of sub and sub-sub folders. In these folders I have files I want to keep and I have files I want to throw away. Which ones stay and which ones go, depends on the file extension. Just by looking at the amount of folders I get sick thinking I have to do all this manually.
Now I know a bash script could do this, only I know absolutely nothing about bash scripts. Who likes to help me with this?
The files I want to keep are .mp3, .flac, .wav, .wma all others can go away.
What would the script look like? Who can help me with this?

Thanks

---

### Post by SeijiSensei on 2012-08-26
This is just a simple starting point that looks at all files in a single directory and deletes the ones that don't match your list of extensions.  You'd need to run it repeatedly in each directory you wish to clean, or you can try to teach yourself a bit of bash scripting and figure out a way to make it recurse down the directory tree. (Hint: to get a list of directories below the current directory use "ls -d */".)

```

#!/bin/bash

for f in *
do

    EXT=$(echo "$f" | awk -F. '{print $2}')
   
    case "$EXT" in 

       mp3|flac|wav|wma)
       ;;

       *)
       rm -f "$f"

    esac

done

exit 0

```

This also assumes all the filenames are of the form "something.ext" and not "something.something.ext".  If you have files with multiple dots in their names, you'd need to futz with the awk command.

Put the script in a file and make it executable with "chmod a+x /path/to/the/script".  Test it out by copying one of your directories to another location like /tmp, then try 

```

cd /tmp/testdirectory
/path/to/the/script

```

Wow, post #5,000 for me.  Who knew I could be so loquacious?

---

### Post by steeldriver on 2012-08-26
... or you could leave bash out of things completely and just do something like

```
find /path/to/dir -type f ! \( -iname '*.mp3' -o -iname '*.flac' -o -iname '*.wav' -o -iname '*.wma' \) -delete
```or

```
find /path/to/dir -type f ! \( -iname '*.mp3' -o -iname '*.flac' -o -iname '*.wav' -o -iname '*.wma' \) -print0 | xargs -0 rm
```[B]I'd recommend you start by doing

```
find /path/to/dir -type f ! \( -iname '*.mp3' -o -iname '*.flac' -o -iname '*.wav' -o -iname '*.wma' \) -print
```first to make absolutely sure it's not going to delete anything you don't want it to[/B]

---

### Post by papibe on 2012-08-26
Hi DeMus.

+1 to steeldriver's suggestion of using both 'find', and first '-print' before '-delete'.

You can also use regular expressions to make the statement a little shorter:
```
find /path/to/dir -type f -not -iregex '.*\.\(mp3\|flac\|wav\|wma\)$' -print
```
Regards.

---

### Post by DeMus on 2012-08-26
> **steeldriver said:**
> ... or you could leave bash out of things completely and just do something like

```
find /path/to/dir -type f ! \( -iname '*.mp3' -o -iname '*.flac' -o -iname '*.wav' -o -iname '*.wma' \) -delete
```or

```
find /path/to/dir -type f ! \( -iname '*.mp3' -o -iname '*.flac' -o -iname '*.wav' -o -iname '*.wma' \) -print0 | xargs -0 rm
```[B]I'd recommend you start by doing

```
find /path/to/dir -type f ! \( -iname '*.mp3' -o -iname '*.flac' -o -iname '*.wav' -o -iname '*.wma' \) -print
```first to make absolutely sure it's not going to delete anything you don't want it to[/B]

Thank you very much for this help. I tried the last one first and got a long list of files I want to delete. Looking through the list I found no file I don't want to delete, so it was safe to replace print with delete at the end of the line. Now all the mess is gone.
Thanks again.

---

