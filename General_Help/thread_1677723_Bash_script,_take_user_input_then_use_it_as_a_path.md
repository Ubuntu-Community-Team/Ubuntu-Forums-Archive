---
title: "Bash script, take user input then use it as a path"
date: 2011-01-29
forum: General Help
---

### Post by Sharft 6 on 2011-01-29
I'm trying to make a script to make it quicker to encode videos.

```

#!/bin/bash
[B]echo "Type the path of the video file"
read -er inputFile[/B]
echo "you have chosen "$inputFile" as the source."
echo "------------------------------------------------------"
echo "Choose an output filename."
read -e outputFile
echo "You have chosen "$outputFile".mp4 as the filename."
echo "------------------------------------------------------"
echo "Chose an audio bitrate (default: 128k)"
read -e audioBitrate
if [ -z "$audioBitrate" ]
then 
audioBitrate="128k"
fi
echo "You have chosen "$audioBitrate" as the audio bitrate."
echo "------------------------------------------------------"
echo "Set thread count (default: 0 (all))."
read -e threads
if [ -z "$threads" ]
then
threads="0"
fi
echo "You have set the thread count to $threads ."
echo "------------------------------------------------------"
echo "Set fps (default: same as source)."
read -e rate
if [ -z $rate ]
then
fps=""
echo "You have set the frame rate to the same as the source file."
else
fps="-r $rate"
echo "You have set the frame rate to $rate ."
fi
echo "------------------------------------------------------"
# pass 1
ffmpeg -i **$inputFile** -an -pass 1 -vcodec libx264 -vpre veryslow_firstpass -vpre ipod320 $fps -s 426x240 -vf crop=320:240 -threads $threads Videos/transcoding/complete/$outputFile.mp4

# pass 2
ffmpeg -i **$inputFile** -acodec libfaac -ab $audioBitrate -pass 2 -vcodec libx264 -vpre veryslow -vpre ipod320 $fps -s 426x240 -vf crop=320:240 -threads $threads Videos/transcoding/complete/$outputFile.mp4

```

```

Videos/transcoding/awesomeSettings.sh 
Type the path of the video file
/home/username/Videos/transcoding/source/Surviving\ Disaster/1001_20100816203000.mpg
you have chosen /home/username/Videos/transcoding/source/Surviving\ Disaster/1001_20100816203000.mpg as the source.
------------------------------------------------------
Choose an output filename.
sds01e01
You have chosen sds01e01.mp4 as the filename.
------------------------------------------------------
Chose an audio bitrate (default: 128k)
192
You have chosen 192 as the audio bitrate.
------------------------------------------------------
Set thread count (default: 0 (all)).

You have set the thread count to 0 .
------------------------------------------------------
Set fps (default: same as source).

You have set the frame rate to the same as the source file.
------------------------------------------------------
FFmpeg version SVN-r25320, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  3 2010 13:10:27 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.32. 0 / 50.32. 0
  libavcore      0. 9. 0 /  0. 9. 0
  libavcodec    52.92. 0 / 52.92. 0
  libavformat   52.79. 0 / 52.79. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.48. 0 /  1.48. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
**/home/username/Videos/transcoding/source/Surviving\: No such file or directory**
FFmpeg version SVN-r25320, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  3 2010 13:10:27 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.32. 0 / 50.32. 0
  libavcore      0. 9. 0 /  0. 9. 0
  libavcodec    52.92. 0 / 52.92. 0
  libavformat   52.79. 0 / 52.79. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.48. 0 /  1.48. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
**/home/username/Videos/transcoding/source/Surviving\: No such file or directory**

```

The problems is that the backslash in the path is exiting the command rather than just indicating a space. If I put quotations around the variable that holds the path, then the backslashes from the user input will still be there so the path will not be valid.

any ideas?

---

### Post by lykeion on 2011-01-29
Try enclose $inputFile with quotes (-> "$inputFile" in the ffmpeg lines). Otherwise it will treat an inputFile with space as two files (--> Surving, Disaster.mpg)

Hope it helps

---

### Post by tredegar on 2011-01-29
Try
```
ffmpeg -i **[COLOR="Red"]"[/COLOR]$inputFile[COLOR="Red"]"[/COLOR]** -an -pass 1 -vcodec libx264 -vpre veryslow_firstpass -vpre ipod320 $fps -s 426x240 -vf crop=320:240 -threads $threads Videos/transcoding/complete/$outputFile.mp4
  
```

---

### Post by Sharft 6 on 2011-01-29
now it says
/home/user/Videos/transcoding/source/Surviving**\** Disaster/1001_20100809203000.mpg: No such file or directory

because adding quotation marks doesn't remove the backslash from user intput.

e.g.
```

mkdir directory\ with\ spaces
cd "directory\ with\ spaces"
bash: cd: directory\ with\ spaces: No such file or directory

```

---

### Post by lykeion on 2011-01-30
Let's say I have a video with a filename with a space in it (replace ~ with your home dir): 
~/Videos/my video.avi

After the read command I enter the full path to the video file (using no escaped space characters)
```
> read f
~/Videos/my video.avi
```
Then trying ffmpeg command on the $f variable:
1. Without quoting the variable - will give you ~/Videos/my: no such file or directory)
```
> ffmpeg -i $f
```
2. When quoting the variable ffmpeg will find the video file
```
> ffmpeg -i "$f"
```

---

### Post by asmoore82 on 2011-01-30
You should always quote all variable references in a bash script.

Whenever you back yourself into a corner where you think you really need
an unquoted variable, it usually means something else is wrong in the thought process.

Quote all of your variable references and try your script with `read -e` instead of `read -er`


For bonus awesome points, you might want to look into the zenity package.
It's a little unruly to interface with at first,
but when you get the hang of it, you can really get the Wow effect.

For example, zenity can quickly throw a standard file open dialog, but
it's going to "echo" the chosen filename with full path back to its stdout.

So you must catch this filename with the "$( ... )" construct.

Also, the user could have hit the cancel button or simply closed the "open" dialog,
so you should immediately test to see if the filename is empty...

```
filename=$( zenity --file-selection )

if [ [COLOR="Purple"]"z[COLOR="Red"]$filename[/COLOR]"[/COLOR] = [COLOR="Purple"]"z"[/COLOR] ]
then
    zenity --info --text [COLOR="Purple"]"User cancelled."[/COLOR]
    [COLOR="Blue"]#maybe do some other cleanup actions[/COLOR]
    exit
fi

[COLOR="Blue"]#continue normal operation with a guaranteed valid "$filename"[/COLOR]
```

---

### Post by Sharft 6 on 2011-02-01
> **asmoore82 said:**
> Quote all of your variable references and try your script with `read -e` instead of `read -er`


That works perfect. thank you

zenity sounds good but I want to keep in cli so I can ssh into the media box, run the script, then copy over the video all from my android phone.

---

### Post by Sharft 6 on 2011-02-04
I tried editing my script so it can que up a number of jobs but I'm back to my original problem again. This time all my variables are referenced with "" except for the array at the end.
```

#!/bin/bash
counter="0"
addOne="y"
while [ "$addOne" == "y" -o "$addOne" == "Y" ]
do
[B]echo "Type the path of the video file"
read -e inputFile[/B]
echo 'You have chosen "'"$inputFile"'" as the source.'
echo "------------------------------------------------------"
echo "Choose an output filename."
read -e outputFile
echo 'You have chosen "'"$outputFile"'.mp4" as the filename.'
echo "------------------------------------------------------"
echo "Choose an encoding speed/quality preset (1=ultrafast, 2=superfast, 3=veryfast, 4=faster, 5=fast, 6=medium, 7=slow, 8=slower, 9=veryslow, 10=placebo (default: medium)"
read -e encodingSpeed
case "$encodingSpeed" in
1)
ffpreset="ultrafast";;
2)
ffpreset="superfast";;
3)
ffpreset="veryfast";;
4)
ffpreset="faster";;
5)
ffpreset="fast";;
6)
ffpreset="medium";;
7)
ffpreset="slow";;
8)
ffpreset="slower";;
9)
ffpreset="veryslow";;
10)
ffpreset="placebo";;
*)
ffpreset="medium";;
esac
echo 'You have chosen "'"$ffpreset"'" as the preset.'
echo "------------------------------------------------------"
echo "Chose an audio bitrate (default: 128)"
read -e audioBitrate
if [ -z "$audioBitrate" ]
then 
audioBitrate="128"
fi
echo 'You have chosen "'"$audioBitrate"'k" as the audio bitrate.'
echo "------------------------------------------------------"
echo "Set thread count (default: 0 (all))."
read -e threads
if [ -z "$threads" ]
then
threads="0"
fi
echo 'You have set the thread count to '"$threads"'.'
echo "------------------------------------------------------"
echo "Set fps (default: same as source)."
read -e rate
if [ -z $rate ]
then
fps=""
echo "You have set the frame rate to the same as the source file."
else
fps="-r $rate"
echo 'You have set the frame rate to '"$rate"'fps.'
fi
echo "------------------------------------------------------"
echo "Would you like to transcode another file? [y/N]"
read -e addOne
**pass1Video["$counter"]='ffmpeg -i '"$inputFile"' -an -pass 1 -vcodec libx264 -vpre '"$ffpreset"'_firstpass -vpre ipod320 $fps -s 426x240 -vf crop=320:240 -threads '"$threads"' /home/philip/Videos/transcoding/complete/'"$outputFile"'.mp4'**
# pass2Video["$counter"]='-i '"$inputFile"' -acodec libfaac -ab '"$audioBitrate"'k -pass 2 -vcodec libx264 -vpre '"$ffpreset"' -vpre ipod320 '"$fps"' -s 426x240 -vf crop=320:240 -threads '"$threads"' -y /home/philip/Videos/transcoding/complete/'"$outputFile"'.mp4'
# echo "${pass1Video["$counter"]}"; exit 0
let counter++
done
counter2="0"
while [ "$counter" -gt "$counter2" ]
do
**${pass1Video["$counter2"]}**
# ffmpeg ${pass2Video["$counter2"]}
let counter2++
done

```

```

philip@philip-mythbuntu:~$ Videos/transcoding/awesomeSettings.sh 
Type the path of the video file
/var/lib/mythtv/videos/misc/Meet\ The\ Cast/tf2_hwguy.wmv 
You have chosen "/var/lib/mythtv/videos/misc/Meet The Cast/tf2_hwguy.wmv" as the source.
------------------------------------------------------
Choose an output filename.
hwg
You have chosen "hwg.mp4" as the filename.
------------------------------------------------------
Choose an encoding speed/quality preset (1=ultrafast, 2=superfast, 3=veryfast, 4=faster, 5=fast, 6=medium, 7=slow, 8=slower, 9=veryslow, 10=placebo (default: medium)
1
You have chosen "ultrafast" as the preset.
------------------------------------------------------
Chose an audio bitrate (default: 128)

You have chosen "128k" as the audio bitrate.
------------------------------------------------------
Set thread count (default: 0 (all)).

You have set the thread count to 0.
------------------------------------------------------
Set fps (default: same as source).

You have set the frame rate to the same as the source file.
------------------------------------------------------
Would you like to transcode another file? [y/N]

FFmpeg version git-d33ed7b, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan 30 2011 22:51:44 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 36. 0 / 50. 36. 0
  libavcore     0. 16. 1 /  0. 16. 1
  libavcodec   52.108. 0 / 52.108. 0
  libavformat  52. 94. 0 / 52. 94. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 74. 0 /  1. 74. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
**/var/lib/mythtv/videos/misc/Meet: No such file or directory**

```

---

### Post by Sharft 6 on 2011-02-05
I've done lots of playing around now and I still can't figure it out.

The question is - **how do I put a command with a path that has spaces into a variable and then execute the command that I put in a variable?**

Here are my test results:
```

philip@philip-mythbuntu:~$ Videos/transcoding/test.sh 
path='/var/lib/mythtv/videos/misc/Meet The Cast/'
echo "This works"
[COLOR="Red"]This works[/COLOR]
echo "$path"
[COLOR="Red"]/var/lib/mythtv/videos/misc/Meet The Cast/[/COLOR]
echo "This also works"
[COLOR="Red"]This also works[/COLOR]
echo $path
[COLOR="Red"]/var/lib/mythtv/videos/misc/Meet The Cast/[/COLOR]
echo "This works too"
[COLOR="Red"]This works too[/COLOR]
cd "$path"
echo "But this doesn't work"
[COLOR="Red"]But this doesn't work[/COLOR]
cd $path
[COLOR="Red"]Videos/transcoding/test.sh: line 11: cd: /var/lib/mythtv/videos/misc/Meet: No such file or directory[/COLOR]
echo "And neither does this"
[COLOR="Red"]And neither does this[/COLOR]
cd /var/lib/mythtv/videos/misc/Meet The Cast/
[COLOR="Red"]Videos/transcoding/test.sh: line 13: cd: /var/lib/mythtv/videos/misc/Meet: No such file or directory[/COLOR]
echo "This works"
[COLOR="Red"]This works[/COLOR]
cd "/var/lib/mythtv/videos/misc/Meet The Cast/"
echo -e "\n"


cd ~
[B]echo "None of the following works"
[COLOR="Red"]None of the following works[/COLOR]
echo "Like this"
[COLOR="Red"]Like this[/COLOR]
fullCommand="cd $path"
$fullCommand
[COLOR="Red"]Videos/transcoding/test.sh: line 21: cd: /var/lib/mythtv/videos/misc/Meet: No such file or directory[/COLOR]
echo "This2"
[COLOR="Red"]This2[/COLOR]
fullCommand="cd ""$path"
$fullcommand
ls -ld
[COLOR="Red"] 62 philip philip 4096 2011-02-06 13:09 .[/COLOR]
echo "This3"
[COLOR="Red"]This3[/COLOR]
fullCommand="cd /var/lib/mythtv/videos/misc/Meet The Cast/"
$fullCommand
[COLOR="Red"]Videos/transcoding/test.sh: line 28: cd: /var/lib/mythtv/videos/misc/Meet: No such file or directory[/COLOR]
echo "this4"
[COLOR="Red"]this4[/COLOR]
fullCommand="cd ""/var/lib/mythtv/videos/misc/Meet The Cast/"
$fullCommand
[COLOR="Red"]Videos/transcoding/test.sh: line 31: cd: /var/lib/mythtv/videos/misc/Meet: No such file or directory[/COLOR]
echo "Or all of the above referenced like this"
[COLOR="Red"]Or all of the above referenced like this[/COLOR]
"$fullCommand"
[COLOR="Red"]Videos/transcoding/test.sh: line 33: cd /var/lib/mythtv/videos/misc/Meet The Cast/: No such file or directory[/COLOR]
echo 'and take my word for it that putting "" inside the $path variable doesn'"'t help either."
[COLOR="Red"]and take my word for it that putting "" inside the $path variable doesn't help either.[/COLOR][/B]

```

I'm wondering if I should make a script that converts all directories with spaces to directories with out spaces.

Sofia Lamb from bioshock is wrong. For a utopia to exist, all knowledge and consciousness does not need to reside in one person. Simply removing spaces from all human languages would suffice.

---

### Post by tredegar on 2011-02-06
> I'm wondering if I should make a script that converts all directories with spaces to directories with out spaces.
This is probably the most sensible solution. Here's a useful one-liner:```
\ls  | while read -r file;  do [COLOR="Red"]echo[/COLOR] $file  $(echo $file | tr " " "_"); done
```
The \ at the start of the line is not a typo, but we want to use the vanilla version of **ls**, not the one with the pretty colours.

It reads all the filenames in the current directory and converts spaces to underscores. It does not rename the files, it just lists the new names. This is just so you can see what it does.

If you like it, you can try this to *rename* the files:```
\ls  | while read -r file;  do [COLOR="Red"]mv[/COLOR] $file  $(echo $file | tr " " "_"); done
```

This only works on the current directory.

To make it recurse through all subdirectories and files, use the -R option to ls:
```
\ls [COLOR="Red"]-R[/COLOR] | while read -r file;  do [COLOR="Red"]mv[/COLOR] $file  $(echo $file | tr " " "_"); done
```

Have fun.

---

### Post by lykeion on 2011-02-06
I don't know why you are mixing single and double quotes in your script like you do, like I said before, just quote the path containing spaces when you pass it as input to ffmpeg.
Example, let's say my video is in this dir: $HOME/Desktop/tmp/space dir/video.avi
If I put this path in variable my_path like this:
```
my_path="$HOME/Desktop/tmp/space dir/video.avi"
```
I could use this variable **quoted** to convert it using ffmpeg
```
ffmpeg -i "$my_path" video.mpg
```

---

### Post by Sharft 6 on 2011-02-07
Yeah I can do that.

But how would you put the entire command in a variable?

```

my_path="$HOME/Desktop/tmp/space dir/video.avi"
entire_command="ffmpeg -i "$my_path" video.mpg"
"$entire_command"

```

won't work.

---

### Post by lykeion on 2011-02-07
> **Sharft 6 said:**
> But how would you put the entire command in a variable?
I wouldn't do that, otherwise you'd get the problems that you're having. Use a function instead....this example shows a script with a function that takes input and output files as arguments:
```

#!/usr/bin/env bash

my_func() {
	# store input argument in variable arg1
	input="$1"
	# store outut argument in variable arg2
	output="$2"

	# exit if input argument is not a file
	if [ ! -f "$input" ]; then
		echo "file is not valid, will quit..."
		exit 1
	fi
	# exit if input argument is not a .avi file
	if [ ! ${input##*.} = avi ]; then
		echo "not a video, will exit..."
		exit 1
	fi
	# do the ffmpeg conversion
	ffmpeg -i "$input" "$output"
	echo "successfully converted to $output"
}

# testing the function...declare a variable with valid path to a .avi file
video_in="/path/to/valid avi/file.avi"
# ...and a variable where to save the converted video
video_out="/path/to/save mpg/file.mpg"
# call the function with the variables as arguments
my_func "$video_in" "$video_out"

```

PS. I think the best way to learn bash scripting is to look at other people's scripts.
Here are some old but good articles you should take a look at:
[http://www.ibm.com/developerworks/linux/library/l-bash.html](http://www.ibm.com/developerworks/linux/library/l-bash.html)
[http://www.ibm.com/developerworks/linux/library/l-bash2.html](http://www.ibm.com/developerworks/linux/library/l-bash2.html)

---

### Post by Sharft 6 on 2011-02-11
Yay i got it!

The first link you sent me under "Command substitution" has the answer. And your right, those articles have all the good juicy bits.

I wanted my script to store a whole lot of transcoding jobs with their parameters and then work away at them one by one after all user input has been taken. I don't see how functions help with this. I will eventually put functions in just to tidy everything up but for now it's working how I want it.

---

