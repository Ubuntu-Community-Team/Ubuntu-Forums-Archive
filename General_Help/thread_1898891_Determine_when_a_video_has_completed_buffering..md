---
title: "Determine when a video has completed buffering."
date: 2011-12-22
forum: General Help
---

### Post by slotlocker on 2011-12-22
Hello,
I was writing this small script the other day.It is a small program which basically finds the flash videos running in the browser and downloads them.
the code goes something like this..

code:
path=$(stat -c %N /proc/*/fd/* 2>&1|awk -F[\`\'] '/lash/{print$2}')
pid=$(echo $path | cut -d / -f3)
name=$( ps --no-header -o comm -p $pid)
mid=$(wmctrl -l | grep -i $name)

filename=`echo $mid | cut -c 21-$(($(echo $mid | wc -c)-16))`


cp $path /home/Downloads/"$filename.avi"



this is just a PART of the code.The first line of the code gets the path to the deleted temp file.The second line gets the pid. Third the process name.Fourth the window id and the window title.The fifth line manipulates the wmctrl output to extract the name of the video playing(most of the time the name of the video is included in the window title..for example youtube)

Now when this script is run after the whole video has buffered,it runs flawlessly(this above script works for google chrome)..and copies the file from the /proc/<pid>/fd folder to the downloads folder and changes its name to the extracted filename.

Now here comes the trick part.I want to automate this code,like,for me to run this code as of now i have to wait for the video to finish buffering(say youtube).

I want this script to determine when the video has finished buffering and then go ahead with the copying part without me having to manually run it at the end of a video.

So is there any way in which i can get to know when a video has completed buffering?

I am a beginner.Any suggestions for improving the code are welcome :)

---

### Post by nothingspecial on 2011-12-22
Hi,

Read this

[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

Closed.

---

