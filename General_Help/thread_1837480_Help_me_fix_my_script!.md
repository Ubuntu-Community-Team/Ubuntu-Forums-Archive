---
title: "Help me fix my script!"
date: 2011-09-01
forum: General Help
---

### Post by sauerpauer on 2011-09-01
I don't think there is a specific forum geared towards this sort of question, so at risk of letting the thread get buried in a matter of minutes, I'll post my question here.

I needed to fix all the permissions in a directory full of files and other directories.  I don't see any way to use chmod to fix all of them at once (since chmod -R doesn't seem to discriminate between directories and files), and I don't want these files to all have execution privs, so I decided to do what we're supposed to do best and write a script to fix them all automagically! :D

The only problem is that I'm definitely a beginning bash scripter, so I'm learning as I go (via extensive use of info and man pages!).  I really have two questions here:

1 - If a script copies itself somewhere else, can that script run itself (recursively)?

2 - Why isn't my for loop working?  I get the error
```
./fix_perms: line 28: syntax error near unexpected token `cp'
./fix_perms: line 28: `    cp ./fix_perms ./'$i'fix_perms.temp;'
```
I can't seem to figure out how to properly call $i, or maybe I need to fix the list that for is using--I'm not sure.  This is the primary point I need help on.

I know that there is some scripting guru here somewhere that is giggling at my mistake, but I'd love some help.  Thanks!

My humble script:
```
#!/bin/bash

# This script will reset the permissions of a directory and its contents such
# that the directories and files all have normal permissions (755 and 644,
# respectively.  It should only rely on coreutils.

# copy this script to the directory you want to  "fix", then run it.


# realized here I could skip the sed part if I told ls to keep the escape char
# # fix the files, then the directories in the current directory
# ls -Ap1 | grep -v '/$' | sed -e s/\^/\"/g -e s/\$/\"/g | xargs chmod 644;
# ls -Ap1 | grep    '/$' | sed -e s/\^/\"/g -e s/\$/\"/g | xargs chmod 755;

# fix the files, then the directories in the current directory
ls -bAp1 | grep -v '/$' | xargs chmod 644;
ls -bAp1 | grep    '/$' | xargs chmod 755;


# run this script in every directory, recursively

# make a list of directories
DIRECTORY_LIST=`ls -bAp1 | grep '/$'`;

# for every directory in the current directory
for i in $DIRECTORY_LIST
    # copy this script into the directory, run it, then delete the script
    cp ./fix_perms ./'$i'fix_perms.temp;
    ./'$i'.fix_perms.temp;
    rm ./'$i'.fix_perms.temp;

done
unset i;
unset DIRECTORY_LIST;

```

---

### Post by papibe on 2011-09-01
Quote your variables with " not ', e.g.:
```
"$i"
```
Regards.

---

### Post by sauerpauer on 2011-09-01
> **papibe said:**
> Quote your variables with " not '
Regards.
Ah, thanks.  Still get the same error though, even with ".
```
./fix_perms: line 28: syntax error near unexpected token `cp'
./fix_perms: line 28: `    cp ./fix_perms ./"$i"fix_perms.temp;'
```
I don't think it would give me a syntax error for trying to copy a script that is already running...

---

### Post by sisco311 on 2011-09-01
I don't even know where to start... :)

Check out the BashGuide, BashFAQ and BashPitfalls @  [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

0.) "USE MORE QUOTES!" They are vital. Also, learn the difference between ' and " and `. See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
and
[http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words)

1.) ls shows you a representation of files. They are NOT file names (for simple names, they mostly happen to be equivalent). Do NOT try to parse it. [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

2.) Don't store the directory list in a (non-array) variable

3.) also see BashPitfall #1

EDIT: forgot to add

4.) [http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082) -- Why is $(...) preferred over `...` (backticks)?

and

5.) The infamous "Advanced" Bash Scripting Guide should be avoided unless you know how to filter out the junk. It will teach you to write bugs, not scripts. In that light, the BashGuide was written: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by papibe on 2011-09-01
I missed this one:
```
for i in $DIRECTORY_LIST
```
Change it to:
```
for i in "$DIRECTORY_LIST"
```
That would take care of the syntax error, but if there's spaces in the filenames it may not provide the result you are looking for.

Regards.

---

### Post by sisco311 on 2011-09-01
BTW: if you have find on your system (this is the Ubuntu forum, so I have to assume you have), you can run:
```
find /path/to/dir -type f -exec chmod 0644 '{}' +
find /path/to/dir -type d -exec chmod 0755 '{}' +

```

Or you could use chmod's uppercase X symbolic mode option. X means: add execute/search  only if the file is a directory or already has execute permission for some user.

---

### Post by sauerpauer on 2011-09-01
The find combination did the trick.  I am still going to work on the script until I can operate on a defined set of files in directories recursively, even though the end goal has been met (more elegantly, at that).  Thanks for your help!

Edit: I'll mark this as solved once I get the recursion to work properly, no matter the method.

---

### Post by sisco311 on 2011-09-01
> **sauerpauer said:**
> The find combination did the trick.  I am still going to work on the script until I can operate on a defined set of files in directories recursively, even though the end goal has been met (more elegantly, at that).  Thanks for your help!


**man find** :)

find has a lot of test options like: -name, -iname, -regex and so on...

> **sauerpauer said:**
> 
Edit: I'll mark this as solved once I get the recursion to work properly, no matter the method.

Please forget the the recursion :evil:

Read the links I posted & re-think the design of your script.

---

### Post by sauerpauer on 2011-09-02
> **sisco311 said:**
> Please forget the the recursion :evil:

Nope.  I do appreciate all of your help so far though :D
> **sisco311 said:**
> Read the links I posted & re-think the design of your script.
Just finished, and I learned a ton.  I'm sure there are going to be small problems that I overlooked by not knowing the nuances of how bash works, but there is one problem left with my script (I think).

For some reason, the revised script doesn't work on every file like it should - I think calling the function recursively breaks out of the for loop.  Results:
```
chris@machinery:~$ ./fix_perms testdir
chris@machinery:~$ ls -lR testdir
testdir:
total 16
drwxr-xr-x 3 chris chris 4096 2011-09-02 15:38 dir1
-rwxrwxrwx 1 chris chris    0 2011-09-02 15:38 file

testdir/dir1:
total 16
drwxr-xr-x 2 chris chris 4096 2011-09-02 15:38 dir2
-rwxrwxrwx 1 chris chris    0 2011-09-02 15:38 file1

testdir/dir1/dir2:
total 12
-rw-r--r-- 1 chris chris 0 2011-09-02 15:38 file2
```

Current script:
```
# This script fixes permissions. This script is built on the
# condition that you can't give chmod a list of files (e.g. with find).  It is
# mostly a learning tool for using recursion in a script.

fixdir () {
    cd "$1"

    # for every file in this directory
    for FILE in * ; do
    
        # if it is a regular file, fix it
        if [ -f "$FILE" ] ; then
            chmod 644 "$FILE"
        fi
            
        # if it is a directory, fix it, then run fixdir() inside it
        if [ -d "$FILE" ] ; then
            chmod 755 "$FILE"
            fixdir "$FILE"
        fi
    done
}

# first, for testing purposes, give everything full permissions
chmod -R 777 "$1"

# if given an argument, fixdir it
if [ -x "$1" ] ; then
    fixdir "$1"
# otherwise, grab an argument from user
else
    echo 'Which directory to fix?'
    read DIR
    fixdir "$DIR" 
fi
```
Edit: substituted [[ for [ after reading about ['s problems, even though it shouldn't affect this script.

---

### Post by sisco311 on 2011-09-02
By convention, we capitalize environment variables (PAGER, EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...). All other variable names should contain at least one lowercase letter. Remember that variable names are case-sensitive; this convention avoids accidentally overriding environmental and internal variables.

Recursion is tricky, isn't it? :)

If you cd into a directory, you have to cd back to the original, right?

I didn't test it, but something like:
```
fixperm ()
{
  cd "$1"
  ...
  cd -
}

```
should work.

In bash you can use globstar to match files recursively:
```
shopt -s globstar nullglob
for file in ./**/*
do
    if [[ -d "$file" ]]
    then
        :
    elif [[ -f "$file" ]]
    then
        :
    else
        echo 'not a regular file or a dir'
    fi
done
```

---

### Post by sauerpauer on 2011-09-02
> **sisco311 said:**
> By convention, we capitalize environment variables (PAGER, EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...). All other variable names should contain at least one lowercase letter. Remember that variable names are case-sensitive; this convention avoids accidentally overriding environmental and internal variables.

Recursion is tricky isn't it? :)

If you cd into a directory, you have to cd back to the original, right?

Yes, recursion can be tricky.  I think it operates differently in bash than I remember it working in other languages.

The script is working the way it should now, and I learned a bunch (this was my first bash script 8-) ).  Thanks so much for your help!

In case anybody comes across this thread and might learn from my experiences, the full, working script is:

```
#!/bin/bash

# This script will reset the permissions of a directory and its contents such
# that the directories and files all have normal permissions (755 and 644,
# respectively. This script is built assuming you can't use one of the other
# (more elegant) methods of doing multiple operations on a directory. It is
# mostly an exercise for using recursion in a script, among other things.


fixdir () {
    cd "$1"

    # for every file in this directory
    for file in * ; do
        
        # if it is a regular file, fix it
        if [[ -f "$file" ]] ; then
            chmod 644 "$file" 
        fi  
                
        # if it is a directory, fix it, then run fixdir() inside it
        if [[ -d "$file" ]] ; then
            chmod 755 "$file"
            fixdir "$file"
       fi  
    done
    cd ../ 
}

# if given an argument, fixdir it
if [[ -x "$1" ]] ; then
    fixdir "$1"
# otherwise, grab an argument from user
else
    echo 'Which directory to fix?'
    read dir 
    fixdir "$dir" 
fi

```

---

### Post by sisco311 on 2011-09-02
> **sauerpauer said:**
> 
The script is working the way it should now, and I learned a bunch (this was my first bash script 8-) ).  Thanks so much for your help!


Cool! You read the links I provided and as far as I tell, you really learned a lot.

It was my pleasure to help you!

---

