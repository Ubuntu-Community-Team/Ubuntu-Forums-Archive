---
title: "Copy multiple files at the same time"
date: 2012-04-21
forum: General Help
---

### Post by sinnadyr on 2012-04-21
Hi,

I want to be able to open several threads when copying a folder with many files, like I am doing when using filezilla for transfers (transfer up to 10 files at the same time).

Can anyone help me with how to do this? 

The reason is that I have an sftp-drive I want to copy data from, and my ISP only allows for 500kb/s per sftp transfer, so I will increase my speed drastically if I copy several at once. 


Thank you very much in advance

---

### Post by SeijiSensei on 2012-04-21
Just run multiple instances of the sftp command from the command line in the background like this:

```
sftp stuff &
sftp stuff &
sftp stuff &

```

And so forth.  The "&" runs the command in the background.  You can do this with any command, not just sftp, of course.

---

### Post by sinnadyr on 2012-04-21
Thank you, but I was trying to avoid that way and find a more automated one.
Maybe a script of some kind?

---

### Post by SeijiSensei on 2012-04-22
Well, you could write a simple script that iterates over the list of files and spawns the sftp jobs.  You'd have to use sftp to get the remote's directory listing then iterate over the files in a for loop and spawn the individual sftp transfers.  I haven't used FTP in a long time, so I'm probably not the best person to write this.  Schematically it would look something like:

```

#!/bin/bash

# get file list
FILES=$(sftp commands_to_get_file_list)

for f in $FILES
do
     sftp user:pass@host:/pub/$f . &
done

```

---

### Post by sinnadyr on 2012-04-22
Thank you very much! This should be easy enough to test out, but remember that I have just mounted the sftp drive, so I am just using basic cp and ls commands to do the operation, which will make it even easier :) 


Could this work? 

```
#!/bin/bash
FROM_DIR = $1
TO_DIR = $2

# get file list
FILES=$(ls -1 FROM_DIR)  

for f in $FILES
do
     cp $f $TO_DIR &
done
```

This will work better:

```

#!/bin/bash
FROM=$1
TO=$2

for f in $(ls -1 $FROM)
do
        cp -r $FROM/$f $TO &
done

```

---

### Post by SeijiSensei on 2012-04-22
If you have actually mounted the remote into the local filesystem it's even easier than that:

```

#!/bin/bash
FROM_DIR = $1
TO_DIR = $2

cd $FROM_DIR

for f in *
do
    cp $f $T0_DIR &
done

```

I mentioned using a list of files in my original post because I thought you needed to get the list from the FTP server.  If it's mounted locally, the "for f in *" syntax is the easiest method.

If the directories have embedded spaces, remember to use the syntax

```
myscript '/path/to/directory one' '/path/to/directory two'
```

to invoke the script.  Also you'll need to surround the file and directory variables in the cp command with double quotes like this:

```
cp "$f" "$TO_DIR" &
```

Embedded spaces are generally a pain in the neck; I use underscores or hyphens when naming files and directories instead.

---

### Post by sinnadyr on 2012-04-22
Thanks!

I have never spaces in file/folder names, so that is not a problem. 
Got the script to work, now I am working on a way to restrict the script to only copy 15 files at the same time. A bit hard since I never know how many files I will be copying, but I assume its never over a thousand. 

So far I got this
```
#!/bin/bash

# First parameter is the folder to be copied
FROM=$1

# Second parameter is the folder to copy to
TO=$2

# Number of files to be copied
NUMB_FIL=$(ls |wc -w)
FLOAT=NUMB_FIL/15
INT=${FLOAT/\.*} # Convert to integer

# Number of iterations
ITERATIONS = $INT

# Number of files per iteration
MAX_FILES=15

echo creating directory $TO/$FROM
mkdir $TO/$FROM

until [ $ITERATIONS -eq 0 ]; do
        for f in $(ls -1 $FROM)
        do
                cp -r $FROM/$f $TO/$FROM &
                echo copying $f to $TO
        done
$ITERATIONS -= 1

done

```
This will not work at the moment, need to figure out how to continue. The for loop will take all the files right know, but I hope you can see the whole idea.

The ```
cd $FROM_DIR
``` was not a bad idea ;)

---

### Post by erind on 2012-04-22
> **sinnadyr said:**
> Thanks!

I have never spaces in file/folder names, so that is not a problem. 
Got the script to work, now I am working on a way to restrict the script to only copy 15 files at the same time. A bit hard since I never know how many files I will be copying, but I assume its never over a thousand. 

[...]

You'd need a counter (say* c*) and the '*wait*' command to achieve that restriction, so the code will look something along the lines of:

```
...
[B]max=${3:-15}
[COLOR=Black]c=1[/COLOR][/B]

for f in $FROM/*
 do
   cp -r $FROM/"$f" $TO/$FROM &
   echo copying "$f" to $TO

   **[COLOR=Black][ $c -eq $max ] && c=0 && wait[/COLOR]**
   [COLOR=Black]**c=$(( $c + 1 )) **[/COLOR]
 done

##adjust code as needed
```With the code above, you can optionally supply the maximum number of files to be copied as the third ($3) positional parameter (else it'll default to 15). Also there's no need to calculate beforehand the number of files to be copied - it'll copy all the files supplied until the end of the loop, in batches with '*max*' number of files.

---

### Post by sinnadyr on 2012-04-23
erind, you're magnificent! 

Thanks a lot!

EDIT: Doh! It did not work :\ Can't figure out why by it makes duplicates of the "from" folder.

---

### Post by sinnadyr on 2012-04-23
erind: could you test your script and paste a working one? Really had my hopes up there

---

### Post by erind on 2012-04-23
My point was simply to illustrate the usage of the *counter* and '*wait*' command, and the code was meant to be further tested.
But the issue seems to be simply the copy command above. Try: **cp -r "$f" "$TO" &** instead, which was also posted by *SeijiSensei* above. 

```
#!/bin/bash

# First parameter is the folder to be copied
FROM="$1"

# Second parameter is the folder to copy to
TO="$2"

# Third optional parameter to supply max number of files in a batch
max=${3:-15}

c=1

for f in "$FROM"/*
 do
   [COLOR=Red]cp -r "$f" "$TO" &[/COLOR]
   echo "Copying $f to $TO"

   [ $c -eq $max ] && c=0 && wait
   c=$(( $c + 1 )) 
 done
```[tested fine]

---

### Post by sinnadyr on 2012-04-24
Yes, I tried editing it, but missed the fact that that line had a mistake.

Thank you both very much. Guess this could be useful for others as well

---

