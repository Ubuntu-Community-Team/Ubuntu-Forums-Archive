---
title: "mp3blaster doesn't work with cron"
date: 2010-03-02
forum: General Help
---

### Post by auvinen on 2010-03-02
Hi! 

I have a problem with mp3blaster.

I want cron to act as an alarm clock: first, it plays an mp3 file and then it runs the speech synthesizer festival which tells me to get up and do stuff.

Now, mp3blaster doesn't do anything when I run it from cron, but festival works without problems.

I've found some possible causes for mp3blaster not working through cron. Someone suggested that pulseaudio is not started. This shouldn't be the problem for me, since I don't even have pulseaudio installed, and festival is playing sound without problems...

I don't know what I should do to make it work. 

Here is my script - runalarm.sh:
```

#!/bin/sh

mp3blaster /root/speechalarmclock/rachels_song.ogg

# Write a file containing the time readout
deit=`date +%u%a`
echo "The time is" > /root/speechalarmclock/time
date +%H:%M >> /root/speechalarmclock/time

# Read the time and the wakeup text
festival --tts /root/speechalarmclock/time
festival --tts /root/speechalarmclock/wakeup

```

I don't want to include the wakeup text here since it contains profanity :D

The mp3 player could be another one too. mp3blaster happens to be the  only player I know that is easy to run from console, like this  "mp3blaster goodsong.mp3", without and playlist creation or other stuff  like that. 

I can run the runalarm.sh from SSH console and it works fine, the mp3 starts playing and festival speaks after that. When run from cron, festival starts speaking right away and no mp3 is heard.

---

### Post by BUSHYBOB on 2010-03-02
You might need to add this 

env DISPLAY=:0

to your cron command

---

### Post by auvinen on 2010-03-02
so if it was:

 00 07  *    *   *   /root/speechalarmclock/runalarm.sh 

how should i put it? like this?

 00 07  *    *   *  env DISPLAY=:0 /root/speechalarmclock/runalarm.sh

---

### Post by BUSHYBOB on 2010-03-02
Yes.

---

### Post by auvinen on 2010-03-02
It didn't work...
I also see no errors in cron's log to /var/log/syslog.

I have no desktop installed on this machine, it's a server. Maybe that has to do with it?

My crontab is now like this:
  00 7  *    *   1-5    env DISPLAY=:0 /root/speechalarmclock/runalarm.sh

---

### Post by d3v1150m471c on 2010-03-02
as far as I know, cron cannot launch applications. Don't quote me on that.

---

### Post by auvinen on 2010-03-02
[http://www.kyle.mathews2000.com/node/18](http://www.kyle.mathews2000.com/node/18)

For example here is a guide how to launch GUI applications.
I tried also like that: export DISPLAY=:0 && command
it didn't work for me.

I don't need a GUI anyway since mp3blaster is text mode... I just want it to play something. Any mp3 player would work.

And I don't think I even have a display since I don't have a desktop installed...

---

### Post by auvinen on 2010-03-02
Oh yeah! Solved my problem.

I don't know what mp3blaster has against cron, but i tried mpg123 with an MP3 file and it worked from cron. 

Only thing is that mpg123 doesn't play OGG :(

---

