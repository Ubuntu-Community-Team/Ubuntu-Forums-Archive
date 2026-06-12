---
title: "From bat to sh"
date: 2011-09-28
forum: General Help
---

### Post by dragonbook on 2011-09-28
Hi

 As a former Windows user, I have a number of bat files I use to perform various tasks. I've tried to use these bat files through wine but it does not work as intended.

 Instead of trying to get them to work in wine, I would much rather try to learn to make a Sh file, but I have absolutely no knowledge of these.

 Is there a friendly person who will try to translate one of my simple bat files to a sh file? That way I can see what the difference is between the two and thereby hopefully translate the others I have.

 Here is the script:

```
@echo off

::--------------------------------------------------------------------------
:: Find images
::--------------------------------------------------------------------------

for /f %%f in ('dir Orginale\*.jpg /b /a:-d-s-h') do call :Thumb "%%f"

echo Finished

pause
goto :EOF

::--------------------------------------------------------------------------
:: Thumb
::--------------------------------------------------------------------------
:Thumb
set dest_file=%1
echo converting %1 to %dest_file%
nconvert -npcd 2 -size 256x256+0 -ctype grey -corder inter -out jpeg -o Thumb/thumb_%1 -ratio -rtype lanczos -rflag decr -resize 0 100 -bgcolor 144 162 133 -canvas 100 100 center Orginale/%1
goto :EOF
``` I use the program nconverter from: [http://www.xnview.com/en/download_nc.html](http://www.xnview.com/en/download_nc.html)

 I would greatly appreciate all the help I can get.

---

### Post by coldraven on 2011-09-28
Sorry but I'm not an expert at bash but here's what I know.
Create a new text file with gedit.
The first line should look like this
```
#! /bin/bash
```
That tells the system to execute the following commands with bash.
Then add a command to send your jpgs through ImageMagic.
Save the file as convert_my_pics (no need for a file extension)
Right click on the file and check "Make executable"

[http://www.imagemagick.org/script/command-line-options.php](http://www.imagemagick.org/script/command-line-options.php)

[URL="http://www.gnu.org/s/bash/manual/bash.html"]http://www.gnu.org/s/bash/manual/bash.html
[/URL]
Or install Phatch from the software centre, it has a nice GUI

"Phatch handles all popular image formats and can duplicate (sub)folder
hierarchies. It can batch resize, rotate, apply perspective, shadows, rounded
corners, ... and more in minutes instead of hours or days if you do it
manually. Phatch allows you to use EXIF and IPTC tags for renaming and data
stamping."

---

### Post by sisco311 on 2011-09-28
Check out the links in my signature.


I don't know much about .bat files, but I think you want something like:
```
#!/bin/bash

# change current working directory where the Orginale dir is located 
# or exit if it doesn't exist
cd **path/to/dir** || exit 1
# create the Thumb directory if it doesn't exist
mkdir -p Thumb

shopt -s nullglob

# for each .jpg file in Orginale do
for file in Orginale/*.jpg
do
    # strip directory name and assign the value to filename  
    filename="${file##*/}"
    nconvert  -npcd 2 -size 256x256+0 -ctype grey -corder inter -out jpeg -o "Thumb/thumb_$filename" -ratio -rtype lanczos -rflag decr -resize 0 100 -bgcolor 144 162 133 -canvas 100 100 center "$file"
done

```

---

### Post by dragonbook on 2011-09-28
> **sisco311 said:**
> Check out the links in my signature.


I don't know much about .bat files, but I think you want something like:
```
#!/bin/bash

# change current working directory where the Orginale dir is located 
# or exit if it doesn't exist
cd **path/to/dir** || exit 1
# create the Thumb directory if it doesn't exist
mkdir -p Thumb

shopt -s nullglob

# for each .jpg file in Orginale do
for file in Orginale/*.jpg
do
    # strip directory name and assign the value to filename  
    filename="${file##*/}"
    nconvert  -npcd 2 -size 256x256+0 -ctype grey -corder inter -out jpeg -o "Thumb/thumb_$filename" -ratio -rtype lanczos -rflag decr -resize 0 100 -bgcolor 144 162 133 -canvas 100 100 center "$file"
done

```

I've saved the above as a sh file and saved it in the same folder as the program nconvert and the folders original and thumb.

 But when I double click the file nothing happens. I have also phasing it directly in the terminal, but it just shuts down.

 Any ideas about what is going wrong?

---

### Post by sisco311 on 2011-09-28
If you run it from the directory where original and thumbs are, then you don't have to change the current working directory. Also, Linux is case sensitive: Original and original are different files.

---

### Post by dragonbook on 2011-09-28
> **sisco311 said:**
> If you run it from the directory where original and thumbs are, then you don't have to change the current working directory. Also, Linux is case sensitive: Original and original are different files.

Okay I obviously doing something wrong, I've tried to run:

```
#!/bin/bash

# create the Thumb directory if it doesn't exist
mkdir -p Thumb

done
``` It makes no directory.

 Is it possible to somehow get the terminal to write what it does?

---

### Post by 23dornot23d on 2011-09-28
Make sure that it is executable ..... it worked for me .....

Two ways either in properties >>> permissions ....

or chmod u+x (file.sh)

in the case below

chmod u+x createThumb.sh

to run it >>>

./createThumb.sh

or double click it .... in the folder view

[IMG]http://img849.imageshack.us/img849/5426/thumbasu.jpg[/IMG]


actually remove [COLOR=Red]**done**[/COLOR] ..... 

keith@keith-MS-7181:~$ cd Thumb
keith@keith-MS-7181:~/Thumb$ ./createThumb.sh
./createThumb.sh: line 6: syntax error near unexpected token `done'
./createThumb.sh: line 6: `done'
keith@keith-MS-7181:~/Thumb$ ./createThumb.sh


it works but dreates a syntax error as it is now ......

```

#!/bin/bash  
# create the Thumb directory if it doesn't exist 

mkdir -p Thumb

```

---

### Post by dragonbook on 2011-09-28
> **23dornot23d said:**
> 
to run it >>>

./createThumb.sh

or double click it .... in the folder view



The double click doesn't work here.

I had to write:
sudo bash createThumb.sh ???

Now I have the folder :-)

Then I try to run:
```
#!/bin/bash 
# 
# create the Thumb directory if it doesn't exist 
mkdir -p Thumb 
# 
shopt -s nullglob 
# 
# for each .jpg file in Orginale do 
for file in Orginale/*.jpg 
do 
    # strip directory name and assign the value to filename   
    filename="${file##*/}" 
    nconvert  -npcd 2 -size 256x256+0 -ctype grey -corder inter -out jpeg -o "Thumb/thumb_$filename" -ratio -rtype lanczos -rflag decr -resize 0 100 -bgcolor 144 162 133 -canvas 100 100 center "$file" 
done
```

But gets this error:
```
: invalid shell option namelglob
test.sh: line 10: syntax error near unexpected token `$'do\r''
'est.sh: line 10: `do

```

---

### Post by 23dornot23d on 2011-09-28
for the loop 

[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

or google search on loops ....

[loop in bash linux]("http://www.google.com/search?client=ubuntu&channel=fs&q=loop+in+bash+linux&ie=utf-8&oe=utf-8")

sorry all I have time for at the moment ...... cul

---

### Post by dragonbook on 2011-09-28
Now it works ... But only if I insert the code directly into the terminal. Anyone know why I can not run it directly by double clicking on thumb.sh file?

 And many thanks for your help everyone so far, I've already learned a lot

---

### Post by sisco311 on 2011-09-28
The error message indicates that you have a carrige return character (ASCII 13, often written as ^M or \r) in the script. CRs are found just before newlines in text files generated by DOS/Windows apps. You can see them with ```
cat -e filename
```

There are three different kinds of line endings in common use:
[list]
[*]Unix systems use Line Feeds (LFs) only.
[*]MS-DOS and Windows systems use CR-LF pairs.
[*]Old Macintosh systems use CRs only.
[/list]

Most text editors allow you to save files in Unix format. For more details see BashFAQ #52 (link in my signature).

---

### Post by dragonbook on 2011-09-29
> **sisco311 said:**
> The error message indicates that you have a carrige return character (ASCII 13, often written as ^M or \r) in the script. CRs are found just before newlines in text files generated by DOS/Windows apps. You can see them with ```
cat -e filename
```There are three different kinds of line endings in common use:
[LIST]
[*]Unix systems use Line Feeds (LFs) only.
[*]MS-DOS and Windows systems use CR-LF pairs.
[*]Old Macintosh systems use CRs only.
[/LIST]

Most text editors allow you to save files in Unix format. For more details see BashFAQ #52 (link in my signature).

Thank you, this fix my problem :)

---

### Post by sisco311 on 2011-09-29
Cool. Please don't forget to mark this thread as solved.

Once again, if you want to learn Bash scripting, check out the Bash Guide, FAQ and Pitfalls links from my signature. Of course, if you have any questions, please feel free to ask.

---

