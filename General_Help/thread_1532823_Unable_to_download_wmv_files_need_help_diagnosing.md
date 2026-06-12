---
title: "Unable to download wmv files need help diagnosing"
date: 2010-07-17
forum: General Help
---

### Post by sofasurfer on 2010-07-17
If this post would be better placed in another forum, please feel free to move it.
OS=Juanty.
I am not aware of any firewall on my system.
I have never noticed this problem since the beginning of time on my pc, but I am not sure whether or not I have ever viewed a wmv file before.
Until now, I have never had a problem viewing a video file or a stream or with downloading a file. At this time I can view streams, Youtube, video files on my pc, etc.

Here is my particular problem.
At this particular website [http://www.tangsoodoworld.com/reference.htm](http://www.tangsoodoworld.com/reference.htm) there are videos, some of which are wmv format. Here is one of them [http://www.tangsoodoworld.com/reference/One%20Steps%20-%20Freestyle%20-%20Set%201.wmv](http://www.tangsoodoworld.com/reference/One%20Steps%20-%20Freestyle%20-%20Set%201.wmv)

When I click on the link mplayer opens but no video plays. If I right-click on the link and click "save link as" the file appears on my desktop with "0" bytes, in other words it is a empty file.

In a previous thread [http://ubuntuforums.org/showthread.php?t=1528604](http://ubuntuforums.org/showthread.php?t=1528604) a poster stated that the files play fine (post #10). In post #23 a person was able to download the file and send it to me and it played for me. 

Therefore, there is an issue that is preventing me from acquiring a wmv file by download. Can anyone help me diagnose this?

PS. I just found that I am able to view wmv files from another site [http://www.natkd.com/pyong_ahn_forms.htm](http://www.natkd.com/pyong_ahn_forms.htm)

When I click on the link Mplayer opens and the video appears to load but does not play. When I right-click and save file I can click the file and Gnome Player (Totem) using Gstreamer opens and the wmv plays. Do I detect a clue here? How do I make Totem open instead of Mplayer? This might make a video play if it downloads but as stated above, that other website is not even downloading a file.

---

### Post by cariboo on 2010-07-17
I'm running Maverick, but I installed the w64codec from the Medibuntu repositories in order to be able to play wmv files.

---

### Post by sofasurfer on 2010-07-17
Wow! I'm sorry for such a long post :-(

---

### Post by sofasurfer on 2010-07-17
Synaptic says I have w64codecs installed.
My problem is in not being able to download the links on the mentioned website, not playing the videos...I think.

---

### Post by mc4man on 2010-07-17
> I'm running Maverick, but I installed the w64codec from the Medibuntu repositories in order to be able to play wmv files. 

you're getting wmv, wma support thru libavcodec and gstreamer wise thru the plugins (good, bad, ugly, ffmpeg

w64 codecs has 3 codecs, all rm related, pretty much a worthless package

> ls '/home/doug/Desktop/w64codecs_20071007-0medibuntu2_amd64/usr/lib/codecs' 
cook.so  drvc.so  sipr.so



---

### Post by sofasurfer on 2010-07-18
Weather or not I have proper support has nothing to do with the fact that other people can download a file and play it but when I download the file it is empty. That is my problem.

---

### Post by techunit on 2010-07-18
Hi I just tryed opening the wmv in Windows to see if it is even playable and it wouldn't play in windows media player!

---

### Post by hawthornso23 on 2010-07-18
The website uses javascript to stream the video. This isn't just a plain link to a wmv file. I wish websites wouldn't do that, but a lot do. They do it because they don't want it to be easy for you to save the file - they just want you to view it. The website designer probably sees your inability to download the file as a feature not a bug. 

If you can't view the file at all however then there is probably something going wrong with the script. I'd look at the web browser setup to see if there is something maybe stopping this script from running properly. Have you got javascript turned off? Have you got some addons (e.g. noscript) that might be blocking this script from doing its job? That is where I think the problem is located.

I can see the video, but I have to tell noscript to allow it. And it doesn't like being rewound or replayed - I have to reload the page.

---

### Post by sofasurfer on 2010-07-18
Hawthorns.
That is the best explaination I have heard so far. Thanks.
I checked synaptic and noscript is not installed. So I installed it. It made no differance. So I reuninstalled it. 
I consider this case closed. I will chalk it up to a crappy website...although, I did email the site and conplained and they said that the videos played fine for them. I think I will send this thread to them and see if they care enough to fix it.
Thanks.

---

