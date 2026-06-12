---
title: "Periodic screenshot utility."
date: 2012-05-12
forum: General Help
---

### Post by UAdnan on 2012-05-12
Hello UF,

It's been around 3 days that I am fetching the web to find any kind of utility or script that would automatically take screen-shots of my desktop activity at specified intervals.

All I have yet found is a script that I wrote in the Terminal, and it worked. After it, I re-wrote the script in a text editor and saved it as Screenshots.sh , which I think is correct. The script worked. It starts to work once when I start the file (I guess it's a shell ... ?), where I get three options: Display the content / Run in Terminal / Run. I usually hit Run, and it works fine.

Well, that's a good step forward, but there's still a problem remaining.

Actually, I would like that script to be automatically executed and to take screen-shots since the Start-up, without having to click on the file manually at first place.
Logically, I went to the Startup options, and located that .sh file and selected it, then wrote " *sh -c'<path/to/my/.sh>'* "

I then rebooted my computer, but no screen-shots were being token. What is even stranger, is that the .sh file is taking process in the System Monitor, so it must be running, but  I don't understand why I still have to enter the file manually for it to take action.

I am sorry not to provide the script right now because, uhm, I didn't get back home yet and I can't recall the script, I will write it when I get back, if ever we'll need it.


Thus, can anyone provide me with a Utility OR script that will:

**T**ake screen-shots at specified intervals and save them to a folder.
**S**tart taking those screen-shots since the startup, automatically without me having to run the .sh file.

For God's sake, make it clean and clear, the problem I've faced while googling my problem is that I am a total noob in Ubuntu, so please tell me every little step that should be done.

Thanks in advance,
Adnan.

---

### Post by UAdnan on 2012-05-12
I am surprised my post got to the 4th page with no answers yet. Is really that hard ? :(

---

### Post by Carborundum on 2012-05-12
When you want something to happen periodically in Linux, you use cron.

You can edit your crontab (which controls cron) by running the command ```
crontab -e
``` There, add the line ```
0 * * * * ./path/to/your/script
``` to run your script once every hour. You can of course change the frequency to suit your needs.

---

### Post by UAdnan on 2012-05-13
Well, I've made a bunch of stuff and modifications (Regarding this topic: [http://ubuntuforums.org/showthread.php?t=90566](http://ubuntuforums.org/showthread.php?t=90566) ) that didn't work either, so I made some modifications in the Startup Applications, and finally, the script worked.

But, I've set the script to take one screen-shot per 20 seconds, but I can't understand why it's being one screen-shot per minute. 

Help please !

---

### Post by Carborundum on 2012-05-13
> **UAdnan said:**
> Well, I've made a bunch of stuff and modifications (Regarding this topic: [http://ubuntuforums.org/showthread.php?t=90566](http://ubuntuforums.org/showthread.php?t=90566) ) that didn't work either, so I made some modifications in the Startup Applications, and finally, the script worked.

But, I've set the script to take one screen-shot per 20 seconds, but I can't understand why it's being one screen-shot per minute. 

Help please !
Post your script. Without it, any attempt to help you would just be guesswork.

---

### Post by UAdnan on 2012-05-13
screenshot_dir='screens'
seconds='20';
if [ ! -d "$screenshot_dir" ]; then
mkdir $screenshot_dir;
fi
while [ 1 ]; do
sleep $seconds;
(import -window root $screenshot_dir/screenshot-$(date +%M_%k_%d_%m_%Y|sed -e 's/^ *//').png) &
done


It's all going fine, except the issue I told you about. My script appears to be very logical...

---

### Post by Vaphell on 2012-05-13
date +%M_%k_%d_%m_%Y
there are no seconds here, so your screenshots sharing the month/day/hour/minute part are saved with the same name overwriting older entries.
is that sed part necessary at all?

besides i think you got your format backwards, it's not sortable in any logical way, if you used the year-month-day-hour-minute-seconds format, lexical order would be the same as chronological order.

---

### Post by UAdnan on 2012-05-13
Great, I just added  %S and everything went fine.

But, aren't there any way to lower the quality of the screen-shot ? A piece of line to add or modify ? Like half the quality, or something like that.

---

### Post by Carborundum on 2012-05-13
> **UAdnan said:**
> Great, I just added  %S and everything went fine.

But, aren't there any way to lower the quality of the screen-shot ? A piece of line to add or modify ? Like half the quality, or something like that.
You can set the quality with ```
-quality <value>
```Note that .png is a lossless format, so if you use it you control compression level instead of quality, with 100 being the highest compression level (and the lowest file size).

If you instead use .jpg or some other lossy format, the -quality option works as expected, with 0 being the lowest quality (and lowest file size).

For further information, see [the documentation]("http://www.imagemagick.org/script/command-line-options.php?ImageMagick=cnnjbgtudejiib6c8t2oi2v324#quality").

---

### Post by UAdnan on 2012-05-14
[I]screenshot_dir='screens'
seconds='30';
if [ ! -d "$screenshot_dir" ]; then
mkdir $screenshot_dir;
fi
while [ 1 ]; do
sleep $seconds;
(import -window root $screenshot_dir/screenshot-$(date +%S_%M_%k_%d_%m_%Y|sed -e 's/^ *//').jpg) &
-quality 5
done[/I]

Maybe I wrote in the wrong place, I am not good at these, I didn't write the whole script by myself, anyway.

So, how should I put it ?

---

### Post by UAdnan on 2012-05-14
**...**

---

### Post by scouser73 on 2012-05-14
***_Ubuntu Forum DO's and DON'T's_***

***DON'T***

* ** 8 ** Bump your posts too often (around once every 24 hours is recommended)*

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by Vaphell on 2012-05-14
how about putting it before/after **-window root** switch/value combo, inside ()?

command line tools usually go like this

```
command_name -option1 value1 -option2 value2 ... file(s)/folder(s)
```

what is available: *import --help*

---

### Post by UAdnan on 2012-05-14
I can't understand how to put it.

Are you able to fix the script I wrote just in the previous post ? That will be easier.
If not, explain further.


Thanks.

---

### Post by Vaphell on 2012-05-14
```
import -window root **-quality N** $screenshot_dir/screenshot-$(date +%M_%k_%d_%m_%Y|sed -e 's/^ *//').png
```

---

### Post by HiImTye on 2012-05-14
just save this wherever you want to run it from. it will store your images in $HOME/Pictures/Screenshots/<date>/<time>.png
```
#!/bin/bash
# declare variables
delay=20 				# seconds to delay
basefolder=$HOME/Pictures/Screenshots	# our main screenshot folder

# create our basefolder if it doesn't exist
if [ ! -d $basefolder ]; then
 mkdir $basefolder
fi
# move into it
cd $basefolder

# meat n pooptatoes
while :
do
 currentdate="$(date +%x)"
 if [ ! "$reference" = "$currentdate" ]; then
   mkdir $currentdate
   reference="$currentdate"
   shotfolder="$basefolder/$currentdate"
   if [ ! -d "$shotfolder" ]; then
     mkdir $shotfolder
   fi
 fi
 currenttime="$(date +%X)"
 import -quality 5 -window root $shotfolder/$currenttime.png
 sleep $delay
done
```

---

### Post by UAdnan on 2012-05-15
Well,_ HilmTye_, I'm sorry to tell you that the script you've written didn't work, it has  just created a "Screenshot" folder within the Pictures folder, containing three sub-folders, the first one having the date day, the second named as the current month, and the last folder named "2012". That's fine, but add to it that no screen-shots were being token.
I'm sorry for that, hope I didn't waste much of your time.

After re-reading my script, I understood how _Vaphell  _has put the script, and here's how my script looks like now and it's working as expected:

screenshot_dir='screens'
seconds='30';
if [ ! -d "$screenshot_dir" ]; then
mkdir $screenshot_dir;
fi
while [ 1 ]; do
sleep $seconds;
(import -window root -quality 3 $screenshot_dir/screenshot-$(date +%S_%M_%k_%d_%m_%Y|sed -e 's/^ *//').jpg) &
done


Thanks to everyone who helped be going through my issue.

---

### Post by HiImTye on 2012-05-15
sorry about that, I didn't actually test it and as a result, neglected quotes in the filename. if you're interested in it, here is the script, fixed:

```
#!/bin/bash
# declare variables
delay=20 				# seconds to delay
basefolder=$HOME/Pictures/Screenshots	# our main screenshot folder
extension=.png				# the extension we want to use
quality=5				# image quality

# create our basefolder if it doesn't exist
if [ ! -d $basefolder ]; then
 mkdir $basefolder
fi
# move into it
cd $basefolder

# meat n pooptatoes
while :
do
 currentdate="$(date +%x)"
 if [ ! "$reference" = "$currentdate" ]; then
   reference="$currentdate"
   shotfolder="$basefolder/$currentdate"
   if [ ! -d "$shotfolder" ]; then
     mkdir $shotfolder
   fi
 fi
 currenttime="$(date +%X)"
 import -quality $quality -window root "$shotfolder/$currenttime$extension"
 sleep $delay
done
```
the advantage to this script is that each day will have its' own folder (and is automagically created by the script on a new day) with the filenames simply being the time and the extension

as you can see, it works:
[ATTACH]217992[/ATTACH]

if you would like it edited so that, for instance, they are separated by hour into separate folders or whatever, just let me know. right now if you leave it running from midnight to midnight you will end up with a folder that has 4320 images inside it (with a 20 second interval)

---

### Post by UAdnan on 2012-05-16
Oh, lucky I came back to this thread. 

Thanks for the script, I just saved it and I will use it whenever I find it necessary ! :)

---

### Post by UAdnan on 2012-05-26
Hey guys, sorry for having to Up this topic, but it's not as old and I need to add something to it:

Can I modify the screen-shot file name to the focused window ? I can't  explain much so here's a photo to make things clearer:




[IMG]http://sournoishack.com/uploads/1120780663Screenshot_from_2012_05_28_11_18_16.png[/IMG]

---

### Post by UAdnan on 2012-05-29
Please...

---

### Post by UAdnan on 2012-05-30
I'll try one more time.

---

