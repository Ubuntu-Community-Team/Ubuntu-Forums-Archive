---
title: "Shell Script Involving Archives"
date: 2012-04-25
forum: General Help
---

### Post by rhss6-2011 on 2012-04-25
Hello there,
I am working on a shell script that will enable me to:

1. Create various types of archives
2. Extract Various types of archives
3. Move various types of files

----------------------------------------
This script I am trying to build is supposed to use core utilities so that even in Ubuntu 9.04 I could use it without installing any additional packages...

***_Functions that don't work will be bold:_***
```
#!/bin/bash
# Command to execute is as follows
#Enter directory with this script, then
#sh extract.sh /DIRECTORY/WITH/ALL/FOLDERS/CONTAINING/RAR/FILES/
#DO NOT FORGET THE LAST SLASH
#For numbers 4-6 you need to edit the path to your own preferred directory...

if [ $# -ne 1 ]
then
  echo "You forgot to enter directory where i should work!"
  exit
fi

while 
mesg="\n==============================================\n
  01.. Check .sfv files.\n
  02.. Unrar all rar files.\n
  03.. Delete rar and sfv files.\n
[B]  04.. Extract TAR files.\n
  05.. Extract TAR.GZ files.\n[/B]
  06.. Gunzip ZIP files.\n
  07.. Move AVI files to your location.\n
  08.. Move MP4 files to your location.\n
  09.. Move MKV files to your location.\n
  10.. Exit
  \n==============================================\n
Select: \c"
do
  echo -e $mesg
  read selection
  case $selection in
  01)
    cd $1
    cfv -r ;;
  02)
    for r in `find $1 -wholename *.rar`
    do
      echo "Unpacking in directory: "`dirname $r`
      unrar e -v $r `dirname $r`
    done ;;
  03)
    for g in `find $1 -wholename *.r01`
    do 
      cd `dirname $g`
      echo "Deleting in directory: "`dirname $g`
      rm *.r?? *.url *.sfv imdb.nfo
      rm -r Sample/
    done ;;
[B]  04)
    for f in `find $1 -wholename *.tar`
    do
      echo "Unpacking in directory: "`dirname $f`
      tar -xvf $f `dirname $f`
    done ;;
  05)
    for f in `find $1 -wholename *.tar.gz`
    do
      echo "Unpacking in directory: "`dirname $f`
      find $1/ -name "*.tar.gz"
      tar -xvf $f
    done ;;[/B]
  06)
    for z in `find $1 -wholename *.zip`
    do
      echo "Unpacking in directory: "`dirname $z`
      gunzip -d -v -r $z `dirname $z`
    done ;;
  07)
      for f in `find $1 -wholename *.avi`
    do
      echo "Moving AVI files from: `dirname $f` to /home/masterchief/MOVETESTING"
      find $1/ -name "*.avi"
      mv $f /home/masterchief/MOVETESTING
    done ;;
  08)
      for f in `find $1 -wholename *.mp4`
    do
      echo "Moving MP4 files from: `dirname $f` to /home/masterchief/MOVETESTING"
      find $1/ -name "*.mp4"
      mv $f /home/masterchief/MOVETESTING
    done ;;
  09)
      for f in `find $1 -wholename *.mkv`
    do
      echo "Moving MKV files from: `dirname $f` to /home/masterchief/MOVETESTING"
      find $1/ -name "*.mkv"
      mv $f /home/masterchief/MOVETESTING
    done ;;
  10) 
    exit;;
  esac
done
```

Can anyone help me there? This is my first real script, and it's driving me crazy. I think that the bold section(s) contain key elements for me to expand on my script the way I am hoping... I basically took bits and pieces from other scripts, and commands to get it together.
I can move the files (it searches in sub-directories and moves them even from there) and the RAR functions all seem to work properly - I haven't tried the GUNZIP function yet, but it should...
If possible could someone take the script and test it? The main focus is intended for a Folder with (MANY) sub-directories... The script is supposed to look through all of them, and find the files. Depending on the script option it's supposed to execute the commands - so far the _**TAR functions are not**_ working...


I am using gnome-terminal and Gedit for this script. To easily read the functions of the script I am using the Gedit cobalt theme -- for example tar turns orange, echo green etc. so it is more easily read...

---

### Post by strask on 2012-04-25
Welcome to the world of shell scripting!

First... if you have to put a comment at the top of the script reminding people to put a / at the end of the directory name, then someone WILL forget to put a / at the end of the directory name. Plan and code for this accordingly. For example:```
folder="`dirname $1`/`basename $1`/"
```

Now, for your tar problem:```
  04)
    # we will need this soon:
    prevdir=`pwd`
    for f in `find $1 -wholename *.tar`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -xvf `basename $f`
      # then go back to the dir we were in to start with.
      cd $prevdir
    done ;;
 
```

Do the tar.gz case exactly like the .tar, except make it ```
tar -xvzf `basename $f`
```

Bonus questions:

1) How can you avoid writing so much duplicate code for the tar and tar.gz cases?

2) What happens if one of the tar file names contains spaces? How can you avoid this problem?

Have fun!

---

### Post by rhss6-2011 on 2012-04-25
```
# we will need this soon:
    ***prevdir=`pwd`***
    for f in `find $1 -wholename *.tar`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -xvf `basename $f`
      # then go back to the dir we were in to start with.
     *** cd $prevdir***
    done ;;

```
So with ***prevdir=`pwd`*** -- What/where is that? I assume it's like "previous directory=" but with the given name of ***"pwd"*** does that mean it looks for that folder name..?
------
Also, Let's say that main folder has 3 sub-folders all of which contain tar.gz files... Wouldn't that create an error, since even in the terminal you can't be in 3 places at one - Because using my example, the terminal would go into those folders using "cd" and extract the files and move back...
... But with multiple sub-folders would that still work?



As I mentioned, this is m very first script so it's sort of going over my head, but in answer to:
> 1) How can you avoid writing so much duplicate code for the tar and tar.gz cases?
It would be ***for f in `find $1 -wholename *.tar.*`*** correct?
Only problem I see, would be if it were a **tar.bz2** file in which case the proper tar command would be **tar -jxvf** correct..?

Now, for your second question I have no idea. I know that in the terminal you can enter a directory that has spaces with;
**cd /foldername\ with\ space/wherever\ it/is** since I have had to use that before, but I have never tried it with a file...

---

### Post by strask on 2012-04-25
> **rhss6-2011 said:**
> So with ***prevdir=`pwd`*** -- What/where is that? I assume it's like "previous directory=" but with the given name of ***"pwd"*** does that mean it looks for that folder name..?

'pwd' is a command -- _**P**_rint _**W**_orking _**D**_irectory. It prints the name of the directory you are currently in.
Any time you have a plain word IMMEDIATELY followed by a =, no spaces, it is a variable assignment. The word to the left of the = is the name of the variable, and on the right is the value to store in that variable.

So what we are doing is storing the current working directory in the variable named prevdir, which we access by putting a $ in front of it later on.

> Also, Let's say that main folder has 3 sub-folders all of which contain tar.gz files... Wouldn't that create an error, since even in the terminal you can't be in 3 places at one - Because using my example, the terminal would go into those folders using "cd" and extract the files and move back...
... But with multiple sub-folders would that still work?0) We store the current working directory in prevdir.
1) The find command finds all the files matching your criteria.
2) The for loop puts these file names in the $f variable, one at a time.
3) For each $f, we cd into the appropriate directory.
4) We extract the tar.
5) We cd back to the previous working directory.
6) Go back to step 3 until we use up all the file names.

It never needs to be in two places at once.

> As I mentioned, this is m very first script so it's sort of going over my head, but in answer to:
[QUOTE]1) How can you avoid writing so much duplicate code for the tar and tar.gz cases?It would be ***for f in `find $1 -wholename *.tar.*`*** correct?[/QUOTE]Well, I was thinking more along the lines of writing a shell function that does the find and the cd and the tar (optionally with the z) and the cd back, and then call that function from both the tar and tar.gz areas. 

> Only problem I see, would be if it were a **tar.bz2** file in which case the proper tar command would be **tar -jxvf** correct..?Good catch, that's the kind of variable you always need to watch out for. Wildcards can catch more than you expect. :)

> Now, for your second question I have no idea. I know that in the terminal you can enter a directory that has spaces with;
**cd /foldername\ with\ space/wherever\ it/is** since I have had to use that before, but I have never tried it with a file...You can also do it with quotes, like ```
cd "/foldername with space/wherever it/is"
```so in our tar code, you could wrap the variable in quotes to protect the spaces if they exist:```
tar -xvf "`basename $f`"
```There are probably a lot of places in your code where you could use quotes to improve safety in the case of space-infested filenames. :)

---

### Post by rhss6-2011 on 2012-04-27
Thanks a lot guys! I really needed the help on that :KS

---

