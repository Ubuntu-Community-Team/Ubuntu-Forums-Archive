---
title: "MP3 Player Podcast Script ???"
date: 2010-11-22
forum: General Help
---

### Post by Rodney9 on 2010-11-22
Hello,

I would like to copy any new podcasts to my MP3 player from my Gpodder downloads.
I would also like to delete any ones that are 3 days or older on both player and pc.

My player auto mounts as /media/COWON
and 
the podcasts are in the directory AAPodcasts
so it is -

> /media/COWON/AAPodcasts

On my pc they are in -

> /home/lone/gpodder-downloads/LinuxOutlaws
/home/lone/gpodder-downloads/Twit
and so on and so on

Is there some script I could use ?

---

### Post by Rodney9 on 2010-11-22
Please can any one help, I have found commands to delete old files like this one- 

> find /home/lone/gpodder-downloads/* -mtime +3 -exec rm {} \;


But I would still like to make the copying and deleting at both ends, a one off process by some sort of script.

---

