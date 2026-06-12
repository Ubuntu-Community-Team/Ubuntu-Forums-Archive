---
title: "ffmpeg bash script. While loop terminates unexpectedly..."
date: 2010-09-27
forum: General Help
---

### Post by mmz27 on 2010-09-27
Hi there

I have a problem with a batch file. My Batchfile searches for videos in a directory with the .mov ending and writes the absolut path into the (hidden) file called .paths.tmp. I use that file with a while loop, which encodes all those .mov files to .mp4 files using ffmpeg. Basically, it works. BUT only with 1 file. After that, the while loop terminates without an error message. 

My "debugging" attempts: 

[LIST]
[*]Exclude the ffmpeg part and only echo the line which was read - works fine.
[*]Include the ffmpeg part - obv it doesn't work. I added two "start_while"/"end_while" text outputs. I noticed that the loop ends without actually taking that loop. The second output doesn't exists.
[*]The one file the while loop actually works, works perfectly.
[/LIST]

Any ideas why my while loop terminates? 

btw I use a Mac Snowlepard

I'm really out of ideas right now.... 
Cheers


```

[FONT=-moz-fixed]while read line 
do 
filename=$line; 
echo "start_while: $filename" 

'/Library/Application Support/ffmpegX/mencoder' "$filename" -ovc  x264 -nosound -ni -sws 0 -x264encopts  threads=2:me=2:bitrate=940:qp_min=22:qp_max=51:i4x4:keyint=120:cabac:deblock:nob_adapt:bframes=1  -ofps 25 -vop scale=640:480,pp=0x33,harddup -of rawvideo -o .videos_temp/output.264" 
/Applications/ffmpegX.app//Contents/Resources/movtowav -o ".videos_temp/output.wav" "$filename" 
/Applications/ffmpegX.app//Contents/Resources/normalize ".videos_temp/output.wav" 
/Applications/ffmpegX.app//Contents/Resources/ffmpeg -i  ".videos_temp/output.264" -i  ".videos_temp/output.wav" -y -vn -f mp4 -acodec  aac -ab 128 -ar 48000 -ac 2 -map 1.0:0.0  ".videos_temp/output.aac.mp4" 
/Applications/ffmpegX.app//Contents/Resources/mp4box -fps 25 -add  ".videos_temp/output.264"  -add  ".videos_temp/output.aac.mp4" -new  ".videos_temp/output.mp4" 
rm ".videos_temp/output.wav" 
rm ".videos_temp/output.264" 
rm ".videos_temp/output.aac.mp4" 

echo "end_while: $line" 
done < ".paths.tmp" 


[/FONT]

```

---

### Post by DaithiF on 2010-09-27
Hi,
a wild guess ... line-endings issue?  perhaps your paths file has old-mac style line endings (\r), as opposed to unix/linux (\n) ... which would cause the bash loop to read just 1 line rather than several.

---

### Post by mmz27 on 2010-09-27
Hi,
I thought so too... that's why I excluded the ffmpeg part from the file and run the script basically only with the while loop echo-ing the $filename. That one worked. That's why it's so confusing to me...

thanks anyway, I appreciate it!

---

### Post by DaithiF on 2010-09-27
> **mmz27 said:**
> Hi,
I thought so too... that's why I excluded the ffmpeg part from the file and run the script basically only with the while loop echo-ing the $filename. That one worked. That's why it's so confusing to me...

thanks anyway, I appreciate it!

yea but maybe your mac terminal is handling the single line with embedded '\r's and displaying those '\r's as newlines on your display ... ie. you may still just be going once through the loop.

you could add a counter to check for sure:
before the loop:
```
count=0
```

and 
```
count=$((count+1))
echo $count

```
within the loop

---

### Post by mmz27 on 2010-09-27
ok, modified my file to:

```

count=0
while read line 
do 
filename=$line;  
echo "start_while: $filename"  
'/Library/Application Support/ffmpegX/mencoder' "$filename" -ovc  x264 -nosound -ni -sws 0 -x264encopts  threads=2:me=2:bitrate=940:qp_min=22:qp_max=51:i4x4:keyint=120:cabac:deblock:nob_adapt:bframes=1  -ofps 25 -vop scale=640:480,pp=0x33,harddup -of rawvideo -o .videos_temp/output.264"  
/Applications/ffmpegX.app//Contents/Resources/movtowav -o ".videos_temp/output.wav" "$filename"  
/Applications/ffmpegX.app//Contents/Resources/normalize ".videos_temp/output.wav" 
/Applications/ffmpegX.app//Contents/Resources/ffmpeg -i  ".videos_temp/output.264" -i  ".videos_temp/output.wav" -y -vn -f mp4 -acodec  aac -ab 128 -ar 48000 -ac 2 -map 1.0:0.0  ".videos_temp/output.aac.mp4" 
/Applications/ffmpegX.app//Contents/Resources/mp4box -fps 25 -add  ".videos_temp/output.264"  -add  ".videos_temp/output.aac.mp4" -new  ".videos_temp/output.mp4" 

rm ".videos_temp/output.wav" 
rm ".videos_temp/output.264"  
rm ".videos_temp/output.aac.mp4"   
echo "end_while: $line"  

count=$((count+1)) echo $count
done < ".paths.tmp"   

```output is: 1

---

### Post by DaithiF on 2010-09-27
ok, so that confirms you have only 1 line in .paths.tmp then, so fix the line endings in that file.

---

### Post by mmz27 on 2010-09-27
[LEFT]yeah.... that's true.
I looked at my paths.tmp file. it is created as following:
```

find /vids -name *.mov -print > .paths.tmp

```After that I took a look at the file with a hex editor and saw, that a new line is in fact 0x0A which is equal to a '\n'. 
Also tried to change it to '\r' with the same result. 
:-(
[/LEFT]

---

### Post by hutou on 2010-09-27
Hi,
I ran into the same problem tonight and found the solution here :
[http://www.linuxquestions.org/questions/programming-9/bash-script-question-while-loop-514730/](http://www.linuxquestions.org/questions/programming-9/bash-script-question-while-loop-514730/)
Simply add ```
</dev/null
``` at the end of your ffmpeg statement !
Hope this helps !

---

### Post by mmz27 on 2010-09-28
Thank you very much!!! 
That was it..... added </dev/null at the end of the line and it worked. Do you know why it works? 

:guitar:

---

### Post by FakeOutdoorsman on 2010-09-28
FFmpeg can replace several of the other tools which makes a simpler script:
```

count=0
while read line 
do 
filename=$line;  
echo "start_while: $filename"  
/Applications/ffmpegX.app//Contents/Resources/ffmpeg -i "$filename" -f wav ".videos_temp/output.wav"
/Applications/ffmpegX.app//Contents/Resources/normalize ".videos_temp/output.wav" 
/Applications/ffmpegX.app//Contents/Resources/ffmpeg -i "$filename" -i  ".videos_temp/output.wav" -map 0:0 -map 1:0 -y -f mp4 -vcodec libx264 -vpre medium -crf 22 -acodec libfaac -ab 128k -ar 48000 -ac 2 -threads 0 ".videos_temp/output.mp4" 

rm ".videos_temp/output.wav" 

echo "end_while: $line"  

count=$((count+1)) echo $count
done < ".paths.tmp"   

```
The FFmpeg options I used are designed for a recent FFmpeg, so an older version may not accept the command.  It also assumes that stream 0.0 is always video, but that won't always be true.  A safer option, similar to what you were doing before, would be to run two instances of FFmpeg where the first command deals with video only and the second FFmpeg command encodes the audio and combines both streams.

---

