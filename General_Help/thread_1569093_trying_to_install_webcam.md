---
title: "trying to install webcam"
date: 2010-09-06
forum: General Help
---

### Post by andypearce on 2010-09-06
Hi I am using  toshiba satellite pro L100 with ubuntu 10.4. I want to use skype on it so need a webcam... I took a punt and got a cheap one from a supermarket. The specifications of this cam are compatible with windows 98se, ME,2000, xp and vista. As I am running ubuntu I put the software disk in anyway and it registered on the desktop as AUTORUN and the paper instructions say select driver to start the installation. This was there when I clicked the icon then a file setup which I clicked and things seemed to happen. Then I got this on the screen...

An error occurred while loading the archive.
Command line output
Archive:  /media/cdrom0/Driver/Setup.exe
[/media/cdrom0/Driver/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Driver/Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Driver/Setup.exe or
          /media/cdrom0/Driver/Setup.exe.zip, and cannot find /media/cdrom0/Driver/Setup.exe.ZIP, period.

I am a bit in the dark here... I assume I need the software for the laptop to detect and operate the webcam. If I do need the software can I get it onto the laptop to make the webcam work bearing in mind the fact that it is a windows compatible webcam or does that not matter. If it does matter then it is no great loss as I will give it to my daughter to use on her pc (Windows). Do I need an Ubuntu or linux specific webcam?Any help would be greatly appreciated.
Andy

---

### Post by no2498 on 2010-09-06
the disk is for windows only so its no use to try

10.04 cheese webcam booth should be loaded
look in sound & video for it with the cam pluged in try cheese

hope it comes on for you

---

### Post by andypearce on 2010-09-06
Thanks I will give it a try.. had a quick peep in applications and it was not there but I will see if it is in the software bit... I will post what I have done.
Thanks again
Andy

---

### Post by andypearce on 2010-09-07
Ok... so I installed cheese and plugged the webcam in and it first said it did not detect it.... a big 'no entry' sign. I noticed a faint green light on the front of it that got brighter during the plugging in process then faint then off. The on/off button made this light flash then go away. I fiddled about a bit.

I have two USB ports on the right hand side of the laptop side by side. The front one has my mouse plugged in and I was using the rear one for the webcam. During one of the fiddles the mouse was 'knocked out'... no power... without me touching it. It came on again when I re started the laptop. I then tried the webcam in the two USB ports on the left, one on top of the other. The webcam again sometimes had a dim light, sometimes a bright light but mostly no light. I tried it on my daughters windows pc and the light was on and it wanted software.

Am I right to conclude that there is something wrong with the USB ports and they will only power a mouse? During the cheese fiddling there were times I got a blank screen rather than a no entry sign saying no cam detected but I could get nothing to happen (this was after a swirly thing on the screen that made me think something was happening). Is this a feature of Ubuntu that hardware for windows will not fit it. When I changed my last pc to Ubuntu it seemed to detect everything no problem including the HP printer which I did think would have problems, but all worked fine? Any thoughts anyone?
Thanks
Andy

---

### Post by howefield on 2010-09-07
> **andypearce said:**
> I took a punt and got a cheap one from a supermarket.

That was probably your first mistake ;-)

If you want a sweet life with Linux, pay more attention to the hardware you take a "punt" on.

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

---

### Post by no2498 on 2010-09-07
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by eev2 on 2010-09-07
So, what model is your webcam?

---

### Post by andypearce on 2010-09-07
Right.... no2498, I ran gstreamer-properties on the terminal and it opened a box and I clicked where it said video at the top. At the bottom of the box there was a bit where it said video for linux2 (v412) and a test button which I selected.Another box opened with me in it... the camera worked...very grainy but I suppose I will find bits to fiddle with to help with that or it reflects the cheapness of the camera bought. I closed this down and clicked cheese and there I was again, it is working!. Again I remain mystified at the workings of these devices but am always very pleased by the help I get from yourself and the wider Ubuntu community. Thank you.

To eev2 I am a bit embarrassed by the make of my webcam as it comes from the evil empire here in the UK, but the model is a TECHWEB1. I will not try to explain what I was doing in there in the middle of the night but I had a good excuse.....

Thanks again all... I will mark this as solved as the webcam works and I cam proceed with getting Skype.

---

### Post by no2498 on 2010-09-07
glad you got it working

---

### Post by nowayucant on 2010-09-24
hello to all . very new to linux . this will be my 1st post . love ubuntu btw . 10.04 . is what im running . . anyway . im having a problem with my webcam & printer .. webcam is a logitech not sure the model # there is no markings on it anywhere other then just to say its logitech .. printer is crap .. but still works with windows its a HP deskjet d1660 . i would really appreciate any help .. as i am new to linux simple suggestions would be best  .. remember im a windows user haha  trying to switch .. thank you in advance :)

---

### Post by no2498 on 2010-09-25
nowayucant
did you do as i told him to do if yes type this in a terminal lsub
give the output in your own ?

---

