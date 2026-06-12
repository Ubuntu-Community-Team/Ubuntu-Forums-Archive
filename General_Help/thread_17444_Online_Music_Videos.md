---
title: "Online Music Videos ?"
date: 2005-02-28
forum: General Help
---

### Post by Ste on 2005-02-28
[http://launch.yahoo.com/](http://launch.yahoo.com/) -- Won't work unless you have Windows (I guess) just wondering if there is an alternative to this great site or a way to get it running through ubuntu. Preferrably without wine.


Ste.

---

### Post by rwabel on 2005-03-02
seems that yahoo don't like firefox...stupid people!!
try it with opera, should work

[QUOTE=Ste][http://launch.yahoo.com/]("http://launch.yahoo.com/") -- Won't work unless you have Windows (I guess) just wondering if there is an alternative to this great site or a way to get it running through ubuntu. Preferrably without wine.


Ste.[/QUOTE]

---

### Post by Ste on 2005-03-03
[QUOTE=rwabel]seems that yahoo don't like firefox...stupid people!!
try it with opera, should work[/QUOTE]
 Opera wouldn't work either, just tried Netscape like they say and that won't work either.
Stupid Yahoo. I've sent a form to their support about this issue anyway.

---

### Post by Jad on 2005-03-03
[QUOTE=Ste]Opera wouldn't work either, just tried Netscape like they say and that won't work either.
Stupid Yahoo. I've sent a form to their support about this issue anyway.[/QUOTE]
if you set Opera to identify as IE it will work 
so I believe if there is a agent switcher for firefox it will works

---

### Post by Ste on 2005-03-03
Did you get the online videos to work ?

---

### Post by Jad on 2005-03-03
didn't try it 
lemme try now

---

### Post by Jad on 2005-03-03
No, its not working 
it stick with "Opening the video lpayer"

---

### Post by bigzak on 2005-03-03
Try installing plugger (apt-get install mozplugger), which lets you use xine, mplayer or whatever as a plugin. Works great for most things. I can even get those awful movie trailer sites with embedded quicktime to play!

---

### Post by Ste on 2005-03-03
I have the mplayer-plugin for mozilla but this site still refuses to ply them.
The trailers sites are easy to view one of the first things I get working on a fresh install.

---

### Post by Jad on 2005-03-03
I'm sure if we have agent switcher its gonna work, 
its very stupid to restrict content based on browser
I think there is a firefox extension that can do it
I'll be looking for it today, and tell you back what happened.

---

### Post by delltony on 2005-03-03
Here this will solve your issue.
What you need to do is make a file i called mine launch.sh but you can name it whatever you want
then give it chmod +x 
once that is done then you simply go to launch's site and put the mouse over the the video you wish to watch it will give you an idea number look down at the bottom of the browser where you normally see Done it will say something  like javascript(223451)  remember that number and do the following
./launch.sh 223451
then set back and watch the clip via mplayer.
Enjoy!

#!/bin/bash

if [ $# -eq 0 ]; then
echo "Usage: launch.sh <videoid> (<bandwidth>) (<protocol>) <mplayer-options>"
echo " videoid = Lauch Video ID"
echo " bandwidth = 56,128,300 (default 300)"
echo " protocol = mms,http (default mms)"
echo " mplayer options can be passed via command line"
echo "Example:"
echo " MMS:"
echo " launch.sh 1112809 300 mms"
echo " HTTP:"
echo " launch.sh 1112809 300 http"
echo " HTTP with mplayer options:"
echo " launch.sh 1112809 300 http -verbose 0 -cache 500"
exit 0
fi

videoid=$1
shift

if [ $1 -eq $1 ] && [ $1 != 0 ]; then
bandwidth=$1
shift
else
# 56 or 128 or 300
bandwidth=300
fi

file1=$(wget "http://launchtoday.launch.yahoo.com/player/medialog.asp?vid=$videoid&cid=1&pid=4&csid=396500550&p1=&p2=&p3=2&bw=$bandwidth&mf=1&origin=35&pguid=AA388C059C7849D99CCFBC72B6F51E37&uid=42&sk=bad551cd352143eb2da02&z=ms.asx" -q -O -)

if [ $1 == "http" ]; then
file2=$(wget "$file1" -q -O - | sed 's/mms:/http:/g')
shift
else
file2=$(wget "$file1" -q -O -)
fi

mplayer -cache 500 $file2 $@
#comment the above line and uncomment this line if you wish to save the file instead of playing it
#it will be named viddump.wmv in your current working dir 
#mplayer -dumpstream $file2 $@ -dumpfile viddump.wmv

---

### Post by Ste on 2005-03-03
```
stephen@godspeed:~/temp/untitled folder $ sh launchfile.sh 8076023
launchfile.sh: line 22: [: !=: unary operator expected
launchfile.sh: line 32: [: ==: unary operator expected
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx


Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv[:dev]>  select video output driver & device ('-vo help' for a list)
 -ao <drv[:dev]>  select audio output driver & device ('-ao help' for a list)
 vcd://<trackno>   play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>   play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <timepos>    seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 up or down       seek backward/forward  1 minute
 pgup or pgdown   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 z or x           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *
```

I get the following error using your script.

---

### Post by delltony on 2005-03-03
that usually means you typed the number incorrectly.
try sh launch.sh 2151483
and tell me what you get.
it should generate alot of output then cache and play the file in mplayer.

---

### Post by Ste on 2005-03-03
[QUOTE=delltony]that usually means you typed the number incorrectly.
try sh launch.sh 2151483
and tell me what you get.
it should generate alot of output then cache and play the file in mplayer.[/QUOTE]
 Thank you!!!
It works. Maybe you should write this up as a howto for the forum or on the wiki.
Nice script :)

---

### Post by Jad on 2005-03-04
./launch.yahoo.sh: line 22: [: !=: unary operator expected
./launch.yahoo.sh: line 2: [http://launchtoday.launch.yahoo.com/player/medialog.asp?vid=14106176&cid=1&pid=4&csid=396500550&p1=&p2=&p3=2&bw=300&mf=1&origin=35&pguid=AA388C059C7849D99CCFBC72B6F51E37&uid=42&sk=bad551cd352143eb2da02&z=ms.asx:](http://launchtoday.launch.yahoo.com/player/medialog.asp?vid=14106176&cid=1&pid=4&csid=396500550&p1=&p2=&p3=2&bw=300&mf=1&origin=35&pguid=AA388C059C7849D99CCFBC72B6F51E37&uid=42&sk=bad551cd352143eb2da02&z=ms.asx:) No such file or directory
./launch.yahoo.sh: line 3: -q: command not found
./launch.yahoo.sh: line 34: [: ==: unary operator expected

---

### Post by Jad on 2005-03-04
Hey, I passed that page with Firefox agent switcher, but I got this 
ERROR


You must have Windows Media Player installed to use this application. Install Windows Media Player now.

Please use the following error code when writing to Yahoo! Help. (Error Code: 14)

---

### Post by Pablo928 on 2005-03-05
I've been complaining to Yahoo support about this issue for months. Seems that aside from their browser requirements, Yahoo Launch will only play through Windows Media Player.

---

### Post by delltony on 2005-03-05
[QUOTE=Pablo928]I've been complaining to Yahoo support about this issue for months. Seems that aside from their browser requirements, Yahoo Launch will only play through Windows Media Player.[/QUOTE]

Just curious what is wrong with the script i posted?
It works I use it constantly you just have to pass it the correct java id number thats it.
just put your mouse over the watch icon on the yahoo page and get the java id number and then pass it to the script that is why you are constantly getting the operator errors cause your not giving it the correct id.
for instance
if you go to 50cents candyshop you get
javascript:playLAUNCHVideo(16235274)
so if your script is named launch.sh
you would do sh launch.sh 16235274
and it will play  :confused:

---

### Post by Pablo928 on 2005-05-08
There is an extension for Firefox that works for me with mplayer plugin called "play launch".

---

### Post by H.E. Pennypacker on 2006-09-16
Why do all this when you can follow the following instructions:

1.  Install Greasemonkey.
2.  Install [http://www.pooyak.com/p/pklaunch/pklaunch-0.8.1.user.js](http://www.pooyak.com/p/pklaunch/pklaunch-0.8.1.user.js).  Just click on the link, and Greasemonkey will know what to do, and will ask you if you want to install it.  Install it.
3.  Go to Launch.com, and watch any video.

I am telling Yahoo to play nice or people will look for alternatives.  They should be flattered we're using their website.

Thanks go to this website:

[http://buhsnarf.net/wordpress/2006/01/06/howto-play-launchcom-music-videos-in-firefox/](http://buhsnarf.net/wordpress/2006/01/06/howto-play-launchcom-music-videos-in-firefox/)

Note these instructions may only work for certain version of Firefox.  Try anyway.

---

