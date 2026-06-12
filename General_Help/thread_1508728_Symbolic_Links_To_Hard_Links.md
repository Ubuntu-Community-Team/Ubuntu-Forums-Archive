---
title: "Symbolic Links To Hard Links"
date: 2010-06-13
forum: General Help
---

### Post by ks07 on 2010-06-13
Hey all,
I have a directory containing symbolic links to files on the same filesystem (specifically /dev/sda5, ext3), which I would like to change to hardlinks. I wanted to know if there is a quick way to convert symlinks to hardlinks, without manually recreating each using the command line. Does anybody know of a script that can do this?

Thanks in advance. :popcorn:

---

### Post by ks07 on 2010-06-13
**UPDATED:** This should now be usable, but feel free to improve upon what I've got so far. This bash script will convert all symlinks found in a given directory to hardlinks. Not heard of many people with this problem, but I needed it once, and it was a good learning experience. :popcorn:

```
#&#65279;!/bin/bash
#Converts all symbolic links in a directory to hard links. See http://ubuntuforums.org/showthread.php?t=1508728 for any updates/problems.
if [ -d $1 ] ; then
    echo "About to convert all symlinks in '$1' . Continue? [y/N]"
    read confirm
    if [ $confirm == y ]; then
        cd "$1" &&
        FOLDER="*"
        for file in $FOLDER
        do
            if [ -L "$file" ]; then
                target=$(readlink "$file")
                echo "Converting link to $file"
                mv "$file" "$file.old" &&
                ln "$target" "$file" &&
                rm "$file.old"
            else
                echo "$file not a symlink, skipping"
            fi
        done
    else
        echo "Exiting. No changes made."
    fi

else
    echo "$1 is not a directory, exiting."
fi
exit
```I've used this as an excuse to try out some slightly more complicated bash scripting. If you have a similar problem to me, copy and paste the following into a blank text file.
Save it as something sensible somewhere sensible, making it executable. Then run the script by changing directory to where you saved it, and run it with the directory of symbolic links you want to convert as an argument.

---

### Post by fattila2 on 2010-11-06
Great script, it helped me:). I needed it to make a directory containing links movable to another hard disk, because moving symlinks doesn't change the target files' location.
The only thing I miss from it is recursivity, because I have many subdirectories to convert symlinks to hardlinks in. Unfortunately, I can't add this feature to the script.
But you can find any symbolic link recursively in a directory if you type this command:
```
 find the_directory_to_search_in -type l
```
Note that hard links can't point to directories - you have to make individual hard links pointing to the contents of the directory.

---

### Post by esromneb on 2011-04-20
This program does not work if there is a space in the directory.

Here is the fix:

```

#!/bin/bash
#Converts all symbolic links in a directory to hard links. See http://ubuntuforums.org/showthread.php?t=1508728 for any updates/problems.
if [ -d "$1" ] ; then
    echo "About to convert all symlinks in '$1' . Continue? [y/N]"
    read confirm
    if [ "$confirm" == "y" ]; then
        cd "$1" &&
        FOLDER="*"
        for file in $FOLDER
        do
            if [ -L "$file" ]; then
                target=$(readlink "$file")
                echo "Converting link to $file"
                mv "$file" "$file.old" &&
                ln "$target" "$file" &&
                rm "$file.old"
            else
                echo "$file not a symlink, skipping"
            fi
        done
    else
        echo "Exiting. No changes made."
    fi

else
    echo "$1 is not a directory, exiting."
fi
exit
```

---

### Post by esromneb on 2011-04-20
For recursive operation, I saved the script below to this location: "/usr/local/bin/symtohard".  Any directory in your $PATH will work just fine.  After putting it there, make sure to run:
```
chmod +x /usr/local/bin/symtohard
```


```

#!/bin/bash
#Converts all symbolic links in a directory to hard links. See http://ubuntuforums.org/showthread.php?t=1508728 for any updates/problems.
if [ -d "$1" ] ; then
    echo "About to convert all symlinks in '$1' "
#    if [ "$confirm" == "y" ]; then
        cd "$1" &&
        FOLDER="*"
        for file in $FOLDER
        do
            if [ -L "$file" ]; then
                target=$(readlink "$file")
                echo "Converting link to $file"
                mv "$file" "$file.old" &&
                ln "$target" "$file" &&
                rm "$file.old"
            else
                echo "$file not a symlink, skipping"
            fi
        done
#    else
#        echo "Exiting. No changes made."
#    fi

else
    echo "$1 is not a directory, exiting."
fi
exit

```

The run this monster with the correct path to recursivly replace all symlinks.  This DOES NOT ASK FOR CONFORMATION, it just runs through.  Be careful!

```
find /directory_with_syms -type l -exec dirname '{}' \; | sort | uniq | xargs -L 1 -I {} symtohard "{}"
```

If you would like to be prompted per directory (but not per file) add "-p" right after xargs.

Happy hardlinks!

---

### Post by ysangkok on 2011-12-04
Currently fails to detect cross-device links, so those links will be renamed <filename>.old.

Here's how to revert:

```
for i in $(find . -iname '*.old' -print | rev | cut -f2- -d. | rev); do mv -vi $i.old $i; done
```

---

