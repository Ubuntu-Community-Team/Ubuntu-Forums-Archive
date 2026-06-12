---
title: "Help with my bash script"
date: 2011-09-22
forum: General Help
---

### Post by shibby4555 on 2011-09-22
So I apologize if this is in a wrong section.
I'm trying to write a simple shell script that shreds entire folders rather than just individual files.
I intend to do it by individually deleting each file within a folder. but i can't figure how to go about listing out each file within a folder then auto deleting it.

Heres the code
```

#!/bin/sh

echo 

echo "Enter the directory that you want to destroy:"
read directory

echo "Enter the number of times you want the file overwritten (I recommend 10):"
read overwrite

echo
echo -n     "You are about to permanently delete $directory and overwrite it $overwrite time(s).

            Do you want to proceed (Y/N)?"
read answer
if test "$answer" != "Y" -a "$answer" != "y";
then exit 0;
fi

gnome-terminal -x bash -c "shred -n $overwrite -z $directory"
gnome-terminal -x bash -c "rm -rf $directory"

```

---

### Post by NERDMAN! on 2011-09-22
i'm no expert but i do know the "dir" command lists all files within the active directory. sorry i cant help with anything more than that. if i think of something i'll post it.

---

### Post by patryk77 on 2011-09-22
for i in $directory/*; do echo shred -n $overwrite "$directory/$file"; done

Remove echo to do the actual shredding, after *MUCH MUCH MUCHO* testing

---

### Post by ofnuts on 2011-09-22
> **shibby4555 said:**
> So I apologize if this is in a wrong section.
I'm trying to write a simple shell script that shreds entire folders rather than just individual files.
I intend to do it by individually deleting each file within a folder. but i can't figure how to go about listing out each file within a folder then auto deleting it.

Heres the code
```

#!/bin/sh

echo 

echo "Enter the directory that you want to destroy:"
read directory

echo "Enter the number of times you want the file overwritten (I recommend 10):"
read overwrite

echo
echo -n     "You are about to permanently delete $directory and overwrite it $overwrite time(s).

            Do you want to proceed (Y/N)?"
read answer
if test "$answer" != "Y" -a "$answer" != "y";
then exit 0;
fi

gnome-terminal -x bash -c "shred -n $overwrite -z $directory"
gnome-terminal -x bash -c "rm -rf $directory"

```
Use the "find" command with the "-exec" option. Basically "find" searches trees for files matching some criteria (name, type, size, age, etc...) and its "-exec" option lets you specify a command to be run against each file found (which is represented by "{}"). The end of the command is indicated by ";" which is usually escaped as "\;" so that bash doesn't confuse it for its own statement separator. This gives:

```
find $directory -type f -exec shred -n $times {} \;
```

---

### Post by Paddy Landau on 2011-09-22
Whenever you use variables, be sure to surround them with quotes in case they contain spaces.

For example, instead of
[FONT=Fixedsys]-z $directory[/FONT]
use
[FONT=Fixedsys]-z "${directory}"[/FONT]

Such habits will pay in the long run.

To list then delete a file, use the *find* command.
[FONT=Fixedsys]find "${directory}" -print -delete[/FONT]

If you specifically want to shred it, you can use the -exec option.
```
find "${directory}" -print -exec shred -n ${overwrite} -z {} + # Shred all files recursively while printing them.
find "${directory}" -delete # Delete the files.
shred -n ${overwrite} -z "${directory}" # Shred the directory.
rm -rf "${directory}" # Delete the directory
```*Be sure to test it in a test directory before putting it live!*

---

### Post by shibby4555 on 2011-09-22
> **ofnuts said:**
> Use the "find" command with the "-exec" option. Basically "find" searches trees for files matching some criteria (name, type, size, age, etc...) and its "-exec" option lets you specify a command to be run against each file found (which is represented by "{}"). The end of the command is indicated by ";" which is usually escaped as "\;" so that bash doesn't confuse it for its own statement separator. This gives:

```
find $directory -type f -exec shred -n $times {} \;
```


That did it. Thanks so much for the help as well as the explanation. I feel pretty proud of myself as this is one of the first shell scripts I've written. Baby steps....

---

### Post by Habitual on 2011-09-23
> **shibby4555 said:**
> ...but i can't figure how to go about listing out each file within a folder then auto deleting it.

```
for i in $(ls -1 /path/to/dir) ; do rm -fr $i ; done
```

---

### Post by Vaphell on 2011-09-23
bad advice, spaces will destroy your approach. Ls is not to be used to iterate over files

```
for i in /path/to/dir/*; do whatever "$i"; done
```

---

### Post by alquery on 2011-09-23
Oh yeah, and in future posts, you should probably use the programming section of the forum so more experts on scripting can find your issue. Also, marking your thread as solved would be nice.

---

### Post by sisco311 on 2011-09-24
> **Vaphell said:**
> bad advice, spaces will destroy your approach. Ls is not to be used to iterate over files

+1

@Habitual

See BashPitfalls #1 (link in my signature) and [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

### Post by Paddy Landau on 2011-09-24
> **sisco311 said:**
> See BashPitfalls #1 (link in my signature) and [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)
+1. I have read those pages before, and they are most instructional.

---

