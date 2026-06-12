---
title: "FLV Download helper speed question"
date: 2011-12-11
forum: General Help
---

### Post by Gatorade on 2011-12-11
Anyone here use FLV download helper?

I was just wondering why it always slow down after a few seconds. I've noticed that if I pause and restart it every time it starts to slow down the video downloads a lot faster, but that's a pain to keep stop/starting it.

Is there any settings that can be adjusted to maintain a good download speed?

---

### Post by oldtimer7777 on 2011-12-11
> **Gatorade said:**
> Anyone here use FLV download helper?

I was just wondering why it always slow down after a few seconds. I've noticed that if I pause and restart it every time it starts to slow down the video downloads a lot faster, but that's a pain to keep stop/starting it.

Is there any settings that can be adjusted to maintain a good download speed?

There is one listed about 1/3rd the way down the new user checklist under mozilla plugins

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by Gatorade on 2011-12-12
hey oldtimer , 

thanks for that link , installed netvideo hunter and it works much faster.

---

### Post by oldtimer7777 on 2011-12-12
> **Gatorade said:**
> hey oldtimer , 

thanks for that link , installed netvideo hunter and it works much faster.

It is pretty awesome. You are welcome. Don't forget to mark this thread as solved please when you are done here. Just click Thread Tools way up above at the start of your thread. Thanks! Live long and prosper.

---

### Post by Gatorade on 2011-12-12
I was just testing out netvideohunter on another video and I just realized that it only downloads in Mp4 format, is there a reason for this? 

is there any option to save the file as flv?

---

### Post by Bobhuber on 2011-12-12
> **Gatorade said:**
> I was just testing out netvideohunter on another video and I just realized that it only downloads in Mp4 format, is there a reason for this? 

is there any option to save the file as flv?
I just installed this and it saved the video in .flv format. 
You can easily convert a video if needed using ffmpeg

---

### Post by Gatorade on 2011-12-12
yeah, I just tried it again with a couple of other videos , some saved as flv , and others saved as mp4, but it doesn't give you the option to choose.

I know I could convert it , but I was hoping I wouldn't need to , I was trying to save it directly to the format I wanted.

I'm going to continue to try different videos and see how it goes.

---

### Post by oldtimer7777 on 2011-12-12
Nope, I just use Winff instead to convert stuff around..

```
sudo apt-get install winff
```and then use winff to generate the command line code you need to cut and paste and do it from the command line.  Much much easier and way more flexible too.  It works for all media files.. flv.. mp4..  you name it!  :)

And if you need to do a whole bunch of files, you can take the commands generated and make your own bash script file to do batches of files. More fun that way too.

Enjoy.

> **Gatorade said:**
> yeah, I just tried it again with a couple of other videos , some saved as flv , and others saved as mp4, but it doesn't give you the option to choose.

I know I could convert it , but I was hoping I wouldn't need to , I was trying to save it directly to the format I wanted.

I'm going to continue to try different videos and see how it goes.

---

### Post by Gatorade on 2011-12-13
thanks for the tips oldtimer, I'll keep it in mind.

I've never heard of a bash file but I'll look into it.

---

