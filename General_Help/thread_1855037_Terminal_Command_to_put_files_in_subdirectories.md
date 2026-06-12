---
title: "Terminal Command to put files in subdirectories"
date: 2011-10-05
forum: General Help
---

### Post by monsieurdozier on 2011-10-05
I ran foremost on one of my external hard drives, and now have a folder that is filled with pictures.  I'm trying to sort through them, but the sheer number is bogging down the file manager.

So what I'm looking for is a terminal command or script I can run that will automatically split all of these files into multiple subdirectories.  I don't care about what order they are in, and I would like to keep under 200 files a folder.  Any ideas?

---

### Post by spiky001 on 2011-10-05
I found this any help [http://www.unix.com/shell-programming-scripting/131199-shell-script-arrange-files-into-several-folders.html](http://www.unix.com/shell-programming-scripting/131199-shell-script-arrange-files-into-several-folders.html)

---

### Post by TeoBigusGeekus on 2011-10-05
I've come up with this
```
#!/bin/bash
pics_no=$(ls | wc -l)
dir_no=$(($pics_no/200))
for (( i=1; i<=dir_no; i++ ))
  do
   dir_name=$(date)
   mkdir "$dir_name"
   for (( j=1; j<=200; j++ ))
    do  
       mv "$(find ./ -maxdepth 1 -type f ! -name "*script*"|head -n1)" "$dir_name"
    done   
   sleep 1
  done

```
Save it as script in the folder with the images, make it executable
```
chmod +x /path/script
```
and run it
```
bash /path/script
```

---

### Post by seawolf167 on 2011-10-05
Question for TeoBigusGeekus:

In your script you have the directories being created with the name being the date from

```
dir_name=$(date)
```Since the date output only displayed down to the number of seconds, i.e.

```
Wed Oct  5 13:18:58 CDT 2011
```will the script run fast enough to create (or attempt to create) multiple folders of the same name?

EDIT: didn't see the 

```
sleep 1
``` at the end of the loop, nevermind then!

---

### Post by monsieurdozier on 2011-10-05
Would it solve the issue to replace the line with:
> dir_name=$i
Thus making the names of the directories sequential numbers?

Or does the sleep 1 prevent the folder double naming from happening?

Edit:

TeoBigusGeekus,

I tried the script and it worked well.  There's a small bug that's easy enough to fix for anyone who uses this script later.  On this line:
> dir_no=$(($pics_no/200))
When the division happens, if there is not an even multiple of 200, the remainder is rounded off and are left in the main folder without having a subfolder created, i.e.: 415 files would make 2 directories and 15 files left in original folder.

I'm not a bash scripter, so I don't want to offer a fix and be wrong.

Otherwise, script worked great.  Thanks.

Off topic: It's also really hard to trust someone with a Troll Face in their avatar. ;-)

---

### Post by TeoBigusGeekus on 2011-10-05
> **monsieurdozier said:**
> 
When the division happens, if there is not an even multiple of 200, the remainder is rounded off and are left in the main folder without having a subfolder created, i.e.: 415 files would make 2 directories and 15 files left in original folder.
Pretty much this. The division is truncated, so the result is subfolders with 200 files in them and the remainder in the base folder.

> **monsieurdozier said:**
> 
Off topic: It's also really hard to trust someone with a Troll Face in their avatar. ;-)

Problem?

---

### Post by WorMzy on 2011-10-05
Put your trust in the fact that s/he has nearly 5000 posts and isn't banned yet. :P

---

### Post by TeoBigusGeekus on 2011-10-05
I'll be banned at 6666 posts. :twisted:

PS: I'm a he mate! Haven't you read all my sexist posts?

---

