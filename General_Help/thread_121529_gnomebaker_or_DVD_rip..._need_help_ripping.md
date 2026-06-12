---
title: "gnomebaker or DVD rip... need help ripping"
date: 2006-01-25
forum: General Help
---

### Post by njzillest on 2006-01-25
Hi, I need help ripping DVD's. On windows i Used Dvd decryter and Auto GK. I downloaded via synaptic DVD rip and Gnomebaker. What one is better? does any one of them decrypt the RCE protection? Will it give it to me in .vob files? is there any way i can convert it to .AVI? 


My disk drive is able to read DVD's and CD's but it can only burn CD's. All i want to do is rip DVD's to my HD. 


toshiba R/10
512 MB of RAM
1.8 ghz processor over clocked to 2.2 ghz
60 gb hd



thanx for the help,
Adel

---

### Post by endersshadow on 2006-01-25
Okay, I'm going to make one suggestion and one shameless plug.  But at least I'm warning you!!

You can use dvd::rip to rip and encode video pretty easily.  Just open up a New Project, and select your titles, and then rip them.  They're ripped into VOBs 1gb large.  You can head over to the transcode tab, and then transcode them into AVI format.  The problem that I have with dvd::rip is that it takes forever (up to 4 times longer than the video for dual pass encoding).  Not my cup of tea.

My problem was that I wanted to rip my videos for my iPod Video, and I wanted to do it quickly.  So I did some sniffing around, and I found vobcopy and cpdvd, which are command line rippers.  With vobcopy, I can rip to one single VOB file...just phenomonal.  Next, I wanted to encode my videos to the correct format...but faster than the video itself was.  I found ffmpeg did a fantastic job with this (for reference, dvd::rip uses transcode).  So, I made a script that shoved them all together and packaged them in a nice little GUI.  I called it iPod Video Encoder, and you can find it [here](http://ubuntuforums.org/showthread.php?t=114946).  Yesterday, I added support for full sized AVI and MPEG formats to be encoding instead of just videos for the iPod Video and/or PSP.  Okay, there's my shameless plug.

---

### Post by njzillest on 2006-01-25
so you recomend ffmpeg and vob copy because its faster? how slow is dvd rip? how many vob files does DVD rip split the DVD into? 


thanx

---

### Post by endersshadow on 2006-01-25
[QUOTE=njzillest]so you recomend ffmpeg and vob copy because its faster? how slow is dvd rip? how many vob files does DVD rip split the DVD into? 


thanx[/QUOTE]

Vobcopy and dvd::rip rip at about the same rate.  However, ffmpeg transcodes MUCH faster than dvd::rip.  dvd::rip took 4 hours for a 2 hour movie for me...ffmpeg did the same movie in and hour and twenty minutes...not even close.

With dvd::rip, it will rip to VOB files that are 1GB large.  So, if you're trying to rip, say, a 5.5GB video, it will give you 6 VOB files, 5 1GB files and 1 0.5GB file.  If you use vobcopy with the -l flag, it will give you one large file.  The reason that I use vobcopy in conjunction with ffmpeg is because ffmpeg does not support multiple input files (unlike transcode, which dvd::rip uses).

At any rate, the best way to learn is by experimenting :-D

---

### Post by njzillest on 2006-01-25
thanks for the help.. 


but one more question? do both convert the VOB files to AVI? I used Auto GK and dvd decryter. Dvd Decryter ripped 5 1 gig files andi had to use auto gk to make it into a compressed .Avi.... I only was only able to get one movie to work. 

with more than one VOB file using DVD::Rip do i have to input all 6 VOB files into the conversion part (to make it into .AVI) 

thanx for the help i know im a n00b

---

### Post by endersshadow on 2006-01-25
In dvd::rip, all you have to do is go to the transcode tab after ripping, and it will automatically compress the files.

Unfortunately, ffmpeg does not support this feature, so I have to use one large file to do it via vobcopy...

---

### Post by Jeffery Mewtamer on 2006-01-26
Does Ipod video encoder support OGG/Xvid OGM as output?

---

### Post by endersshadow on 2006-01-26
[QUOTE=Jeffery Mewtamer]Does Ipod video encoder support OGG/Xvid OGM as output?[/QUOTE]

You asked, I [delivered](http://ubuntuforums.org/showthread.php?p=642610#post642610).

:-D

---

### Post by Jeffery Mewtamer on 2006-01-26
[QUOTE=endersshadow]You asked, I [delivered](http://ubuntuforums.org/showthread.php?p=642610#post642610).

:-D[/QUOTE]

Thats what I love about the Opensource community. Newer and better software is a daily occurence. I'll go it out right now.

---

### Post by kcallis on 2007-02-15
What is the easiest way to figure out which part of a DVD is the part I need to convert so I just end up with the movie?

---

