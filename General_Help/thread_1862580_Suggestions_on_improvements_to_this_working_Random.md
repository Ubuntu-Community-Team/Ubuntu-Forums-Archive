---
title: "Suggestions on improvements to this working Random GNOME3 Wallpaper script?"
date: 2011-10-16
forum: General Help
---

### Post by inameiname on 2011-10-16
Knowing that my old GNOME2 random-wallpaper-changer script no longer works in Oneiric, I decided to write one myself. 

Anyway, I figured it out. It allows for multiple input folders for pictures, and it does pick one inside one of the folders at random. However, how I have written the script (it first randomly picks one of the folders (ie, each has a 50/50 chance), and then randomly picks a file inside it), unless each of the two folders has the same number of pictures, the pictures in the folder with the fewer number of pictures will be used far more than the other one. 

So this is my question. Is there a better way to have it give all the pictures, no matter the folder, and equal chance at randomly getting selected.

Here is the script. Once again, it works, so this isn't a huge deal. I am just curious if I could find an even better way:

```

#!/bin/bash



###################################
# Random-Gnome3-Wallpaper.sh                      
# Creator:        Inameiname                
# Version:        1.0                              
# Last modified:  16 October 2011          
# License:        GPLv3+                  
#                                       
# Descripton:                             
# Script to randomly set Background from files in a  
# directory(s) in GNOME3                      
#                                      
# Installation Instructions:                         
# Put in ~/.gnome2/nautilus-scripts directory and     
# right click to run.                             
# Can also put as startup script in Startup Applications
# so will run at every startup for rotating backgrounds
###################################



# Directories Containing Pictures (to add more folders here, just "/path/to/your/folder")
arr[0]="/usr/share/backgrounds"
arr[1]="$HOME/Pictures/Backgrounds"
# arr[2]=
# arr[3]=
# arr[4]=
# arr[5]=
# arr[6]=
# arr[7]=
# arr[8]=
# arr[9]=
# arr[10]=

# How many picture folders are there? (currently = 2)
rand=$[ $RANDOM % 2 ]

# Command to select a random folder
DIR=`echo ${arr[$rand]}`

# Command to select a random file from directory
# The *.* should select only files (ideally, pictures, if that's all that's inside)
PIC=$(ls $DIR/*.* | shuf -n1)

# Command to set background Image
gsettings set org.gnome.desktop.background picture-uri "file://$PIC"

```

---

### Post by hwttdz on 2011-10-17
Say you set your desktop to wallpaper.jpg

You can run something like
find /path/to/folder/containing/possible/wallpapers -type f -name "*.jpg"|rl|head -n 1|xargs -I{} bash -c "ln -s {} /path/to/wallpaper.jpg"

which will find all the jpgs, sort them in a random order (you can use sort -R as well, but it doesn't scale well), and then update the link which is wallpaper.jpg to point to the one it selected.  You might need to deal with some overwriting stuff, possibly link to wallpaper_temp.jpg and then move wallpaper_temp.jpg to wallpaper.jpg.  You can put it in a cronjob to have it run say every 10 minutes.

Or just looking at yours, you could use the same 

gsettings set org.gnome.desktop.background picture-uri "file://$PIC"

command, so instead of the linking stuff do

...|xargs -I{} bash -c "gsettings set org.gnome.desktop.background picture-uri \"file://{}\""

---

### Post by inameiname on 2011-10-17
> **hwttdz said:**
> Say you set your desktop to wallpaper.jpg

You can run something like
find /path/to/folder/containing/possible/wallpapers -type f -name "*.jpg"|rl|head -n 1|xargs -I{} bash -c "ln -s {} /path/to/wallpaper.jpg"

which will find all the jpgs, sort them in a random order (you can use sort -R as well, but it doesn't scale well), and then update the link which is wallpaper.jpg to point to the one it selected.  You might need to deal with some overwriting stuff, possibly link to wallpaper_temp.jpg and then move wallpaper_temp.jpg to wallpaper.jpg.  You can put it in a cronjob to have it run say every 10 minutes.

Or just looking at yours, you could use the same 

gsettings set org.gnome.desktop.background picture-uri "file://$PIC"

command, so instead of the linking stuff do

...|xargs -I{} bash -c "gsettings set org.gnome.desktop.background picture-uri \"file://{}\""


Thanks for the suggestion. I'm trying to better understand your way, as it contains things I've never seen before. I am curious, though...is it more or less another way of randomly selecting a file (.jpg in your case) inside one folder? Does it do multiple folders? Sorry, but it was a bit confusing to me. Then again, it is 1AM here, so who knows what the reason for that is. :P

I was trying something like:

find "$HOME/Pictures/Backgrounds" -type f -name "*.jpg"|rl|head -n 1|xargs -I{} bash -c "gsettings set org.gnome.desktop.background picture-uri\"file://{}\"" as a one-liner that I thought would do it all, but I guess that is not the way you were talking about.

---

### Post by hwttdz on 2011-10-17
The find command will find _every_ file inside that directory tree matching the conditions you specify (here I've specified file and jpg, you can also use or syntax so it's quite flexible).  The advantage is that it will weight each file that it finds equally (not each folder equally).  You could also put a "grep -v" in the middle to exclude the files you don't want (i.e. non image files).  

It might be enlightening to run 
"find . " on a directory structure thus (run in the toplevel folder).

```
/toplevel
  /folder_one
      /file1.txt
      /file2.txt
  /folder_two
      /file1.txt
      /file2.txt
      /file3.txt
```

---

### Post by inameiname on 2011-10-17
> **hwttdz said:**
> The find command will find _every_ file inside that directory tree matching the conditions you specify (here I've specified file and jpg, you can also use or syntax so it's quite flexible).  The advantage is that it will weight each file that it finds equally (not each folder equally).  You could also put a "grep -v" in the middle to exclude the files you don't want (i.e. non image files).  

It might be enlightening to run 
"find . " on a directory structure thus (run in the toplevel folder).

```
/toplevel
  /folder_one
      /file1.txt
      /file2.txt
  /folder_two
      /file1.txt
      /file2.txt
      /file3.txt
```

Ah, I see. That could work, I guess. Though, wouldn't a search in the top directory between a '/usr/share/backgrounds' and '~/Pictures/Backgrounds' folder be '/', which would result in a little hang to allow time for it to check everything? 

Anyway, that would work just fine I think if the directories were close. And also, I do appreciate the assistance. I love learning new ways and techniques in script-making.


Oh, and I just happened to find another way of doing this script, and after tweaking it a fair bit, I think I have figured out an even better way (albeit, not as pretty) to randomly change the wallpaper via a script, and have it equally choose a random file, regardless of the folder and the number of wallpapers inside:

```

#!/bin/bash
IFS=$'\n'

cat > "/tmp/.directorylist" <<"End-of-message"
/usr/share/backgrounds
/home/me/Pictures/Backgrounds
End-of-message
ALIST=( `cat "/tmp/.directorylist"` )
COUNTER=${#ALIST[@]}
find "${ALIST[$COUNTER-1]}" -maxdepth 1 -mindepth 1 -type f | grep ".bmp\|.BMP\|.jpeg\|.JPEG\|.jpg\|.JPG\|.png\|.PNG\|.SVG\|.svg" > "/tmp/.wallpaperlist"
let COUNTER-=1
until [ $COUNTER -lt 1 ]; do
find "${ALIST[$COUNTER-1]}" -maxdepth 1 -mindepth 1 -type f | grep ".bmp\|.BMP\|.jpeg\|.JPEG\|.jpg\|.JPG\|.png\|.PNG\|.SVG\|.svg" >> "/tmp/.wallpaperlist"
let COUNTER-=1
done
ALIST=( `cat "/tmp/.wallpaperlist"` )
RANGE=${#ALIST[@]}
let LASTNUM="`cat "/tmp/.lastwallpaper"` + 1"
let "number = $LASTNUM % $RANGE"
echo $number > "/tmp/.lastwallpaper"
echo "${ALIST[number]}" > "/tmp/.currentwallpaper"
gsettings set org.gnome.desktop.background picture-uri file://"${ALIST[$number]}"

```The only issue I see with this one, aside from having to use the '/tmp' folder, is that I cannot simply use "~" or "$HOME" for my home directory, but I have to write it all the way out.

---

### Post by hwttdz on 2011-10-17
For the /usr/share/background and ~/Pictures example you can do:

find /usr/share/background ~/Pictures

and it will find all files in either, you really want to avoid running find on / as it will take a long time and there are a lot of images there that are not viable backgrounds.  So you want to give find directories that contain no extra files.  That bash script makes my head hurt just looking at it.

---

### Post by inameiname on 2011-10-17
> **hwttdz said:**
> For the /usr/share/background and ~/Pictures example you can do:

find /usr/share/background ~/Pictures

and it will find all files in either, you really want to avoid running find on / as it will take a long time and there are a lot of images there that are not viable backgrounds.  So you want to give find directories that contain no extra files.  That bash script makes my head hurt just looking at it.

Oh I see. So 'find /usr/share/background ~/Pictures/Backrounds' would handle the job of equally randomly searching inside for pictures, no matter which folder has more or less? Interesting.

Yeah, that was my thinking too. 

Haha, and yeah to that too. It is quite a headachy script. I prefer my must prettier, easier to read one, but the lack of giving all backgrounds in multiple folders an equal chance sucks. I'll look into that last 'find' comment you mentioned, though.

---

### Post by inameiname on 2011-10-17
So this seems to be working. I don't know why it wasn't when I tried it the first time, when I had only one folder inside. But so far so good.

Now, looking at it, it does look like it randomly searches equally within the two folders, and dishes out a random background. Very cool. I'll keep testing.

Definitely a LOT easier and cleaner than the others. One-liners rock.

```

find "/usr/share/backgrounds" "$HOME/Pictures/Backgrounds" -type f -name "*.jpg"|rl|head -n 1|xargs -I{} bash -c "gsettings set org.gnome.desktop.background picture-uri \"file://{}\""

```Although, one thing I would like it to also do is to check for not just ".jpg" files, but also ".bmp\|.BMP\|.jpeg\|.JPEG\|.jpg\|.JPG\|.png\|.PNG\|.SVG\|.svg" files. If I can figure out how to add a line like that inside, it would definitely be the easiest/coolest one of its kind around.

---

### Post by inameiname on 2011-10-17
I decided to just leave it at this. It seems to work just fine, and so long as there aren't any abnormal files inside the chosen directories (which I only keep with pictures), it will work fine here, no matter the extension.

Thank you for helping me here.

```

#!/bin/bash



##################################################
# Random-Gnome3-Wallpaper.sh     
# Creator:               Inameiname   
# Major Contributor:     hwttdz        
#                        (did most of work :P) 
# Version:               1.1           
# Last modified:         18 October 2011    
# License:               GPLv3+          
#                      
# Descripton:                   
# Script to randomly set desktop/gdm background 
# from files in a directory(s) in GNOME3   
#                       
# Requires: sudo-apt get install randomize-lines 
#                     
# Installation Instructions:             
# Put in ~/.gnome2/nautilus-scripts directory   
# and right click to run.           
# Can also put as startup script in Startup     
# Applications so will run at every startup for 
# rotating backgrounds              
##################################################



###### just add/remove as many directories as wish
find "/usr/share/backgrounds" "$HOME/Pictures/Backgrounds" -type f \( -name "*.bmp" -or -name "*.BMP" -or -name "*.jpeg" -or -name "*.JPEG" -or -name "*.jpg" -or -name "*.JPG" -or -name "*.png" -or -name "*.PNG" -or -name "*.svg" -or -name "*.SVG" \)|rl|head -n 1|xargs -I{} bash -c "gsettings set org.gnome.desktop.background picture-uri \"file://{}\""

```

UPDATED 18 October 2011:

Updated script.

---

### Post by hwttdz on 2011-10-17
The multiple extensions can be done easily a few different ways

1) grep the list generated by find for image extensions (note grep escaped period)
i.e. grep -E "\.jpg|\.png|\.gif" # can you even set gif backgrounds?

2) have find do the lifting for you (note shell escaped parens)
find dir1 dir2 -type f \( -name "*.jpg" -or -name "*.png" \)

3) you can have it keep picking a file at random until it gets one that passes as a picture (I admit this is almost as weird as your bash script, but on the other hand it's a kind of interesting and flexible way of checking if a file is an image).

exiftool test.txt|grep "Unknown file type" >/dev/null || echo "is a picture"

here I'm essentially using the exitstatus of grep to determine if a file is a valid photo (also, slightly annoyed that exiftool with exit with status 0 on a text file and just say "Error: Unknown file type").

---

### Post by inameiname on 2011-10-17
> **hwttdz said:**
> The multiple extensions can be done easily a few different ways

1) grep the list generated by find for image extensions (note grep escaped period)
i.e. grep -E "\.jpg|\.png|\.gif" # can you even set gif backgrounds?

2) have find do the lifting for you (note shell escaped parens)
find dir1 dir2 -type f \( -name "*.jpg" -or -name "*.png" \)

3) you can have it keep picking a file at random until it gets one that passes as a picture (I admit this is almost as weird as your bash script, but on the other hand it's a kind of interesting and flexible way of checking if a file is an image).

exiftool test.txt|grep "Unknown file type" >/dev/null || echo "is a picture"

here I'm essentially using the exitstatus of grep to determine if a file is a valid photo (also, slightly annoyed that exiftool with exit with status 0 on a text file and just say "Error: Unknown file type").

Thanks for the suggestions! That second one is the one I kept trying to do, finding similar online in my searches, but I couldn't quite get it right. Anyway, I think I will try that one. The first looks good too, its just to make it as simple as possible, why not just let 'find' do it, rather than adding another command, 'grep', in the mix. And the third is definitely an odd one. Idk if it is the best here, but the idea of it sounds very interesting, and potentially useful in the future in other scripts/commands I may write. Thanks.


UPDATE: 

Seems okay. I updated my script from above. Thanks!

---

