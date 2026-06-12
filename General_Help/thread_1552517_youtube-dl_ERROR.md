---
title: "youtube-dl ERROR"
date: 2010-08-13
forum: General Help
---

### Post by linuxformat on 2010-08-13
Hi All 

This error comes when download from youtube-dl

solom@solom-desktop:~$ youtube-dl [http://www.youtube.com/watch?v=Sb_YmcZ6R1w](http://www.youtube.com/watch?v=Sb_YmcZ6R1w)
[youtube] Setting language
[youtube] Sb_YmcZ6R1w: Downloading video info webpage
[youtube] Sb_YmcZ6R1w: Extracting video information
ERROR: format not available for video
solom@solom-desktop:~$ 


Is there another program or solution to this problem

Thanks

---

### Post by 0004tom on 2010-08-13
Try 

youtube-dl -f 18 [http://www.youtube.com/watch?v=Sb_YmcZ6R1w](http://www.youtube.com/watch?v=Sb_YmcZ6R1w)

---

### Post by linuxformat on 2010-08-13
The same problem

---

### Post by earthpigg on 2010-08-13
hi,

i dont have an alternative program to do this, but i can tell you a way that doesn't rely on any third party program.

1) go to the desired youtube video in firefox, press pause. wait for the little red bar to move all the way across, indicating that the video is fully downloaded to firefox's temporary folder.

2) leave that tab in firefox open. go to the temporary folder in nautilus. ~/.mozilla/firefox/[something].default/cache (once you find it, it isn't a horrible idea to bookmark it in nautilus so it will appear in the 'places' menu on your top gnome panel)

3) sort by date modified, with most recent at top.

4) find the one that has it's 'type' listed as 'shockwave flash file'.

5) drag and drop it to wherever you want the video to be saved.


optional: use ffmpeg to strip the audio and create an mp3. install ffmpeg, then:

```
ffmpeg -i flashfilename mp3filename.mp3
```


you need written permission from Google for this not to be a violation of their EULA, the same as youtube-dl. i will assume you have that. ;)

---

### Post by andrew.46 on 2010-08-14
Hi linuxformat,

If it is legal/appropriate for you to download this particular video try a newer version:

```

sudo apt-get remove youtube-dl
sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2010.08.04/youtube-dl -O /usr/local/bin/youtube-dl
sudo chmod +x /usr/local/bin/youtube-dl

```

The youtube-dl people tend to update every month or so and this version certainly worked for me:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]youtube-dl -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=Sb_YmcZ6R1w'[/COLOR]**
[youtube] Setting language
[youtube] Sb_YmcZ6R1w: Downloading video webpage
[youtube] Sb_YmcZ6R1w: Downloading video info webpage
[youtube] Sb_YmcZ6R1w: Extracting video information
[download] Destination: Best_Romantic_Relax_Music_ever.flv
[download] 100.0% of 8.13M at   33.87k/s ETA 00:00 

```

Have a good read of the YouTube copyright pages though, I am not a lawyer and cannot really comment on this sort of thing...

Andrew

---

### Post by linuxformat on 2010-08-18
I found these additions in Mozilla Fox



[https://addons.mozilla.org/en-US/firefox/addon/11047/](https://addons.mozilla.org/en-US/firefox/addon/11047/)


[https://addons.mozilla.org/ar/firefox/addon/13990/](https://addons.mozilla.org/ar/firefox/addon/13990/)



Thank you very much


Regards

---

### Post by barney385 on 2010-08-25
thanks

---

### Post by johanesbrain on 2010-11-13
thanks works for me

---

### Post by Mr.Dee on 2011-04-17
you must update youtube-dl twice, kinda weird, I know.

sudo youtube-dl -U
sudo youtube-dl -U

---

### Post by brakbox on 2011-05-05
> **Mr.Dee said:**
> you must update youtube-dl twice, kinda weird, I know.

sudo youtube-dl -U
sudo youtube-dl -U

Nice one!:popcorn:

---

### Post by DaVoid_73 on 2011-05-30
thanks made my day!:p

---

### Post by littlepear on 2011-07-10
Thanks, Mr. Dee!:KS

---

### Post by xile_ on 2011-10-30
> **Mr.Dee said:**
> you must update youtube-dl twice, kinda weird, I know.

sudo youtube-dl -U
sudo youtube-dl -U

Worked for me.
Seems like the first update gets the HEAD github version, whereas the second update gets a different version..

As you said yourself, kinda odd :-)

---

