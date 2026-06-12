---
title: "Bash - check if all the file names are correct"
date: 2010-09-23
forum: General Help
---

### Post by EgoGratis on 2010-09-23
Hi. I have bash script for converting files. I have a problem. If file name is "corrupted" then mv command for that file will not work. For example file with "-" in front of the name.

Is there a way to check if in some folder (subfolder) all the files have correct file names or they don't?

If they are all correct -> OK proceed with execution of the script!

If they are not all correct -> NOT OK stop with execution of the script!

Thanks for answers!

---

### Post by lloyd_b on 2010-09-23
You're probably doing something like```
for FILE in *; do
``` to get the filenames, which has problems with some filenames (the "-name" example is one of those).

You can avoid this issue by using the 'find' command instead of a wildcard:```
for FILE in `find .`; do
```The find command will always return the filename with either a directory name or "./" prepending to the front, which will allow programs such as "mv" or "rm" to handle them correctly.

Note that spaces in filenames will still cause problems even using this method.  You can resolve this by using a 'read' in the loop, rather than a typical 'for' loop```
find . -name "*.jpg" |
while read FILE; do
    mv "$FILE" /home/user/otherdir
done
``` will correctly handle any file name that's legal in Linux, provided that you wrap $FILE with parentheses.

Lloyd B.

---

### Post by EgoGratis on 2010-09-24
OK i will test this later on. I takes a bit of understanding and testing for me.

But bottom line. There is no command for bash to check if file names are valid or not?

---

### Post by Vaphell on 2010-09-24
you can check if the file exists
```

if [ -f testfile ]
then
echo testfile exists!
fi
```

as for validity of hypothetical file name, almost all characters are allowed - for example, according to wikipedia, ext2, ext3 and ext4 allow for any char except null (\0) and /. Detect any of those in string - name is not legal

---

### Post by lloyd_b on 2010-09-25
> **EgoGratis said:**
> OK i will test this later on. I takes a bit of understanding and testing for me.

But bottom line. There is no command for bash to check if file names are valid or not?

The problem is that those filenames *are* valid, as far as the kernel and filesystem drivers are concerned.  They're just a headache for certain utility programs.

If you want a "find files that will give utilities problem" command, there's none by default, but here's a script that should do exactly that:```
#!/bin/bash

# We need to 'cd' into directories for this to be valid, but we'll need 
# remember the starting directory so we can 'cd' back to it.
STARTDIR=`pwd`

# Use 'find' to get a list of all files and directories in or below the
# current directory, and then process that list
find . -print |
while read FILE; do
    # Separate the directory component from the filename component
    DIRNAME=${FILE%/*}
    FILENAME=${FILE##*/}

    # 'cd' into that directory
    cd "$DIRNAME"

    # try to 'stat' the filename, discarding all output
    stat $FILENAME > /dev/null 2>&1
   
    # Now check the return code from 'stat' to see if it failed
    if [ "$?" -ne 0 ]; then
        echo "Unable to stat file '$FILE' - possible 'bad' filename"
    fi

    # cd back to starting directory before moving on to next file
    cd "$STARTDIR"
done
```I've deliberately left the quotation marks from around $FILENAME on the stat command - this will cause it to generate an error if there are spaces in the filename as well as things like a '-' character on the front of the name.  Basically, if passing the filename to a command like "mv $FILE /home/user/somewhere" will cause any problems, this should detect it.

Lloyd B.

---

