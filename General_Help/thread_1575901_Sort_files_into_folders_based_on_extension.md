---
title: "Sort files into folders based on extension"
date: 2010-09-16
forum: General Help
---

### Post by DragonDon on 2010-09-16
Greetings all,

I recovered some 60,000 files with PhotoRec and need a script to sort them into individual folders based on extension.  I was able to do this once before but cannot find the script again (sad thing is that I probably saved it on another HD that I'm having partition issues with, but that's another story....).

I found this script:

```
#!/bin/dash

mkdir "$1"

for file in *.$1; do
  mv "$file" "$1"
done
```

While it does work, I am not looking forward to going through all 132 folders and typing in each extension.  The last time I did it, the folder was automatically created based on the extension(s) found.

Any help would be greatly appreciated.

---

### Post by gmargo on 2010-09-16
Here's a simple command to get a list of all file extensions in use in the current directory.
```

find . -mindepth 1 -maxdepth 1 -type f -print | grep '^\./.*\.' | sed 's/^.*\.\([^.][^.]*\)$/\1/' | sort -u

```Integrating this into your script:

```

#/bin/sh

exts=$(find . -mindepth 1 -maxdepth 1 -type f -print | grep '^\./.*\.' | sed 's/^.*\.\([^.][^.]*\)$/\1/' | sort -u)

for e in $exts; do
    mkdir "$e" 
    for file in *.$e; do   
        mv "$file" "$e"
    done
done

```And a last find command to run the script in each directory:
```

find . -depth -type d -print -exec /path/to/ext/script \;

```

---

### Post by DragonDon on 2010-09-16
While I am far from truly understanding shell scripts, I honestly do appreciate the efforts.

I ran the script and got:

"find: `/home/dragondon/sort2.sh': Permission denied"

Then I realized that I hadn't marked it as executable, did so and it worked beautifully!

Now, is there some way I can simply make that command into some sort of simply script or batch file?

---

### Post by DragonDon on 2010-09-20
Does anyone know how to alter the script a little to let this work on a complete range of sub-directories?

i.e.  Right now I have to be in each directory to run the script.

Steps:

1/ cd recup_dir.##
2/ find . -depth -type d -print -exec /path/to/ext/script \;
3/ cd ..
4/ repeat

For 132 directories, this is tedious.

Is it as simple as changing the ' -mindepth 1 -maxdepth 1' to 2 so that I can run the script once on each recup sub directory?

---

### Post by gmargo on 2010-09-21
Alter script to take directory as argument.
Also alter script to short circuit if the current directory is already named by the extension, so you should be able to run this script more than once without the music files getting deeper and deeper each cycle.
```

#/bin/sh

# Give directory as argument
dir=$1
if [ "x$dir" != "x" -a -d "$dir" ] ; then
    cd "$dir"
fi

dir=$(pwd)
basedir=$(basename "$dir")

exts=$(find . -mindepth 1 -maxdepth 1 -type f -print | grep '^\./.*\.' | sed 's/^.*\.\([^.][^.]*\)$/\1/' | sort -u)

for e in $exts; do

    # Skip extension if this directory is already named by extension.
    if [ "$basedir" = "$e" ] ; then
        continue
    fi

    mkdir "$e"
    for file in *.$e; do
        mv "$file" "$e"
    done
done


```Alter find command to provide directory to script: 
```

find . -depth -type d -print -exec /path/to/ext/script {} \;

```Now you can run the find command once at the top level.

EDIT: modified script to remove multi-run effects.

---

### Post by COKEDUDE on 2010-09-21
Very nice :). I gotta try this out :).

---

### Post by DragonDon on 2010-09-22
Thanks for update, worked great!!!

Shell Scripts on on my list to understand and use :)

---

