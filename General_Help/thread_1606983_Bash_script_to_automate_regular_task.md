---
title: "Bash script to automate regular task"
date: 2010-10-27
forum: General Help
---

### Post by oldmankit on 2010-10-27
Hi,

I have a need for a no doubt simple script, and started to have a look at working out how to write bash scripts myself, but realised it will take me many hours and someone else just a few minutes.  And I very rarely need custom bash scripts.  So if you have time to help, please do.

Every photo I take is in two formats, JPG and CR2 (a raw format).  As soon as I download them onto my computer, I put all CR2 images into a new folder, ./raw  The file name before the suffix is exactly the same, e.g. ./IMG_4063.JPG and ./raw/IMG_4063.CR2  

I then go through the JPGs, deleting all of the poor ones.  

At this point I want to delete all of the CR2 images for which I deleted the JPG image.

I would like a script that can take all  .JPG files in the current directory and delete any .CR2 files for which there is no corresponding .JPG.

Many thanks in advance.

---

### Post by DaithiF on 2010-10-27
something like:
```
#!/bin/bash
[[ ! -d raw ]] && { echo "No 'raw' subdirectory found, are you in the right driectory?'"; exit 1; }

shopt -s nullglob

for file in raw/*.CR2
do
        filename=${file##*/}
        jpg_filename="${filename%.CR2}.JPG"
        if [[ ! -e "$jpg_file" ]]; then
                echo "About to delete $file as no matching JPG exists"
                echo "rm -f $file"
        fi
done

```
Remove the echo from around the rm -f line once happy that its finding the right files

---

### Post by oldmankit on 2010-10-28
> **DaithiF said:**
> something like:
```
#!/bin/bash
[[ ! -d raw ]] && { echo "No 'raw' subdirectory found, are you in the right driectory?'"; exit 1; }

shopt -s nullglob

for file in raw/*.CR2
do
        filename=${file##*/}
        jpg_filename="${filename%.CR2}.JPG"
        if [[ ! -e "$jpg_file" ]]; then
                echo "About to delete $file as no matching JPG exists"
                echo "rm -f $file"
        fi
done

```Remove the echo from around the rm -f line once happy that its finding the right files

Thanks so much.  Your thousandth post.  

I ran this and it matched every single CR2 in ./raw, even if the JPG existed in ./

For example, it said:
> About to delete raw/IMG_4105.CR2 as no matching JPG existsyet IMG_4105.JPG exists.

Glad you put the echo in before rm -f $file!  

I honestly don't have a clue how your script works so I can't guess where the problem is.

---

### Post by DaithiF on 2010-10-28
sorry, typo, amend as follows:
```
jpg_filename="${filename%.CR2}.JPG"
        if [[ ! -e "$jpg_file**[COLOR=Red]name[/COLOR]**" ]]; then
```

---

### Post by oldmankit on 2010-10-28
Lovely!  Thank you very much.  I will use this script often.

---

### Post by oldmankit on 2010-11-26
Just to say that this script is already being massively useful to me!

---

### Post by DaithiF on 2010-11-26
good, I'm glad to hear it.

---

### Post by bodypilot on 2011-06-05
I too find this script very useful for deleting my CR2 files.

I have adapted it slightly:
```

#!/bin/bash
#http://ubuntuforums.org/showthread.php?t=1606983
#Directory structure for this to work:
#/Folder/Compressed/In-Camera compressed/IMG_1234.JPG
#/Folder/Raw/IMG_1234.CR2
#Edit "[[ ! -d ../../Raw ]]" and "for file in ../../Raw/*.CR2" if your directory structure is different.
#Run this script from the /Folder/Compressed/In-Camera compressed/ (or your equivalent) directory.

#check if Raw-directory exists
[[ ! -d ../../Raw ]] && { echo "No 'raw' directory found, are you in the right directory?'"; exit 1; }

shopt -s nullglob

for file in ../../Raw/*.CR2
do
        filename=${file##*/}
        jpg_filename="${filename%.CR2}.JPG"
        if [[ ! -e "$jpg_filename" ]]; then
        zenity --warning --title="Warning" --text="About to move $file to trash as no matching JPG exists"
        #http://www.linuxquestions.org/questions/programming-9/bash-script-how-to-move-files-to-trash-instead-of-deleting-819103/
                mv -f "$file" ~/.local/share/Trash/files/
        fi
done
zenity --info --title="RAW files deleted" --text="CR2 files without matching JPGs have been deleted to trash."  
```What this does is move the CR2 files to the trash-can instead of completely deleting them and adding a pop-up notification once the script finishes.

Add a # in front of the ```
zenity --warning --title="Warning" --text="About to move $file to trash as no matching JPG exists"
``` line once you're comfortable the script does what it's supposed to do.

Save this script to /home/USERNAME/.gnome2/nautilus-scripts and it will be available to you with a right-click in the Nautilus file manager.

---

