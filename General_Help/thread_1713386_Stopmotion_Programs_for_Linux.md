---
title: "Stopmotion Programs for Linux?"
date: 2011-03-24
forum: General Help
---

### Post by Da CalebMan on 2011-03-24
Hey Guys, 

Just wanted to get a little advice on some stop-motion programs for Linux. I really need one for an animation project coming up and so far the ones I've tried haven't worked the way they should. Any advice on new programs or help with existing ones would be highly appreciated.

I've tried 'Stopmotion' the one available in default repos, but when I added the camera (Logitech Quickcam 6400?) it simply said, "Pre-poll command does not exist."

I tried Frameworks, which besides the annoying compiling, seemed to be a better candidate, but when I navigated to the camera I simply got a large screen full of static and extremely slow fps.

My webcam works fine in Cheese. Am I missing a specific driver perhaps? Or are all the stopmotion programs out-dated?

Please help me out ...

---

### Post by tupfzom on 2011-03-24
If your webcam works with some other application, you can most likely make it work with stopmotion, but it needs some manual adjustment.  First you have to find a command line program that can capture from your webcam.  Candidates I know of are vgrabbj, dvgrab, videodog, fswebcam and gphoto2.  There might be others.  I had to invest some time to work out what works best with my cameras.  I tried two different ones with stopmotion and came up with two different solutions:

```

fswebcam -d /dev/video0 --rotate 180 myimage.jpg

```
```

gphoto2 --capture-image-and-download --force-overwrite --filename myimage.jpg

```

If you found something that works on the console, in stopmotion you can click Settings => Configure Stopmotion => Video Import => Add.  Give it a reasonable name and description and paste the working command in the Pre-poll command field, replacing the video device (e.g. /dev/video0) with $VIDEODEVICE and the filename (e.g. myimage.jpg) with $IMAGEFILE.  For example:

```

fswebcam -d $VIDEODEVICE --rotate 180 $IMAGEFILE

```
```

gphoto2 --capture-image-and-download --force-overwrite --filename $IMAGEFILE

```

Good luck!
Thomas W.

---

### Post by Da CalebMan on 2011-03-24
Hey Thanks, It worked! Well, somewhat.
Gphoto2 didn't recognise camera model, but Fswebcam found it pretty easily. The only problem though, was it was extremely sluggish (about 3-4 seconds before frame change) and there was quite some tearing.

I'm pretty sure a lot of that lag and bad quality is due to my bad webcam. Would it be possible to use a digital camera? More specifically, a Panasonic Lumix (DCM-FS3)?

---

### Post by tupfzom on 2011-03-24
Can the camera be controlled remotely?  Did it come with capturing software (for Win/Mac)?  If not, it's unlikely.

---

### Post by Da CalebMan on 2011-03-25
Hmmm, Not a chance.

I did find my old Sony Digital Handycam though. It uses tape so It's pretty old, but it does have a usb/dv output. Any way that this might work? I googled it and couldn't find much. I'm guessing not many people use these any more.

It's a DCR-TRV19E. Just so you know. 

Only problem so far is, besides the ol' yellow video out jack, I can't find a cable in my house that'll fit it. Sure I've seen them before, I just don't know where they've gone ...

---

### Post by Da CalebMan on 2011-03-26
Hey, I got it working with Kino! What does Kino use to grab video? Would it be possible to use it in Stopmotion? Or is there a way I can animate through Kino?

Forgive me if my questions are silly ...
Thanks!

---

### Post by tupfzom on 2011-03-27
It uses dvgrab, but I've no idea how to use it.  If you find out, I'd be interested to hear how it works.

---

