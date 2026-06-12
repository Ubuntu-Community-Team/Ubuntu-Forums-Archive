---
title: "Toshiba 1Tb external HDD general issue"
date: 2010-01-12
forum: General Help
---

### Post by tje210 on 2010-01-12
I got this 1Tb Toshiba external about a month ago, and recently I started really using it to share lots of media files.  What I've noticed is that it turns itself off after a few minutes of inactivity -- I researched this issue across the internet, and found that it's between 5 and 30 minutes, depending on who's writing about it.

I found a person who posted a DOS batch file, which (i think) continuously accesses the drive as long as the batch file is running.  I'd like to find a way to do that in linux.  could someone point me in the right direction?

i took a few minutes to plan it out... i think i need a loop that will access the drive (or do something to it, at least) once every minute until i close the script.  I'd also like a message box that shows up that says something like "while this is open, your HDD is being accessed".

i did do a little research to try to start this off, but i really don't know what sorts of commands are available for me to use, or really where to start.  it would be cool if someone could either just point me in the right direction, or maybe give me a general template/idea for what to do?  I appreciate any assistance offered.

---

### Post by prshah on 2010-01-12
> **tje210 said:**
> if someone could either just point me in the right direction

I recommend you use cron. your crontab(le) can be set to perform repetitive tasks, such as accessing the directory of the external every 5 mins (example). More details at the man page on cron.

You can edit your cron using ```
crontab -e
``` The add a line similar to ```
# m h  dom mon dow   command
*/15 * * * * access_external.sh
``` The shell script access_external.sh can be anything, for example, a listing of the contents of your external. The above code indicates the script is to be run every 15 mins (*/15), every hour, day, month, day of week.

I can explain more later if you require it. Please post back if you need this.

---

### Post by tje210 on 2010-01-16
thanks for the tip :)  that didn't immediately solve my problem, though... i haven't had time to investigate why.  what i just did, for now, was make a simple loop that would run from the hard drive, that will at least ensure that it's active.  that cron utility is quite useful, though, for a guy like me... i'm always forgetting important things like periodic backups, which crontab makes quite simple.

do you know where i could find the log that keeps track of activity on that drive?  figure i can see what happens around the time that it goes idle and becomes antisocial.  additionally, is there a way i could make the drive thinks it's been reconnected?  for example, maybe disabling that USB port and re-enabling it?  that way if it did go idle, i could just type a quick command instead of having to go out and power cycle the drive.  i did a quick google search of that, but didn't really come up with anything; there's also a thread on the forums here that mentioned the same question but didn't get an answer.

---

