---
title: "Scripting/batching help"
date: 2010-10-14
forum: General Help
---

### Post by robbiemacg on 2010-10-14
I'm working my first real world scripting problem. I have a batch of epub/ebook files that need to be changed slightly before being sent to a retailer.

I need to crack open each file, remove an XML file (it has the same name in each instance), then zip the file back up again.

I can do this via the Command Line for an individual file via a series of commands something like this:

```
cp ~/Desktop/OriginalFiles/<fileName>.epub ~/Desktop/RetailerFiles/<fileName>.zip && unzip -o ~/Desktop/RetailerFiles/<fileName> -x *DATAFILE.xml -d ~/Desktop/RetailerFiles/<fileName> && cd ~/Desktop/RetailerFiles/<fileName> && epub ../Homing.epub && cd .. && rm -r <fileName>.zip <fileName> && cd
```I move/rename the file; extract it's contents (less the offending XML file); package the ebook back up again (using a custom function); clean up and return to my home directory. *Apologies if these seems clumsy. Again, this is my first attempt at solving a problem with a script. 

Can anyone help me with a script/strategy that would allow be to process a batch of files (each with a unique filename)? I want to be able to point a script at a directory and have the above commands executed for each of the epub files within.

---

### Post by d5xtgr on 2010-10-14
I'm not good enough with the syntax to understand all you are accomplishing in that code, but could you accomplish at least sections of it using the * wildcard where you have filename?

---

### Post by d5xtgr on 2010-10-14
There is a script here that performs a different task but similarly to what I think you want to do- can you use the same structure to perform the tasks you require?  A bit more elegant than trying to use the wildcard, which will give problems if you have other identically named files in the zip.

[http://ubuntuforums.org/showthread.php?t=1588954](http://ubuntuforums.org/showthread.php?t=1588954)

---

### Post by xircon on 2010-10-14
```
#!/bin/bash

for file in *

do
  
   ls -l "$file"  
  
done

exit 0

```

From [http://tldp.org/LDP/abs/html/loops1.html#LISTGLOB](http://tldp.org/LDP/abs/html/loops1.html#LISTGLOB)

Just play around a bit!

---

### Post by robbiemacg on 2010-10-14
Thanks, [d5xtgr]("http://ubuntuforums.org/member.php?u=1130246"), for the speedy response. I have experimented with wildcards, and had little success. 
* is useful for selecting files, but it's not a container. I could find every epub file and execute a command, but I'm not sure how I'd establish identity (have each file saved with it's own original, unique filename).
Any thoughts?

---

### Post by robbiemacg on 2010-10-14
Thanks, [xircon]("http://ubuntuforums.org/member.php?u=662795").
I'll take a look at that thread.

---

### Post by lloyd_b on 2010-10-14
> **xircon said:**
> ```
#!/bin/bash

for file in *

do
  
   ls -l "$file"  
  
done

exit 0

```

From [http://tldp.org/LDP/abs/html/loops1.html#LISTGLOB](http://tldp.org/LDP/abs/html/loops1.html#LISTGLOB)

Just play around a bit!

The only problem with that construct is that it produces weird results if there happens to be a space in a file name (the shell treats spaces a "field separators", so a file named "this file" will be treated as two different items ("this" and "file").

The usual way around this is to use a read loop:```
ls * |
while read FILENAME
do
    ls -l "$FILENAME"
done
```

There are limits to this method, but they shouldn't be a problem in this example (it's only an issue if you want to set a variable inside the while loop and access it outside the loop).

Lloyd B.

---

### Post by amauk on 2010-10-14
completely untested

```
#!/bin/bash

# Top level directory,
# any .epub file under this directory
# will be modified
TOP_DIR="$HOME/Desktop/OriginalFiles"

# Output directory
# Modified epubs will be saved here
OUTPUT_DIR="$HOME/Desktop/OutputFiles"

# Create Output directory if it doesn't exist
if [ ! -d "$OUTPUT_DIR" ]; then
    mkdir -p "$OUTPUT_DIR"
fi

IFS=$'\n'
EPUBS=$(find "$TOP_DIR" -type f -name '*.epub')

for EPUB in $EPUBS; do
    cp "$EPUB" "${EPUB}.bak"
    mv "$EPUB" "${EPUB}.zip"
    mkdir -p "${EPUB}.d"
    unzip -o "$EPUB" -x *DATAFILE.xml -d "${EPUB}.d"
    cd "${EPUB}.d"
    epub "${OUTPUT_DIR}/$(basename "$EPUB")"
    rm -rf "${EPUB}.d"
    rm -f "$EPUB"
done
```

---

### Post by xircon on 2010-10-14
```

steve@n5010 ~/Scripts> ./test.sh 
-rwxr-xr-x 1 steve steve 54 2010-09-05 22:23 cdock.sh
-rwxr-xr-x 1 steve steve 409 2010-09-04 08:20 cdockv2.sh
-rwxr-xr-x 1 steve steve 119 2010-10-14 23:08 test.sh
steve@n5010 ~/Scripts> 

Added "te st.sh"
steve@n5010 ~/Scripts> ./test.sh 
-rwxr-xr-x 1 steve steve 54 2010-09-05 22:23 cdock.sh
-rwxr-xr-x 1 steve steve 409 2010-09-04 08:20 cdockv2.sh
-rw-r--r-- 1 steve steve 119 2010-10-14 23:16 te st.sh
-rwxr-xr-x 1 steve steve 119 2010-10-14 23:08 test.sh
steve@n5010 ~/Scripts> 

```

Lloyd, 

Not seeing any problems with spaces in file names, I added a "te st.sh" to the directory, output looks fine.

Steve

---

### Post by CharlesA on 2010-10-14
The quotes around the varible make it work with filenames that contain spaces. :)

---

### Post by xircon on 2010-10-14
> **CharlesA said:**
> The quotes around the varible make it work with filenames that contain spaces. :)

:) Getting late, time for bed!!

---

### Post by robbiemacg on 2010-10-14
Thanks all.
The solution proposed by [amauk]("http://ubuntuforums.org/member.php?u=384906") looks extremely promising.
I'm going to test it first thing in the a.m. on my work computer and will share results here along with anything else I learn.

---

### Post by lloyd_b on 2010-10-15
> **xircon said:**
> ```

steve@n5010 ~/Scripts> ./test.sh 
-rwxr-xr-x 1 steve steve 54 2010-09-05 22:23 cdock.sh
-rwxr-xr-x 1 steve steve 409 2010-09-04 08:20 cdockv2.sh
-rwxr-xr-x 1 steve steve 119 2010-10-14 23:08 test.sh
steve@n5010 ~/Scripts> 

Added "te st.sh"
steve@n5010 ~/Scripts> ./test.sh 
-rwxr-xr-x 1 steve steve 54 2010-09-05 22:23 cdock.sh
-rwxr-xr-x 1 steve steve 409 2010-09-04 08:20 cdockv2.sh
-rw-r--r-- 1 steve steve 119 2010-10-14 23:16 te st.sh
-rwxr-xr-x 1 steve steve 119 2010-10-14 23:08 test.sh
steve@n5010 ~/Scripts> 

```

Lloyd, 

Not seeing any problems with spaces in file names, I added a "te st.sh" to the directory, output looks fine.

Steve

This is a brain fart on my part.  There is an issue with spaces in a for loop, but only when the list is being fed by the output from a command, rather than a wildcard.  For instance:```
for FILE in `find . -name *.txt -print`
do
    ls -l "$FILE"
done
```will have that "spaces in filenames" issue.  The while read loop I suggested is to compensate for this.

Lloyd B.

---

### Post by asmoore82 on 2010-10-15
amauk is 99.9% there. As is it will certainly break if filenames OR directories have spaces in them.

You should avoid mixing up `ls` and `find` commands in a `for` loop.
Use the shell's built-in wildcard `*` ability - it's faster and less error prone.

```
#!/bin/bash

# Top level directory,
# any .epub file under this directory
# will be modified
TOP_DIR="$HOME/Desktop/OriginalFiles"

# Output directory
# Modified epubs will be saved here
OUTPUT_DIR="$HOME/Desktop/OutputFiles"

# Create Output directory if it doesn't exist
if [ ! -d "$OUTPUT_DIR" ]; then
    mkdir -p "$OUTPUT_DIR"
fi

for EPUB in "$TOP_DIR/"*.epub
do
    if [ -f "$EPUB" ]
    then
        cp "$EPUB" "${EPUB}.bak"
        mv "$EPUB" "${EPUB}.zip"
        mkdir -p "${EPUB}.d"
        unzip -o "$EPUB" -x *DATAFILE.xml -d "${EPUB}.d"
        cd "${EPUB}.d"
        epub "${OUTPUT_DIR}/$(basename "$EPUB")"
        rm -rf "${EPUB}.d"
        rm -f "$EPUB"
    fi
done
```
^just remember that an unmatched wildcard `*` is left untouched.
The inner `if` statement protects this case.

This also protects in the case of a directory with a matching name.
You really want to be 100% sure before you start using `mv` and `rm` :D.

It's worth noting, however, that this particular wildcard `*` solution is
not doing a recursive search as `find` would have. If an exhaustive search
is really necessary, you could use a recursive bash function.

P.S. The `ls | while` construct is a neat hack but still breakable.
It is not illegal for a newline character to be a part of a filename in Linux.
The shell's wildcard `*` is OK even in this extreme case.

---

### Post by robbiemacg on 2010-10-15
Many thanks to [asmoore82]("http://ubuntuforums.org/member.php?u=341737") and [amauk]("http://ubuntuforums.org/member.php?u=384906")! I think I'm almost there now.

I've been working with the scripts you built, making small changes, testing different options. Everything seems to be working correctly except for this little bit of code:
```
cd "${EPUB}.d"
epub "${OUTPUT_DIR}/$(basename "$EPUB")"
```I don't think the **cd** command is changing the working directory, or it might not be poited at the correct directory. 

To be clear: the directory is created (and it's created where we'd expect, in TOP_DIR); it contains the files we want it to (DATAFILE.xml is removed); something falls apart when we go to change the working directory.

Any thoughts? I'm getting close, but I really need some help.

When I **cd** manually and execute the **epub** function everything works. 
(NOTE: The **epub** function only works when executed from within the directory contain the files to be packaged... for now.)

---

### Post by xircon on 2010-10-15
Add:

echo $PWD
sleep 2000

This will echo the current directory to screen.

---

### Post by robbiemacg on 2010-10-15
A little more about this **epub** function...
Perhaps it's also a little 'inelegant.' I'll share it with the group.

Right now, I exicute the function from within the directory containing the files I want to package up and provide a file name.

The function looks like this:
```
function  epub()
{
rm -f $@; zip -q0X $@ mimetype; zip -qXr9D $@ *
}
``` It's really just some instructions for how (in what order) to zip up a bunch of files.

Could we change this and avoid having to **cd** in the script I'm trying to develop?

---

### Post by robbiemacg on 2010-10-15
Hello again, [xircon]("http://ubuntuforums.org/member.php?u=662795").
Where do you think I should add that bit of code? Within the EPUB if loop? Should it be with the **cd** command? I'm not clear.

---

### Post by xircon on 2010-10-15
> **robbiemacg said:**
> Hello again, [xircon]("http://ubuntuforums.org/member.php?u=662795").
Where do you think I should add that bit of code? Within the EPUB if loop? Should it be with the **cd** command? I'm not clear.

Yes after the cd command to check it is changing to the expected directory.

---

### Post by robbiemacg on 2010-10-15
At [xircon]("http://ubuntuforums.org/member.php?u=662795")'s suggestion, I double checked that the **cd** command was having the correct effect. It was. 
The problem was the **epub** function. I decided to build the instructions for executing the function right into the script and that seems to have taken care of my problem.

I made a couple of additional small changes in an attempt to simplify things. For one thing, I'm no longer creating a back up file, just leaving the original files where they are. Is this the sort of thing [asmoore82]("http://ubuntuforums.org/member.php?u=341737") was warning against above, or is it acceptable?

The code bellow seems to do the trick, and can handle batches of epubs without problem:

```
#!/bin/bash

# Top level directory,
# any .epub file under this directory
# will be modified
TOP_DIR="$HOME/Desktop/OriginalFiles"

# Output directory
# Modified epubs will be saved here
OUTPUT_DIR="$HOME/Desktop/OutputFiles"

# Create Output directory if it doesn't exist
if [ ! -d "$OUTPUT_DIR" ]; then
    mkdir -p "$OUTPUT_DIR"
fi

# MAKE EPUB
function  epub()
{
rm -f $@; zip -q0X $@ mimetype; zip -qXr9D $@ *
}

for EPUB in "$TOP_DIR/"*.epub
do
    if [ -f "$EPUB" ]
    then
        cp "$EPUB" "${EPUB}.zip"
        mkdir -p "${EPUB}.d"
        unzip -o "$EPUB" -x *Shortcovers.xml -d "${EPUB}.d"
        cd "${EPUB}.d"
        epub "${OUTPUT_DIR}/$(basename "$EPUB")"
        cd "$TOP_DIR"
        rm -rf "${EPUB}.d"
        rm -rf "$EPUB.zip"
    fi
done
```

---

### Post by robbiemacg on 2010-10-19
All right, gang, I'm satisfied with the way this script is working now. I'm going to mark this thread solved and move on to the next challenge. 
Thanks for your helpful comments and good ideas!

---

