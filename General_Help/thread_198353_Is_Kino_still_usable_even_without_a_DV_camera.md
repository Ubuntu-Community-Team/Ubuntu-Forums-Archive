---
title: "Is Kino still usable even without a DV camera"
date: 2006-06-17
forum: General Help
---

### Post by justin2021 on 2006-06-17
I have been downloading all kinds of video editing tools and none of them worked out right. Cinelerra didnt seem to show .avi files, LiVES sound was WAY out of sync, and avidmux doesnt seem to have anything to import music and sound. I hear Kino is great, but when I try to import .avi files, no such luck. It tells me it needs to be a DV file, then gives me a bunch of windows telling me how it wont import. Is there any way to turn my .avis into DV, then after editing them, back to .avi again?

---

### Post by reclusivemonkey on 2006-06-17
[QUOTE=justin2021]avidmux doesnt seem to have anything to import music and sound.[/QUOTE]

I've not used Avidemux much at all, but you can import music. I recorded a goal from PES4, imported the .avi, then created a WAV of a similar length. I loaded the video, then go to "Audio" and "Main Track". Where it says "Select audio track", choose "External PCM(Wav)" and select your audio track.

You can see the test clip I did here;

[http://www.reclusivemonkey.com/GerrardsRocket.avi](http://www.reclusivemonkey.com/GerrardsRocket.avi)

AFAIK, Kino will only work with digital video files, I'm not aware of how you would convert a regular avi/mpeg to this format.

---

### Post by justin2021 on 2006-06-17
When I click main track it doesn't do anything

---

### Post by reclusivemonkey on 2006-06-17
[QUOTE=justin2021]When I click main track it doesn't do anything[/QUOTE]

Do you have a video file loaded?

---

### Post by william_nbg on 2006-06-24
I've been trying to work out that same problem.

Maybe ffmpeg could convert an avi to a dv, but I'm not sure of the option it'd need.

---

### Post by leetcharmer on 2006-06-24
I'm waiting for Diva.

---

### Post by william_nbg on 2006-06-25
[QUOTE=leetcharmer]I'm waiting for Diva.[/QUOTE]


What is Diva, and how long will you have to wait for it??

---

### Post by reclusivemonkey on 2006-06-25
[QUOTE=william_nbg]What is Diva,[/QUOTE]

[http://diva-project.org/](http://diva-project.org/)

[QUOTE=william_nbg]and how long will you have to wait for it??[/QUOTE]

That's the proverbial "How long is a piece of string?" question...

---

### Post by william_nbg on 2006-06-25
[QUOTE=reclusivemonkey][http://diva-project.org/](http://diva-project.org/)



That's the proverbial "How long is a piece of string?" question...[/QUOTE]


Have you tried to compile one of the beta versions yet??

---

### Post by leetcharmer on 2006-06-25
no, I'm waiting for the errors that say: "crash on launch" to be fixed :D

---

### Post by faintscrawl on 2008-02-07
half the solution? ...

installing ffmpeg somehow gave kino the power to import my mpeg, and convert it to .dv, but it was way out of sync.

---

### Post by faintscrawl on 2008-02-07
i installed mencoder and re-did the import.  now it is synced, but the quality of image (and sound too i think) has decreased.  also it appears to be in the wrong aspect ratio.

---

