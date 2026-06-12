---
title: "WakeUp Alarmclock Wont Work"
date: 2012-08-13
forum: General Help
---

### Post by Zukaro on 2012-08-13
I've installed WakeUp (an alarmclock which can talk to you and tell you information) but when it gets to the time it's supposed to go off at it doesn't.  I've used it before and it used to work, but now it doesn't.  It also tells me there's an error with the crontimes or something like that when I try to set it.

I don't have it set to boot my computer as I just leave my computer on 24/7, but I've tried using the option to see if that could make a difference (I get the error when I do that however).  When I don't set it like that it gives no error but the alarm never goes off.

Does anyone know how to fix this?  I'm using Ubuntu 12.04.

---

### Post by marlow59 on 2012-08-13
this is a problem specific to the application, you may give a look to the available documentation in their webpage.

---

### Post by Habitual on 2012-08-13
terminal >
```
crontab -l 
```

output please.

---

### Post by Zukaro on 2012-08-13
> **Habitual said:**
> terminal >
```
crontab -l 
```output please.

For both root and my account it says there's no crontab.


I've also tried patching WakeUp with the patch found here: [https://bugs.launchpad.net/wakeup/+bug/990946](https://bugs.launchpad.net/wakeup/+bug/990946)
I get a new error: "Unable to set all alarms. Check time preferences."

---

### Post by Zukaro on 2012-08-14
Does anyone know of any possible fixes for this?  I've tried the patch from the bug report but it doesn't work.

---

### Post by sienile on 2012-08-14
I don't know how to fix this, but I have a suggestion for until you figure it out.

Kalarm, available in USC, is a feature packed alarm program that can run programs and display notes in addition to alarms. Until you get WakeUp working, it would be a decent alternative.

---

### Post by Zukaro on 2012-08-14
Really all I need is a way to play music and speech at a certain time each day.  I know how to make my computer talk at certain times using a crontab and a shell script but I don't know how to play music using a terminal command.

Would Kalarm be able to run a shell script and then play music afterwards?

Or does anyone know how to play music using the terminal?
(either would be helpful)

Which I just figured out :V
*should be able to get it all working now* :P :3

---

### Post by sienile on 2012-08-14
Yes, Kalarm can run terminal commands and scripts.

---

### Post by Zukaro on 2012-08-14
k; thanks.

I've gotten it all working now however.

For those who want to do something similar here's what it all looks like:

```
echo "Good morning.  The time is $(date +%R), this is a 24 hour format.  Today's date is $(date +%A) $(date +%B) $(date +%d)." | festival --tts

mplayer "/home/zukaro/Music/House (feat. Nick Nikon).mp3"
```The reason I used a 24hour format is because when I use the 12 hour format festival says the zero in front of the number (so if it's 9:00am festival will say 09hours).  It also doesn't pronounce am as A and then an M, it says it as one word.

As for the crontab:

```
30 7 * * * /home/zukaro/Documents/Alarm/Alarm.sh
```

---

### Post by ububot on 2012-10-04
This bug in wakeup has been fixed in version 1.3, available in the quantal repositories or at [https://launchpad.net/ubuntu/+source/wakeup/1.3-0ubuntu2/+build/3875909/+files/wakeup_1.3-0ubuntu2_all.deb](https://launchpad.net/ubuntu/+source/wakeup/1.3-0ubuntu2/+build/3875909/+files/wakeup_1.3-0ubuntu2_all.deb)

---

