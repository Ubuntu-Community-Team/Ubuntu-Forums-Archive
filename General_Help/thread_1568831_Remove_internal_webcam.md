---
title: "Remove internal webcam"
date: 2010-09-05
forum: General Help
---

### Post by sam-bo on 2010-09-05
I have a dv9000 and the internal  webcam is not functional. Since  skype is defaulted through "/dev/video0"  and not changeable, my usb  webcam deosnt appear in skype. However,  cheese and webcam studio both  use the usb cam. how do I go about booting  the internal webcam off of " /dev/video0" to be able to une skype with the usb webcam?
 
thanks,
 
sam-bo

---

### Post by anubhavrocks on 2010-09-05
There is this config.xml which might be helpful in your case:

I think its in "~/.Skype/SKYPEID/config.xml"

Remember to restart skype once you make changes to this file.

---

### Post by sam-bo on 2010-09-05
Where exactly do I make these change?

in "gstreamer-properties"
or skype settings?

---

### Post by anubhavrocks on 2010-09-05
1. First of all make a backup of the config.xml.
2. You need to find "/dev/video0" and replace it with "/dev/video1", save the changes and restart skype if it is already running.

---

### Post by sam-bo on 2010-09-05
ok, How do I find the "config.xml" and how do I back it up.  I appreciate your help.

---

### Post by sam-bo on 2010-09-05
is it "sudo edit ~/.Skype/SKYPEID/config.xml" ?

---

### Post by sam-bo on 2010-09-06
ok so I got "sudo gedit /home/user/.Skype/id/config.xml" but there is no "/dev/video0"

am I close?

---

### Post by HermanAB on 2010-09-06
You can also rename the devices:
mv /dev/video0 /dev/video2
mv /dev/video1 /dev/video0

Then Skype should pick up the correct video device - till you reboot.

---

### Post by sam-bo on 2010-09-06
i get error:

mv: cannot move `/dev/video0' to `/dev/video2': Permission denied

how do I change to "write" privilege?

---

### Post by anubhavrocks on 2010-09-07
sudo can be used to get super user privileges.

sudo mv /dev/video0 /dev/video2
sudo mv /dev/video1 /dev/video0

---

### Post by sam-bo on 2010-09-08
Yes that worked since the last sudo update.  Now thw skype video source is "/dev/video2".

Everything works fine, wxCam and WebcamStudio both show video.  I set wxcam to "video4linux1" and "video4linux2", also "auto" and no combination seems to affect skype.  the test shot deose not want to pick up video.

---

### Post by no2498 on 2010-09-08
you are only setting the cam program to v4l1 or 2

thy this

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by sam-bo on 2010-09-08
After making the sudo commands, this is the error:

Video for Linux 2 (v4l2): Could not open device '/dev/video0' for reading and writing.

thought "test input" and "custom" both show the color screen with a bit of snow in the corner.

when I run "gstreamer-properties", there are 7 skipping lines:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

---

