---
title: "mass zip conversion help"
date: 2006-02-02
forum: General Help
---

### Post by chronusdark on 2006-02-02
i have a bunch of 7z files from my days on windows and since i converted to linux i wanted to convert them to zip since zip is better integrated with linux than 7z so i was wanting someon with good bash scripting skills to hook me up with a script that will convert all my .7z files to regular old .zip


i would do it but im not that good at bash scripting yet lol

thanks in advance

---

### Post by chronusdark on 2006-02-02
oh and by a bunch i mean 1031 and each archive contains about 1-10 files

---

### Post by johnnymo87 on 2006-02-02
You could email a .zip company, like winzip. I know some of the guys there, and I know they're pretty knowledgable with Linux.

Here's their e-mail.
[email]help@winzip.com[/email]

---

### Post by chronusdark on 2006-02-02
somehow i dont think they would be allowed to help me when dealing with a competitors zip format  
i just need a script/program to extract all my .7z files individually then recompress them with the regular old zip format

---

### Post by ximok on 2006-02-03
Eat your heart out...
Here is how it works.  You run this script from the directory where all your 7z files are.  You specify a second directory where you want the zips to end up.

So, if you want to put all your resulting zips into /tmp/BigFolderOZips/
type conv7z2zip  /tmp/BigFolderOZips/
(I'm assuming you save it as conv7z2zip)

NOTE: You have to create this folder and your temporary folder FIRST!

```

#!/bin/bash
## This monster will convert the .7z files to .zip and place them in
##   the destination directory of your choice
## Made by Ximok  - Say thank you ;)


## This is the directory (absolute) where all your files will be converted at
tempdir=/tmp/7zconvert/


## It's not recommended to change much after this
stnderr=" Syntax: $0 destination"
if [[ ! -d $tempdir ]]; then
     echo $stnderr
     echo " Whoa! Make sure your temp directory exists first!"
     echo " Does $tempdir exist?"
     echo " Maybe try mkdir $tempdir    or pick a different tempdir"
     exit 1
fi
if [[ ! -w $tempdir ]]; then
     echo $stnderr
     echo " Whoa! Make sure you have write permissions first!"
     echo " Do you have write permissions to $tempdir ???"
     exit  1
fi
curdir=`pwd`
cd $tempdir
tempdir=`pwd`
echo $tempdir
cd $curdir

destination=$1
if [[ "$destination" == "" ]]; then
     echo $stnderr
     echo; echo " Danger Will Robinson! Danger!"
     echo " You must provide a destination folder for your files"
     echo " We recommend ~/zipdone as a solution"
     echo " So, go type mkdir $destination or mkdir ~/zipdone"
     exit 2
fi

if [[ "$destination" == "$curdir" ]]; then
     echo $stnderr
     echo; echo " Danger Will Robinson! Danger!"
     echo " It is not advisable to use the same directory"
     echo " for both your 7z files and your zip files"
     exit 3
fi
if [[ ! -w $destination ]]; then
     echo $stnderr
     echo " Whoa! Make sure you have write permissions first!"
     echo " Do you have write permissions to $destination ???"
     exit  3
fi


cd $destination
destination=`pwd`
cd $curdir

count=0

for  file in `ls -1 *.7z`; do

     echo "Working on $file"

     cd $curdir

     7z x -o$tempdir $file

     zipfile=`echo $file|awk -F.7z '{ print $1 }'`

     cd $tempdir

     zip -r9 $destination/$zipfile ./

     rm -Rf *

     count=$(($count + 1 ))

done


echo;echo;echo
echo "Done!!!!"

echo Processed $count files




```

---

### Post by ximok on 2006-02-03
BTW, why not use Gzip or Bzip2?  They do a LOT better job than good old fashioned zip.

---

### Post by ximok on 2006-02-03
I just realized.  Make sure you have NO SPACES in your filenames
shell scripts and files with spaces don't get along too well.

If you run this script in a folder, it will convert all spaces to _

Forgive me, I wrote this script 3 or so years ago and it is completely redundant and not very efficient, but it gets the job done.

The reason for the 20 cycles is so you don't end up with something like smith__,_jon instead of smith,jon.


```

#!/bin/bash
a=0

while [ $a -lt 20 ]
do
  a=`expr $a + 1`
  rename \  _ *
  rename _-_ - *
  rename -_ - *
  rename _- - *
  rename __ _ *
  rename _,_ , *
  rename -,- , *
  rename -- - *
  rename .. . *

done
##The loop makes it so freaking redundant, but effective.




```

---

### Post by chronusdark on 2006-02-04
[QUOTE=ximok]BTW, why not use Gzip or Bzip2?  They do a LOT better job than good old fashioned zip.[/QUOTE]

if you must know they are Roms 

and thanks for the scripts gonna try it now thanks alot

---

### Post by chronusdark on 2006-02-04
your second script keeps giving me errors

```
Bareword "_" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "_" not allowed while "strict subs" in use at (eval 1) line 1.
Unknown option: _
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
syntax error at (eval 1) line 2, at EOF
```

---

### Post by ximok on 2006-02-07
I'm going to assume you cut and pasted the code... 

hrmm...  Try this: just type 

```

 rename \  _ *

```

Take note: there are TWO spaces after the \  (Pretend that the # represents a space)
```

rename#\##_#*

```

So, in the second example, you would just take the # and replace with a space.   Just running that command will take care of all the spaces (but it won't be as pretty as it could be)

---

