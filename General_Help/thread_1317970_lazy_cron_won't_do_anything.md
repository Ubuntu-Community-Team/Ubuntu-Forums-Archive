---
title: "lazy cron won't do anything"
date: 2009-11-07
forum: General Help
---

### Post by ducttapeandzipties on 2009-11-07
Ok my objective is to have my computer start the bit torrent at 2am and kill it or halt the system entiery at 7am, since I am on hughesnet satellite and that is the only time I am not subjected to the 200MB/day limit.

this is what I am doing, please tell me what I am doing wrong or not doing.


1) I type in "sudo crontab -e"

2) I enter my pass and the crontab comes up in nano.

3) I add a string "5 2 * * * /usr/bin/transmission"
to start bit torrent at 2:05am

4) I ctrl+x and save changes

5) nothing happens!

I have tried invoking crontab -e from root and from my user account.  I have tried "transmisson" "usr/bin/transmission" and "halt" with no luck.  I have tried editing the file in gedit, and then rebooting to reload it.  Nothing.  Could someone maybe point me in the right direction?

---

### Post by ducttapeandzipties on 2009-11-25
:popcorn:  I got popcorn for anyone willing to help!

---

### Post by harfa on 2009-11-25
from [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")



GUI Applications

It is possible to run gui applications via cronjobs. This can be done by telling cron which display to use.

00 06 * * * env DISPLAY=:0 gui_appname

The env DISPLAY=:0 portion will tell cron to use the current display (desktop) for the program "gui_appname".

And if you have multiple monitors, don't forget to specify on which one the program is to be run. For example, to run it on the first screen (default screen) use :

00 06 * * * env DISPLAY=:0.0 gui_appname

The env DISPLAY=:0.0 portion will tell cron to use the first screen of the current display for the program "gui_appname".

Note: In Karmic(9.10), you have to enable X ACL for localhost to connect to for GUI applications to work.

 ~$ xhost +local:
non-network local connections being added to access control list
 ~$ xhost
access control enabled, only authorized clients can connect
LOCAL:
...

---

### Post by harfa on 2009-11-25
for the stopping transmission at 7am use "pkill transmission"

---

### Post by crysys on 2009-11-25
There it is. I've been fighting this for a day now and I was leaving out the : at the end of, 

> xhost +local:

You're a lifesaver!

---

### Post by ducttapeandzipties on 2010-02-04
> **harfa said:**
> for the stopping transmission at 7am use "pkill transmission"

Awesome, thanks a lot, specifying the display worked perfectly. In my haste I missed the gui section of the howto. pkill didn't work but It will in terminal if I type  "ps -A" and then "pkill transmission"  I tried adding two more lines to the crontab but no luck.  

Is it possible to halt the system with cron?  That what what I had originally wanted to do but couldn't get that to work so I thought I'd try using kill.

[IMG]http://www.nasa.gov/images/content/49105main_popcorn.jpg[/IMG]

---

### Post by gmargo on 2010-02-04
I like **ktorrent**, which has a bandwidth scheduling mechanism.

---

