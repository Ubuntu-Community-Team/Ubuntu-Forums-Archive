---
title: "Webcam server via http anyone help me with blank images"
date: 2010-02-09
forum: General Help
---

### Post by t4thfavor on 2010-02-09
I have 2 webcams installed on my ubuntu server, I have used them both in the past, both on Linux and Windows. Currently I have tried webcam-server, and motion. The output is a blank image. It looks like the brightness is set all the way up or something.

I have a logitech QuickCam express (looks like a ball) and a 3com homeconnect (old)

```

#lsusb
Bus 004 Device 002: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam]
Bus 002 Device 003: ID 046d:0920 Logitech, Inc. QuickCam Express

```

I have published the site so you all can see what it looks like.
[http://fultonit.net:8081](http://fultonit.net:8081) I took this down since the same thing happens with fswebcam

Can anyone give me any ideas on why it doesn't work when it used to. 

Does it have something to do with the v4l2 driver, I believe it used to work with the older v4l driver.

---

### Post by hwttdz on 2010-02-09
When I use fswebcam I have to throw out the first n frames otherwise it appears severly overexposed.  I'm not sure how to get live webcams (mine just snaps a photo every few seconds).

---

### Post by t4thfavor on 2010-02-09
That's really all i'm looking for, is a snap every second or two, but all of them look like they are grey blank images.


There are 500 some in the tmp/motion folder, and they all look the same.

---

### Post by hwttdz on 2010-02-09
Here's my fswebcam config:

```
log /home/$user/public_html/webcamlog.txt
#log /dev/null
device /dev/video0
skip 10
jpeg 80
#deinterlace
resolution 1600x1200
no-banner
set "Sharpness"=200
#set "White Balance Temperature, Auto"=False
set "White Balance Temperature, Auto"=True
set "Backlight Compensation"=0
set "Brightness"=130
set "Contrast"=32
#32 is default
set "Saturation"=28
#28 is default
frames 1
#frames 255
#loop 1
save /home/$user/public_html/output.jpg
```

And I do essentially

while [ 1 ]; do
fswebcam --config ~/path_to_config_file
done

You'll have to modify the options for your webcam, but you should get the gist of it.

---

### Post by t4thfavor on 2010-02-09
This is what the output from fswebcam, Same as the output on the website. I think this is a problem with the v4l2 driver. I guess I will have to delve deeper into that unless someone else knows how to fix it.


Thanks,

---

### Post by hwttdz on 2010-02-09
What's your fswebcam log say? perhaps you should run it specifying options on the command line until you get it figured.

---

### Post by t4thfavor on 2010-02-09
Perhaps were getting somewhere.

```

Writing JPEG image to '/home/chance/output.jpg'.
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Setting Brightness to 130 (36%).
Adjusting resolution from 1600x1200 to 352x288.
Error setting pixel format.
VIDIOC_S_FMT: Invalid argument
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Setting Brightness to 130 (36%).
Adjusting resolution from 1600x1200 to 352x288.
Error setting pixel format.
VIDIOC_S_FMT: Invalid argument
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Setting Brightness to 130 (36%).
Adjusting resolution from 1600x1200 to 352x288.
Error setting pixel format.
VIDIOC_S_FMT: Invalid argument
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Setting Brightness to 130 (36%).
Adjusting resolution from 1600x1200 to 352x288.
Error setting pixel format.
VIDIOC_S_FMT: Invalid argument
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Setting Brightness to 130 (36%).
Adjusting resolution from 1600x1200 to 352x288.
Error setting pixel format.
VIDIOC_S_FMT: Invalid argument
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Setting Brightness to 130 (36%).
Adjusting resolution from 1600x1200 to 352x288.
--- Capturing frame...
Skipping 10 frames...
Capturing 1 frames...
Captured 11 frames in 1.98 seconds. (5 fps)
--- Processing captured image...
Setting output format to JPEG, quality 80
Disabling banner.
Writing JPEG image to '/home/chance/output.jpg'.

```

```

#sudo fswebcam -d v4l2:/dev/video0 --list-inputs
--- Opening v4l2:/dev/video0...
/dev/video0 opened.
--- Available inputs:
0: tv8532
No input was specified, using the first.
Adjusting resolution from 384x288 to 352x288.
--- Capturing frame...
Captured frame in 0.00 seconds.
--- Processing captured image...
There are unsaved changes to the image.


```

---

### Post by hwttdz on 2010-02-09
And one from mine:

```
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Setting Brightness to 130 (50%).
Setting Contrast to 32 (12%).
Setting Saturation to 28 (10%).
Setting White Balance Temperature, Auto to True (1).
Setting Sharpness to 200 (78%).
Setting Backlight Compensation to 0 (0%).
--- Capturing frame...
Skipping 10 frames...
Capturing 1 frames...
Captured 11 frames in 2.00 seconds. (5 fps)
--- Processing captured image...
Setting output format to JPEG, quality 80
Disabling banner.
Writing JPEG image to '/home/user/public_html/output.jpg'.
```

---

### Post by t4thfavor on 2010-02-09
Any ideas? It appears that my log is roughly the same as yours. The second snippet is the output from the --list-inputs command which specifies that there is only one input on the device.

---

### Post by hwttdz on 2010-02-09
Why not try specifying the device with driver test and seeing if you get the color bars?

---

### Post by t4thfavor on 2010-02-09
Beautiful colorbars, they look exactly like they did in the 80's on TV :)

---

### Post by hwttdz on 2010-02-09
Hey, that's progress, little steps.  

Ok, what if you don't specify a driver in a prefix (it then steps through the list). 

Apparently you're getting a pixel format error, whatever that means.  But that's where to start searching.  Sorry I couldn't be more help.

"Error setting pixel format.
VIDIOC_S_FMT: Invalid argument"

---

### Post by t4thfavor on 2010-02-09
I haven't tried adding a prefix, but when I specify anything other than v4l2 it doesn't work. 

With v4l1:/dev/video0
```

/dev/video0 opened.
Requested width too large. Adjusting 1600 -> 352.
Requested height too large. Adjusting 1200 -> 288.
No input was specified, using the first.
Error getting information for input "(null)".
VIDIOCGCHAN: Invalid argument
/dev/video0 closed.

```

---

### Post by no2498 on 2010-02-09
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2

get cheese and wxcam 

getdeb has wxcam

1 of the 2 will see your cam
open cheese's help file faq's has a lot of help in it
if you used v4l1 before you may need a file v4l1 to v4l2
sorry i forget what its called
but it lets v4l1 work with the new v4l2 driver
hope this helps

---

### Post by t4thfavor on 2010-02-09
Its a guiless server :( so no go on the cheese and whatnot, its just for web stuff, no gui at all.

---

### Post by t4thfavor on 2010-02-10
Friendly neighborhood bump! Just for good measure.

---

### Post by no2498 on 2010-02-10
you are on linux - ubuntu
did you try gstreamer-properties 
thats how they test the cams

---

### Post by t4thfavor on 2010-02-11
I think that requires a gui, no? If not, what package does it come in?

Remember, I just wan't my webcam to take a picture every so often, and put it on the web, all I get from 2 different webcams is varying shades of grey/blue which does not help.


Update, at night the picture is black, like so. So this has to be a settings issue.

---

### Post by t4thfavor on 2010-02-13
OK, so if I put the webcams on a system with a gui, I get some success with gstreamer-properties.

The 3com camera appears to work fine with the v4l1 driver. Great, I tried it on skype, and it segfaults :(  nogo. The logitech gives me a scrambled input using the v4l driver, and then tells me "Could not get /settings from device/resource."


If I use v4l2 with the logitech, I get a green picture that looks like a nice clear shot, just like night vision in the movies. i am sitting in broad daylight so I know its not a low light situation. This one also fails in skype, it shows a grey box to me, and a "loading" circle to the other party.

EDIT:I changed some properties in the gstreamer-settings app, and the output became normal color. It still doesn't work in any apps though.

Anyone know where the settings file is for this as I would really like to get these cameras working on my server, or at least on my laptop with skype.

---

