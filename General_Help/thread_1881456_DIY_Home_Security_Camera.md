---
title: "DIY Home Security Camera"
date: 2011-11-15
forum: General Help
---

### Post by juicyoner on 2011-11-15
Hello Ubuntu community!

I have a little pet project that I'd like to get feedback on. I suspect this is something many others have done. I'd like to set up a web cam to be used as a security camera for my house. The *ideal* situation would feature:

1. motion detection
2. night vision
3. wifi (no usb cords)
4. battery powered (no powercords)

I'd like to have this rigged up to save all images to the cloud (~/dropbox or ubuntu one).

An even *more* awesome solution would be able to save images directly to the cloud without having to connect to a desktop/server in my house. I suspect this would be a lot more difficult, so I'm just throwing it out there.

Any suggestions for web cam models? 
Software packages? 

Thanks~!

---

### Post by rbc on 2011-11-15
Can't help with hardware suggestions, but for software, have a look at Motion and Zoneminder. I think they're both in the repos. I haven't played with either application in a while. I could never get Zoneminder to work, but I was using a very low spec computer, which might have contibuted to the issues

---

### Post by juicyoner on 2011-11-16
Can anyone suggest a specific brand/model of webcam?

---

### Post by wymand on 2011-11-19
> **juicyoner said:**
> Can anyone suggest a specific brand/model of webcam?
 I have been playing with a Foscam F18918W Wireless camera with a web interface and IR (no IR filter so all images show the IR spectrum)
 
The camera firmware is Linix.  The motion detection shoots too many frames imnsho and like most cameras sees wind as movement.  The best thing is it is cheap no make that inexpensive (Chinese made) Their UPnP isnt complete yet.  It has pan/tilt and you can write your own interface [http://home.comcast.net/~wymand/cam1.htm](http://home.comcast.net/~wymand/cam1.htm)

---

### Post by wymand on 2011-11-19
:( Forgot to mention my camera page is not streaming video but updates on a timer

---

### Post by sepo on 2011-12-27
Some time ago I tried motion:
[http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideGettingItRunning](http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideGettingItRunning)

My 2 cents: 
I configured motion to activate under motion detection :o
The pc was usb-connected to a webcam. When motion detected some movements it started grabbing pictures into a folder...for my convenience the pics were all with same name (yes, they were overwritten), but this is not necessary. It can also grab videos (using ffmpeg).

It also expose an http interface to config it ([http://localhost:8080](http://localhost:8080)) and one to see the camera's images ([http://localhost:8081](http://localhost:8081)) using the 'Content-type: multipart/x-mixed-replace' to emulate the streaming over a normal browser (but this is another story :) )

---

### Post by richiegriffin on 2012-03-17
If you don't know how to set-up Zoneminder with the PHP, MySQL, and whatever Kernel is required, I'd say don't bother trying.

I really made an effort to get this installed but Zoneminder has such poor quality documentation that relies heavily on a community of advanced users. The guides assume you already have advanced knowledge of Linux and are littered with broken links and spelling errors.

I've finally decided that its not worth sitting around trying to tweak this ****. I'm going to create a second partition for Windows 7 Ultimate and just run an application thru there.

---

