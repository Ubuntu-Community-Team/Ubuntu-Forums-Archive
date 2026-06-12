---
title: "Cron job stops early"
date: 2010-06-20
forum: General Help
---

### Post by duke.tim on 2010-06-20
I have created a cron job to play audio reminders daily. The cron job starts and plays 8 seconds and then stops.
```
crontab -e (vi/m)
22 16 * * * /usr/bin/mplayer ~/reminders/*.wav
```

I need it just to keep playing until all the *.wav files have been played

---

### Post by MooPi on 2010-06-20
I do the same thing but as an alarm to wake every work day promptly at 7 am.
I use ogg or mp3 file without issue.
```
# m h  dom mon dow   command
 00 07  *   *   *    mpg123 ~/music/rainbow.mp3
```You can try to convert your wav files to mp3. I've done it but I'm rusty on the conversion code.
Might be something like this: > lame -V4 in.wav out.mp3  

---

### Post by duke.tim on 2010-06-20
I just tried *.ogg and *.mp3 neither of them work. could it be mplayer that is causing the problem....the commands work in the shell without problem.

---

### Post by MooPi on 2010-06-20
try ogg123 or mpg123

---

### Post by duke.tim on 2010-06-20
ogg123 and mpg123 both work. wonder why mplayer won't...well i'm happy it works thanks for the help.:p

---

