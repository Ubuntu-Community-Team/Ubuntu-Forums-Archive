---
title: "is this crontab correct?"
date: 2006-04-17
forum: General Help
---

### Post by ice60 on 2006-04-17
hi, i found a cron i want to run from the ubuntu blog [here](http://ubuntu.wordpress.com/tag/commands/), this is the command i want to use -
```
find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```
i want to run it on Mon and Tues at 16:55, 17:55 and 18:55. is this anywhere near what i need to put in to the crontab? i'm scared of running something none stop :( 
```
55 16-18  * * mon,tue find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```
and i'm going to put it here -
```
crontab -e
```
i just ran crontab -e and because i haven't already made it it's running from a temp directory, if i save it will it save to vvv ??
```
var/spool/cron/crontabs
```
thanks.

---

### Post by ice60 on 2006-04-18
i think i'm going to change the cron and only run it once! i'm going to install anacron so it can run any missed crons. so i think i want to run this -
```
55 16  * * mon find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```
that should run the cron once at 16:55 every Monday, but because i'm going to use anacron i want to run it twice a month now - at that time then every two weeks onward. i'll try and work it out tomorrow. if anyone knows what to do that would be great :)

---

