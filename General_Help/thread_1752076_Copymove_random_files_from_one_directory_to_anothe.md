---
title: "Copy/move random files from one directory to another"
date: 2011-05-07
forum: General Help
---

### Post by EgoGratis on 2011-05-07
We have two folders: source folder and destination folder. In source folder we have many sub folders and many files of different type!

Task: Script that would copy or move defined number of files from source to destination folder. Files must be selected randomly and sub folder in source folders must be selected randomly and we don't copy or move defined number of files just form one sub folder in source folder. In destination folder sub directory structure of source folder should not be preserved. Solution should be robust and as simple as possible.

---

### Post by r-senior on 2011-05-07
Is this a homework assignment, or does it have a practical application? I'm struggling to think of the latter.

Does it have to be a script, or can it be a program?

---

### Post by Perfect Storm on 2011-05-07
Homework assignment are not allowed on UF. Thread closed.

---

### Post by bapoumba on 2011-05-07
Reopened [http://ubuntuforums.org/showthread.php?p=10784162](http://ubuntuforums.org/showthread.php?p=10784162)
Please answer the questions in post #2, thanks.

---

### Post by EgoGratis on 2011-05-07
> **r-senior said:**
> Is this a homework assignment, or does it have a practical application? I'm struggling to think of the latter.

Does it have to be a script, or can it be a program?

I opened this thread for the fun of it. It was written like "homework assignment" on purpose but i didn't know i was that good of an professor. ;) If this "problem" can not be "solved" with few bash lines nobody should put an effort in it! It is not "critical" to find a solution for this thread topic but it would be nice if it can be done with simple bash script.

-Two folders, one full of files and folders and another one empty
-Bash script (simple)

Bash script copies/moves preconfigured number of randomly selected files from folder one to folder two. Files are selected randomly in all sub folders but when copied/moved folder structure is lost and are all copied/moved to the same folder!

---

### Post by EgoGratis on 2011-05-07
Let say u have 1000 files in one folder (and sub folders). This files must be reviewed (and moved elsewhere) and u have 10 people working on it. You want 10 files to be reviewed by one person in one day. This script would move 10 randomly selected  files to each person every day. If it can be done in bash with few lines OK if not forget about it! And to make things more simple forget about 10 persons and say it is for one person only and forget about "cron" and focus just on move/copy part.

---

### Post by kaibob on 2011-05-07
I think this will do what you want. The find commands finds all files in the source directory and subdirectories. The sort command randomizes the list of files. The mapfile command creates an array of the first five of the randomized files (you can change the 5 to whatever number you want). I used the backup option with the copy command just in case there are any duplicate files copied. 

```
#!/bin/bash

mapfile -t -n 5 files < <(find /source -type f | sort -R)

cp --backup=numbered "${files[@]}" /target
```

---

### Post by EgoGratis on 2011-05-07
> I used the backup option with the copy command just in case there are any duplicate files copied.

Didn't think of that. The files could have the same name yes. I will try your suggestion tomorrow. Thanks!

---

### Post by AlphaLexman on 2011-05-07
> **EgoGratis said:**
> I didn't know i was that good of an professor. If this "problem" can not be "solved" with few bash lines nobody should put an effort in it!
A **good** professor would know the difference between [COLOR=Red]an professor[/COLOR] and [COLOR=Blue]a professor[/COLOR], a **better** professor would already know this would require more than a **few** (+ 3 to 4) lines of code.

That being said, **I** would start with a read command to get the number of random files to copy, then use find to get a full recursive list of files, then knowing that bash does NOT have any built-in random generator, I would have to use another program, maybe awk's 'rand' to generate random values, but I would still have to equate random values to filenames, all before I could separate current directories and sub-directories, and then copy all randomly generated files to one common directory, and I still haven't tested for unique filenames, should I overwrite or skip?

Probably more than a **FEW** lines of code, so I won't put an effort in it...

EDIT: kaibob may have proved me wrong :-(

---

### Post by EgoGratis on 2011-05-08
> A good professor would know the difference between an professor and a professorBut still i managed to pull it off. Didn't I? Everybody thought it was homework assignment just like an professor would give it to his students! ;)

@kaibob

You are an professor. It works. Here is how i did it in the end. For duplicate files i didn't bother with Bash scripting or making backups. There are some tools available for this job like FSlint, fdupes, rmlint... I just went and installed FSlint from Ubuntu Software Center. It has a nice GUI and command line tools. I use fslint-gui on /source directory to find duplicate files (checksum). In the end i run this command:

/usr/share/fslint/fslint/findsn /source

To find files that are not duplicates, but have the same name. I don't know if it is possible to enable "same name" option in fslint-gui too!

Then the second part. I realised that moving and not copying files is much better option. So i modified your scrip a bit:

```
#!/bin/bash 
mapfile -t -n 5 files < <(find /source -type f | sort -R) 
mv "${files[@]}" /target

```I tested this many times with different number and it works just like it should! It moves randomly selected files from source directory (and sub directories) to destination directory not preserving directory structure. This is the solution i was looking for. A few lines in bash that do the job right!

Thanks for your solution!

P.S. Could you or somebody else explain in words:

```
mapfile -t -n 5 files

"${files[@]}"

```I can't find manual (man mapfile) and list of parameters!

---

### Post by matt_symes on 2011-05-08
Hi

It is a lovely solution. Very succinct.

```
P.S. Could you or somebody else explain in words:

Code:
mapfile -t -n 5 files

"${files[@]}"
I can't find manual (man mapfile) and list of parameters!
```

mapfile will map input from stdin into an array.

In this case files is the name of the array. -n 5 is the number of elements to map into the array before stopping and -t removes any trailing new lines from the input.

```
< <(find /source -type f | sort -R)
```

So the above line will perform a find of files (the -f flag) in the directory and sub directories of /source. It will sort them randomly.
This all happens in a sub shell. The output of that is redirected into the input of the mapfile command.

```
mapfile -t -n 5 files < <(find /source -type f | sort -R)
```

As stated, the line above will populate the array called files with the first 5 items from the redirected input of the find and sort commands after removing any trailing new lines.

"${files[X]}"

Above is the syntax to access elements in an array in bash, where X is replaced by a value.

"${files[0]}" will access element 0.
"${files[1]}" will access element 1 and so on.

@ is a special value when it comes to arrays. It means all the elements of the array. So in this case it can be translated as

```
mv "${files[0]}" "${files[1]}" "${files[2]}" "${files[3]}" "${files[5]}" /target
```

"${files[0]}"

Above the command is quoted so bash will not split files containing white space. 

I.E. a file name 'hello world.jpg' will be interpreted as one file called 'hello world.jpg' and not two files, one called 'hello' and the second one called 'world.jpg'
 
I hope this helps. If you want to read up about bash programming have a look at the two links at the bottom of my sig.

Kind regards

---

### Post by EgoGratis on 2011-05-08
Thank you for your excellent explanation!

Just one more question. If i run this scrip with cron i get this error:

> syntax error near unexpected token `<'

I tried a few things but didn't manage to find a solution. Any suggestions for this?

---

### Post by matt_symes on 2011-05-08
Hi

Can i have a look at your exact script ?

Can i also have a look at your crontab entry ?

Kind regards

---

### Post by EgoGratis on 2011-05-08
Actually after some additional tests it looks like the script does works with cron!

```
#!/bin/bash
mapfile -t -n 5 files < <(find /source -type f | sort -R) 
mv "${files[@]}" /target
```This is what happened. I use gnome-schedule to set up cron tasks and after setting up the task i decided it was the time to test it. In gnome-schedule i selected the task and clicked on Run selected task. It opened up the terminal and there was the mentioned "error message". BUT i didn't noticed that when i press enter terminal closes and task is successfully finished. Then i just left cron to do the task and it was done successfully. There are no errors in syslog.

So probably everything is OK?  Thanks to everybody for helping me to get this to work!

---

