---
title: "Video Surveillance?"
date: 2011-06-02
forum: General Help
---

### Post by Roasted on 2011-06-02
So I decided to hook up a wireless IP based TRENDnet camera to my network. It works great. I found the exact URL to check out the MJPEG stream and it's very clear and very solid.

So I began to use ZoneMinder, a Linux based solution for setting up home surveillance with any type of camera. Okay, great. So I checked out its features and I was pleasantly surprised it had motion detection and all sorts of other features.

However, the honeymoon was quickly over when I began to ran into problems quite often. Now, out of no where, I lost my playback ability on my motion detected events. 

To say the least, I'm a little frustrated with ZoneMinder. But that got me wondering. ZoneMinder doesn't record video feeds. It just records a ton of JPG files and renders them for playback (well, sometimes at least, in my case). So I got to wondering, is there a way I can set up an application within Ubuntu 11.04 to record (based on motion detection) my MJPEG stream? If there's a way to do that, I could probably work around these issues and still have some sort of video surveillance set up on a Linux box. What do you guys think? Is this possible?

EDIT - so it seems the latest version of ZoneMinder that was released a matter of weeks ago has solved nearly all of my issues. I'm going to continue using it, however I am more than open to other ideas if anybody would like to clue me in.

---

### Post by SteveDee on 2011-06-02
> **Roasted said:**
> ...I'm going to continue using it, however I am more than open to other ideas if anybody would like to clue me in....

Take a look at "motion" here: [http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuide](http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuide)

Motion also captures jpeg images and stitches them together to create video. It can be configured to save pictures or video or both.

It has its own web server, so you can use Firefox to remotely view live video.

It has a loop-back mode so you can connect another application to the same video stream.

Motion does not have a gui interface. You setup via a config file which can also be adjusted via a web browser.

---

### Post by Roasted on 2011-06-03
> **SteveDee said:**
> Take a look at "motion" here: [http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuide](http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuide)

Motion also captures jpeg images and stitches them together to create video. It can be configured to save pictures or video or both.

It has its own web server, so you can use Firefox to remotely view live video.

It has a loop-back mode so you can connect another application to the same video stream.

Motion does not have a gui interface. You setup via a config file which can also be adjusted via a web browser.

Sounds like a nice application. Although, now that I have ZoneMinder behaving nicely (which wasn't that hard, I just had to buckle down and RTFM) I may use that for when-I'm-away surveillance, and for real-time streaming, I get a NICE feed from the direct mjpeg stream from the camera. I may end up using that in the long run.

Is there solid documentation for Motion? I think I'd like to try it out for the learning experience. Sounds cool you can stitch jpg's together to make a video.

---

### Post by no2498 on 2011-06-03
wxcam says it has motion detection 
i have never used it myself

[http://linux.softpedia.com/get/Multimedia/Video/wxCam-29612.shtml](http://linux.softpedia.com/get/Multimedia/Video/wxCam-29612.shtml)

---

