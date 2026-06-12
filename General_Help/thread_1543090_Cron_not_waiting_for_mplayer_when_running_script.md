---
title: "Cron not waiting for mplayer when running script"
date: 2010-07-31
forum: General Help
---

### Post by confusador on 2010-07-31
This is going to be a long one, so I appreciate you looking at it. I have a feeling, too, that it's going to be something simple in the end, but I'll be darned if I can find it.  I'm not sure if this behavior is Ubuntu specific, but I thought this might be a good place to start.  I'm currently running Karmic, though again I don't think it matters.

I'm trying to get some experience with cron, since it seems like a handy thing to know.  Putting together a script to play some chimes seemed like a simple way to do that.  I've since fallen into (and crawled out of) a bunch of pitfalls, and will never make assumptions about the running environment again!  This last piece is killing me, though.  Whatever I do, I can't seem to get cron to wait for mplayer to finish while it's running the script.

Here's what I've got:

```
#! /bin/bash

### depends on: libnotify-bin mplayer
### DISPLAY=:0.0 must be in crontab

TIME=$(date +'%R, %a %e %b')
#MIN=$(date +'%M')
#HR=$(date +'%I')
MIN=00
HR=12
echo "Time set to $HR:$MIN" >> ~/scripts/chimes.log  # for troubleshooting

notify-send "$TIME" "(from chimes)"

case $MIN in 
15) mplayer -volume 40 -endpos 3.7 ~/scripts/chimes.ogg;;
30) mplayer -volume 40 -endpos 7.2 ~/scripts/chimes.ogg;;   
45) mplayer -volume 40 -endpos 10.4 ~/scripts/chimes.ogg;;
00) mplayer -volume 40 ~/scripts/chimes.ogg;;
*) mplayer -volume 40 ~/scripts/toll2.ogg
esac

if [ $MIN = 00 ]; then
echo -n "Tolling: " >> ~/scripts/chimes.log #logging
i=0
while [ $[$HR-1] -gt $i ]; do
	let i=$i+1
	mplayer -volume 40 ~/scripts/toll1.ogg
	NOW=$(date +'%S'); echo -n "toll$NOW, " >> ~/scripts/chimes.log #logging
done
mplayer -volume 40 ~/scripts/toll2.ogg
echo "toll." >> ~/scripts/chimes.log #logging
fi

#more troubleshooting
if [ $PATH = /usr/bin:/bin ]; then
FROM='from cron'
else
FROM='manually'
fi
echo -e "Run at $TIME, $FROM" >> ~/scripts/chimes.log

#if [ $PATH = /usr/bin:/bin ]; then
#sleep 30
#fi

NOW=$(date)
echo -e "End at $NOW.\n" >> ~/scripts/chimes.log
```

And since more than half of the script is debugging, it'd be helpful to see the output.  You'll notice I've set it to always ring noon, which is the worst case scenario.  Here's what I get when I run it from the terminal:
```
Time set to 12:00
Tolling: toll43, toll47, toll50, toll53, toll56, toll59, toll02, toll05, toll08, toll11, toll14, toll.
Run at 12:45, Sat 31 Jul, manually
End at Sat Jul 31 12:46:21 CDT 2010.

```
Nice 2.5 second pauses while it waits for mplayer to play the chime.  Takes about a minute.  Here's what cron puts out:
```
Time set to 12:00
Tolling: toll06, toll06, toll06, toll06, toll06, toll06, toll06, toll06, toll06, toll06, toll06, toll.
Run at 12:45, Sat 31 Jul, from cron
End at Sat Jul 31 12:45:06 CDT 2010.
```
The whole thing is done in 6 seconds!  Now, I know that it is able to invoke mplayer and find the audio files, because I get about 4 seconds of sound.  For some reason, though, it doesn't wait to finish playing each file before moving on.

You can see where I initially though adding a sleep command would help, I've also tried adding nohup to the crontab and the case statements, and I've tried adding '& echo "foo"' to the case statements.

Any thoughts would be greatly appreciated.

---

### Post by prodigy_ on 2010-07-31
IIRC, expressions that you want to be evaluated by **let** builtin should be double-quoted: ```
let "<expression>"
``` or you can use double parentheses like everyone does: ```
(( <expression> ))
```
I'm absolutely not sure that this is the culprit, but your script definitely fails somewhere around that part...

---

Also try to insert something like: ```
set -x
exec 2>~/scripts/chimes-trace.log

``` in the beginning of your script. The log will show you what actually happens withing the while loop.

---

### Post by confusador on 2010-07-31
Good catch on the let.  I... don't actually know how that was working.  But it was, since it counted correctly even when run by cron.  One of the deep mysteries, I guess.

I put the trace in there, and it's marvelously helpful.  It is failing, as I suspected, in the mplayer called by the case statements.  When run from the terminal (which works as I intend), it returns:

```
+ case $MIN in
+ mplayer -volume 40 /home/confusador/scripts/chimes.ogg
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
+ '[' 00 = 00 ']'
```
A couple of errors, but with pulse it's not surprising, and they're not fatal.  When run from cron it does:
```
+ mplayer -volume 40 /home/confusador/scripts/chimes.ogg
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440


MPlayer interrupted by signal 13 in module: play_audio
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
+ '[' 00 = 00 ']'
```

The rest of the mplayers are invoked but have no output.
```
+ let i=1
+ mplayer -volume 40 /home/confusador/scripts/toll1.ogg
++ date +%S
```

I haven't been able to find anything on signal 13, but I have to assume it indicates script termination.

Thanks again for the tips!

---

### Post by prodigy_ on 2010-07-31
> **confusador said:**
> MPlayer interrupted by signal 13 in module: play_audio
Hmm, interesting. There's a possible workaround for this: try to add ```
>/dev/null 2>&1
``` to the crontab line that runs your script.

---

Also > ```
+ let i=1
``` doesn't look right. It should be, for example: ```
+ let i=0+1
```
So I'd suggest to replace your while loop with something like: ```
for ((i=0;i<$[${HR}-1];i++))
do
	mplayer -really-quiet -volume 40 ~/scripts/toll1.ogg
	NOW=$(date +'%S'); echo -n "toll$NOW, " >> ~/scripts/chimes.log #logging
done
```

---

### Post by confusador on 2010-07-31
> **prodigy_ said:**
> try to add **>/dev/null 2>&1** to the crontab line that runs your script.

Fascinating.  I don't yet understand why that would matter, but it worked!  I'll have to look into what cron does with its output by default.

I am much obliged for the assistance.

---

