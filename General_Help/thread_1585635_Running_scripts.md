---
title: "Running scripts"
date: 2010-09-30
forum: General Help
---

### Post by ali999 on 2010-09-30
Hey,

Although I have been using ubuntu for some time now, i am quite the noob when it comes to scripts. I recently acquired a script that allows you to easily open files through the terminal. I put it in the usr/bin folder as this is somewhere my path variable points to. Made it executable through chmod. But cannot get it to run. Anybody have any ideas as to what I may be doing wrong? Thanks in advance.

---

### Post by CharlesA on 2010-09-30
Need more information:

What is the name of the script and how are you trying to run it?

---

### Post by madinc on 2010-09-30
hi you should make a bin directory in your home directory export it to the PATH and put your script there.

---

### Post by CharlesA on 2010-09-30
> **madinc said:**
> hi you should make a bin directory in your home directory export it to the PATH and put your script there.

I can verify that this works. :)

---

### Post by holiday on 2010-09-30
/usr/bin might be a better choice. Did you forget the first /? Your post doesn't have it so its possible that the search path is looking down from your pwd (current directory).

But I agree with the above posts suggesting that your personal scripts should go in a sub of your home directory. 

I keep a ~/sh directory for my scripts. /usr/bin is more for BINary executables and scripts are text. This is a niggling point and has no functional advantage really. It's just neater.

---

### Post by madinc on 2010-09-30
if you want to try my way do this.
open terminal.

```
mkdir bin
```in /home/username press ctrl h  look for the .bashrc file open it and add this at the end;

```
export PATH
PATH="/home/username/bin:$PATH"
```save it restart the pc put your script there open the terminal type the name of your script press enter and thats it.

---

### Post by ali999 on 2010-10-01
i tried the method above but I still cannot manage to get it to work. I created a folder in my home directory called bin and put the script there. used chmod to make it exucatble. Then modified my .bashrc file as stated and restarted. 
Im attaching the script below so hopefully that might help. It basically allows files to be easily opened through terminal using gnome. I am not exactly sure how this works as I did not write this and my knowledge of scripts is very limited. I got it from a professor at my university after I saw him using it. 
the script is in a file called "go.sh". To run it you just go to terminal and type "go" followed by the filename.

```
#!/bin/sh

ARGS=" 2> /dev/null"

if [ $# = 0 ];  then
    # Find the most recent regular file that has been modified.
    FILE=$(find . -maxdepth 1 -type f -print0 |xargs -0 ls -t1|head -n1)

elif [ $# = 1 ]; then

    if [ -e "$1" ]; then
        FILE=$1  # A file given on the command line.
    else
    # Find the most recent file with the file extension given on the command line.
    FILE=$(find . -maxdepth 1 -name "*.$1" -type f -print0 |xargs -0 ls -t1|head -n1)
    fi

else echo Too many input files!

fi

if [ ${#FILE} = 0 ]; then
    echo No files!
    exit 1
fi

# Assume gnome and open the file.
echo gvfs-open "$FILE" "$ARGS"
eval gvfs-open "'$FILE'" "$ARGS"

```

---

### Post by madinc on 2010-11-16
try to change
```
#!/bin/sh
```to
```
#!/bin/bash
```

---

### Post by efflandt on 2010-11-16
The reason for what *madinc* says is that many people may assume that the default shell for /bin/sh is bash.  But in Ubuntu /bin/sh is now **dash**, which is slimmer to be quicker, but it does not do everything that **bash** does.

---

### Post by deconstrained on 2010-11-16
Try 'apropos' and 'which' on eval and gvfs-open (i.e. 'which gvfs-open'). If they come up null, they don't exist on your system or aren't in your $PATH, so you can't call them from within a script. Furthermore, this bears asking: why the need for 'eval gvfs-open'? You could just use 'gnome-open' instead.

Also, on a personal note: putting user scripts in /bin, /usr/bin (etc) or anywhere other than tucked away neatly in a userscripts folder in your home directory pointed to in $PATH is the omg-fugly-messy way.

---

