---
title: "finding and moving files into new subfolder within its current location"
date: 2011-09-23
forum: General Help
---

### Post by sooky on 2011-09-23
I'm new to linux.. (3 days) 

I have about 60,000 vehicle images I need to search through and sort into newly created sub folders for inertior (/int) and exterior (/ext)in the same directory the images were found.

My file structure looks something like this

/mu/assets/vehicles/acura/2011/6056/*.png
/mu/assets/vehicles/honda/2011/3345/*.png

images angles are numbered so that all exterior shots end in 090.png, 037.png, etc

I have tried the following

$ sudo find assets -maxdepth 6 \( -name "*090.png" -o -name "*037.png" -o -name "*038.png" -o -name "*041.png" \) -type f -execdir mv {} /ext \;

but nothing happens, no errors just a return to the prompt..

I need help..

---

### Post by ScottSanbar on 2011-09-23
Here is one solution.  Just adjust the find commands and mv.scr script to your needs:

**************************************************************************************************

Script started on Fri 23 Sep 2011 12:16:25 AM CDT

scott@scotts2ub:$ls -al
total 64

drwxr-xr-x  4 scott scott  4096 2011-09-23 00:16 0m01;34m .
drwxr-xr-x 47 scott scott  4096 2011-09-23 00:15 01;34m ..
--rwxr--r--  1 scott scott    58 2011-09-23 00:10 01;32m mv.scr
-rw-r--r--  1 scott scott     1 2011-09-22 23:59 test1
-rw-r--r--  1 scott scott     1 2011-09-22 23:59 test2
-rw-r--r--  1 scott scott     1 2011-09-22 23:59 test3
drwxr-xr-x  2 scott scott  4096 2011-09-23 00:15 01;34m testdir

scott@scotts2ub:$ ls -al testdir
total 8
drwxr-xr-x 2 scott scott 4096 2011-09-23 00:15 0m01;34m .
drwxr-xr-x 4 scott scott 4096 2011-09-23 00:16 01;34m ..

scott@scotts2ub:$ find . -name "*1" -type f > mv.data
scott@scotts2ub:$ find . -name "*2" -type f >> mv.data
scott@scotts2ub:$ find . -name "*3" -type f >> mv.data

scott@scotts2ub:$ cat mv.data
./test1
./test2
./test3

scott@scotts2ub$ cat mv.scr
#!/bin/bash
#
while read LINE; do
  cp $LINE testdir
done

scott@scotts2ub:$ ./mv.scr < mv.data

scott@scotts2ub:$ ls -al testdir
total 20
drwxr-xr-x 2 scott scott 4096 2011-09-23 00:17 0m01;34m .
drwxr-xr-x 4 scott scott 4096 2011-09-23 00:17 01;34m ..
-rw-r--r-- 1 scott scott    1 2011-09-23 00:17 test1
-rw-r--r-- 1 scott scott    1 2011-09-23 00:17 test2
-rw-r--r-- 1 scott scott    1 2011-09-23 00:17 test3

scott@scotts2ub:$ exit

Script done on Fri 23 Sep 2011 12:18:02 AM CDT

***********************************************************************************

---

### Post by papibe on 2011-09-23
Welcome to the forums!

First, I recommend that you backup your data before running any script. Specially if running as root, since the potential damages of a mistake on the script could be greatly increased.

I think this is the problem with your command:
```
mv {} /ext \;
```
You are coping what you found in a file called ext under the root directory. Next time you 'find' finds a file, it will overwrite the file on the same place (thus losing your data!).

Assuming that the subdirectory ext actually exists under every location needed, a simple fix would be:
```
mv -v '{}' ./ext/ \;
```
-v will print a message every time a file is moved.
./ext/ is a relative path (from where the file is found).

I hope it helps,
Regards.

---

### Post by sooky on 2011-09-23
thanks pap I'll try that. How would I create the folders needed while moving?

---

### Post by patryk77 on 2011-09-23
Read the mkdir man page:
man mkdir

Basically what you want would be:
mkdir -p path

The -p option tells it to create it and not spit out an error if it exists

---

### Post by papibe on 2011-09-23
> **sooky said:**
> How would I create the folders needed while moving?
The simplest way I can think of is modify what you have. Since you already 'know' how to find the places that needs the subdirectories, just change the execdir part for something like this:
```
-execdir mkdir -p ./ext \;
```
I hope it helps,
Regards.

---

### Post by nothingspecial on 2011-09-24
If I have understood you correctly,

Assuming that there are 3 levels of directories make/year/number

and all the png files are in the nimber folder.

Assuming that all files ending ,for example, 21.png and 22.png are interiors


```

for f in */*/*; do mkdir "$f"/int; mv "$f"/*{21,22}.png "$f"/int; done
```

Then do the same for the exteriors, changing the 21 and 22 for the right numbers and both instances of int to ext

Make sure, before you run this that it is going to do what you want it to do. If you don't understand or have any questions post back before you run it.

I assume you do have a back up. :D

---

