---
title: "Should I get a new computer when flash makes my CPU usage go to 100%?"
date: 2010-06-06
forum: General Help
---

### Post by TheNerdAL on 2010-06-06
So my computer is old, I think about 5-10 years old. The CPU speed is 1.8 GHZ and when I play Hulu Desktop it lags, and when Flash is being used, the CPU usage goes to like 99% to 100%. Should I just get a new computer?

I want to watch TV shows that I missed on Hulu Desktop. 

Thanks.

---

### Post by McRat on 2010-06-06
Try a new video card or more ram first.  You can always reuse or return it if you wrong.

---

### Post by philinux on 2010-06-06
Moved to General Help

---

### Post by sdennie on 2010-06-06
Flash will probably take your CPU to 100% regardless of what kind of CPU you have.  It's terrible.  Upgrading your CPU will probably stop the lagging (assuming it CPU based and not network based) but, another (and probably cheaper) option would be to find a non-flash based method of acquiring your media.

---

### Post by no2498 on 2010-06-06
see if this may help it comes from cheese help



    * 5.1.&#8194;The video is sluggish/has a slow response. What can I do?
    * 5.2.&#8194;I have a Mac with iSight and a ATI graphics card, and the colors are weird.
    * 5.3.&#8194;My webcam works with gstreamer, but does not work with Cheese. What's wrong?
    * 5.4.&#8194;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?
    * 5.5.&#8194;Where does Cheese store my photos?
    * 5.6.&#8194;My Quickcam Express doesn't work with Cheese...
    * 5.7.&#8194;Which cameras are supported

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.
    
5.3.&#8195;My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using "gstreamer-properties" mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa. If this still does not work run "cheese --verbose" on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.
    
5.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in "gstreamer-properties". If it works
      there, but not in Cheese, please file a bug report in our 
      
      bug tracker.
    



hope this helps

---

### Post by philinux on 2010-06-06
@no2498 what has chees got to do with a flash problem in a browser?

---

### Post by TheNerdAL on 2010-06-06
> **McRat said:**
> Try a new video card or more ram first.  You can always reuse or return it if you wrong.

I got a better video card and added 1 GB of RAM already.

---

### Post by philinux on 2010-06-06
> **TheNerdAL said:**
> I got a better video card and added 1 GB of RAM already.

Unfortunately flash won't use the gpu at the moment. I wouldn't worry about the cpu usage. Flash is a resource hog.

---

### Post by dtfinch on 2010-06-06
Disabling compiz might help (system->preferences->appearance->visual effects->none) if it's not disabled already, because Flash doesn't try to use gpu acceleration if it detects that compiz is enabled.

What kind of 1.8ghz processor?

---

### Post by TheNerdAL on 2010-06-06
> **philinux said:**
> Unfortunately flash won't use the gpu at the moment. I wouldn't worry about the cpu usage. Flash is a resource hog.

Well what do I do? :(

---

### Post by sdennie on 2010-06-06
Verify the lag is coming from the CPU (like I said, flash will peg any CPU to 100%) and if it is buy a new CPU.  Or, find another way to get your flash content.  You may be able to sign up for HTML5 support on youtube.  And, you can probably find other methods to get the rest of your content.

---

### Post by philinux on 2010-06-06
> **TheNerdAL said:**
> Well what do I do? :(

Flash hits my dual core amd 64 5200+. Temps are ok so I ignore it.

---

### Post by nemilar on 2010-06-06
Flash is something Linux doesn't have "right" yet.  It is proprietary from Adobe, though, so annoyances should be directed there.  I for one hope that Flash becomes obsolete in favor of HTML5, which is open, and the support apps will (and thus, performance) will be done by Mozilla, Google, etc...

I have a couple of less-powerful machines that run flash fine in Windows, but once you move to Linux it pegs the CPU at 90%+ and occasionally becomes unusable.  It's no fun.  The only machine I have that is able to handle flash comfortably is my core 2 duo box, and even then, when I run flash the fan kicks up full gear and it starts pumping out heat (it's a laptop).

Let's all just hope flash gets killed off quickly in favor of HTML 5....

---

### Post by konsta82 on 2010-06-06
That is software problem. Flash is crap , but you still must be able to run it on your engine.
Flash works good enough on my friends 1 ghz & 512 ram with 9.10

---

### Post by no2498 on 2010-06-06
flash uses video change the driver it may or may not help
but 100% cpu is too much
i do flash chat and cam with only 25%

---

### Post by dtfinch on 2010-06-06
Flash is single threaded, so it using only 25% just means that you have a quad core.

---

### Post by nemilar on 2010-06-06
> **dtfinch said:**
> Flash is single threaded, so it using only 25% just means that you have a quad core.

That's incorrect.  In top, 100% would be one core; 200% would be two cores.  Look in top, you will see things consuming more than 100% CPU.

---

### Post by dtfinch on 2010-06-06
> **nemilar said:**
> That's incorrect.  In top, 100% would be one core; 200% would be two cores.  Look in top, you will see things consuming more than 100% CPU.

It depends on where you're looking. Looking for myself, when I have a process using 2 cores (out of 6), top reports about 33% total and 200% for that process. Mousing over the system monitor toolbar applet reports the lower number.

---

