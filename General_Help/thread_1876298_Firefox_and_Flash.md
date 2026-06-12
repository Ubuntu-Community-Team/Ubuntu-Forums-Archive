---
title: "Firefox and Flash"
date: 2011-11-06
forum: General Help
---

### Post by Synoc on 2011-11-06
ok I have a problem, I am trying to download some flash player seminars (not copyrighted) so I can access them offline. Where does Firefox now store those files? if this is all and out simply not to be discussed on this forum, please let me know. I am not in the business of doing things illegally.

---

### Post by llamabr on 2011-11-06
It's not firefox, it's the new flash.  You can downgrade flash, or else:

[http://www.omgubuntu.co.uk/2010/09/saving-flash-videos-in-linux-tmp-no-longer-works/](http://www.omgubuntu.co.uk/2010/09/saving-flash-videos-in-linux-tmp-no-longer-works/)

depending on the fires and the website, it depends on whether this violates their tos, so one never knows whether this forum will object.  etc.

---

### Post by pqwoerituytrueiwoq on 2011-11-06
probably in the cache folder
[FONT=Courier New]nautilus ~/.mozilla/firefox/*.default/Cache/[/FONT]
if it is flash related it could be in here but good luck finding it there 
[FONT=Courier New]tree /proc/$(pgrep -f flashplayer)[/FONT]

if you are looking for a video's location so you can play it with something other fan flash for hardware acceleration i pause the video and run this command (after pausing stitch tabs in firefox to stop flash cpu usage)
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
```

---

### Post by jo4hnc on 2011-11-06
If you're using Firefox, you can use the extension DownloadHelper and designate where you want it to save the video file. I use it on a regular basis and find it to be very useful.

---

### Post by Synoc on 2011-11-06
> **jo4hnc said:**
> If you're using Firefox, you can use the extension DownloadHelper and designate where you want it to save the video file. I use it on a regular basis and find it to be very useful.

This is actually what I was looking for. I did find where firefox keeps the videos, and found the videos. as soon as it finised downloading, it killed the file don't know how,BUT if you activate the file so it CAN'T delete it... so it crashes flash... THEN deletes it... heh

---

### Post by aisdyg87 on 2011-11-11
But is it possible to view (from cache) a partially complete youtube video in firefox ?

I don't get youtube, why waste bandwidth re-downloading from the beginning ? If we really want to we can download the whole file.

---

