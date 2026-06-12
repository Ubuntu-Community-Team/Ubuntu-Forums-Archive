---
title: "pausable uploader for huge files?"
date: 2011-09-18
forum: General Help
---

### Post by shelbyvision on 2011-09-18
I made a 55 minute video, .mp4, that I want to upload to my website or wherever (not Youtube, they won't accept videos that long). Using my website server's upload is out of the question, since it can't be paused or re-started, and it's about a 8-12 hour upload from here. I tried Veoh (it works with WINE), and started the upload, and got it about 1/3 done, and then paused it, then shut down the compputer for the night (probably a big mistake). Next morning, it won't work, keeps telling me I need to download Adobe Flash player (which I already have), and keeps opening multiple instances of itself, which I can only get rid of with the force-quit tool. Is there any application for this purpose that works well with Ubuntu (10.04)?

---

### Post by Lisiano on 2011-09-18
If your website server has SSH you can copy the file using it
```
scp -C file.mp4 username@server.net:/path/to/folder/file.mp4
``` -C just means compression. AFAIK scp automatically resumes if it notices a file on the server.

---

### Post by shelbyvision on 2011-09-18
What is SSH? I don't see it anywhere on my server's control panel.

---

### Post by Lisiano on 2011-09-18
[Wikipedia - Secure Shell (SSH)]("http://en.wikipedia.org/wiki/Secure_Shell")
If you use Website hosting (Not a server, virtual server or a virtual private server) then SSH is not an option. Mind telling what is the Video size? Maybe there is an option to compress it by using a different codec or using better options. Also the codecs.

---

### Post by shelbyvision on 2011-09-18
Yes it's website hosting.
The video size is 890 MB. It's an mp4, originally taken with a Flip video camera, edited with Kino and pieced together in Avidemux, where it got it's final format, which is (I think) the same as it was to start with (at least it has the same file extension). I don't want to compress it in a way that will degrade the quality.

---

### Post by Lisiano on 2011-09-20
By compression I meant a better video codec, for example H.264 (X.264), it can give quite acceptable quality at quite low sizes.
Just run the file with mplayer, it will tell you what codec it uses. If you didn't change the codec in Kino (I have no idea how Kino works) or picked a fat codec as Xvid you might have "made the file big". Re-encoding with H.264/X.264/MPEG-4 AVC might save you some space, also using variable bitrate can not only decrease the size but also bump the quality in some places.
Also if you don't mind using file hosts, you could upload your video to Ubuntu One, Dropbox, Mediafire. Sadly Ubuntu One can't resume (Last time I checked), but Dropbox might, same with MediaFire as long as you don't close the browser (Don't know if hibernation and suspending will work in this case)

---

### Post by shelbyvision on 2011-09-20
Thanks for the suggestions.
Mplayers just says it's MPEG-4. Is there a program you would recommend for re-encoding in the ways you mentioned?
I'll check out dropbox and mediafire.

---

### Post by Lisiano on 2011-09-20
You can easily do the reencoding in Avidemux, on the left bar pick Mpeg-4 AVC and for audio, something like Vorbis maybe. Configure the video codec as you wish, the tooltips should help you if you have questions.
Or if you want to use some other stuff. FFmpeg is a neat tool, sadly I forgot how to encode with it.

---

### Post by jvance492 on 2011-09-20
Sorry if I didn't understand correctly but...

Could FTP be your solution?

If you don't want to re-encode that video for a smaller size, maybe FTP can be a pausible file transfer solution to get it onto your server.

Even a Desktop version of Ubuntu can act as an FTP server. You could upload the video to your server over the coarse of a month if you really wanted to.

Fairly simple installation as well:

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Also dropbox would work if you wanted to pay for it. DropBox only has 2 GB storage Free unless you refer friends up to 8 GB.

DropBox will resume sync, but when your dealing with a single file im not 100% sure if it will start that file over if its half finished. FTP sounds like your best bet to me.

---

### Post by shelbyvision on 2011-09-20
I tried Avidemux again, actually that's what I used to begin with, and I think it's as small as it's going to get, unless I want to make the display size smaller. 
I discovered that I can pause an upload with Filezilla, which is what I have used all along for uploading to my website. I have very slow speed "high speed" internet service, so it's about a 15 hour upload, but since I can pause and resume, it's not a problem. I guess the next problem is if a lot of people want to download the video from my website it might put me over my limit for bandwidth, don't know. 
I guess that since Filezilla does what I was wanting to do, I can call this one solved.

---

