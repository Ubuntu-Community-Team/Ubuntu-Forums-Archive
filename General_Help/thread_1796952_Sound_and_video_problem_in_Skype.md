---
title: "Sound and video problem in Skype"
date: 2011-07-04
forum: General Help
---

### Post by Cap_Sot on 2011-07-04
Helllo,
I am using Ubuntu 11.04 and skype 2.2.0.35 (beta) in my computer. All of a sudden, where everything was normal, I started a call but the others couldn't hear me..The problem still stands..And on top of that, when I try to start my video nothings happens again..

Any suggestions will be appreciated..

---

### Post by Cap_Sot on 2011-07-05
Nobody familiar with such situations?At least, can anybody give me some hints on how to trace the origin of the problem??

Thanks in advance!

---

### Post by marin123 on 2011-07-05
you dont have sound problems? i mean, do you hear other sounds normally?

go to options in skype and see if sound devices are set to default and while there, test video in video section of skype.

let me know how it went. and also try making test call to echo123...

---

### Post by Cap_Sot on 2011-07-05
Hello and thank you for your reply!
Yes, I can hear other people's voices and other sounds (ie when somebody texts me etc) normally..In sound devices Microphone, Speakers and Ringing have the value: "PulseAudio server (local)".
In video devices section, when testing my camera, I can't see a thing..Only black screen..And also when calling echo, I can't hear my voice, back in the recorded message..

---

### Post by dFlyer on 2011-07-05
Have you checked to see if your mic is mute.

---

### Post by Cap_Sot on 2011-07-05
yeap..the mic is unmuted!

---

### Post by autumnColors on 2011-07-05
I just got an update that caused the mic to stop recording. I can't remember if I used a default app, or if I installed it, but under System->Preferences there is an app/icon simply called "Sound". The window comes up with "Sound Preferences" in the title bar. Under the "Hardware" tab, there are 2 entries. One is for Internal Audio Output and one entry for my Logitech 9000 Pro webcam that has the mic in the camera body. There is a checkbox to mute the Output volume - make sure that is unchecked (it wasn't after the update). On the tab marked "Input", make sure the microphone selected is the one you are using. I only have the Logitech Webcam as an option. There is a second "Mute" checkbox in the Input tab, and it also needs to be unchecked. The "Sound Effect" also has a Mute checkbox for the Alert volume, but that came defaulted to unchecked. Hope this helps.

As for your camera, does it still work on a different computer? If the camera is working, there is usually a light somewhere on the device to let you know it's powered. I can't help much here because I haven't had any camera problems.

---

### Post by gandaran on 2011-07-05
> **Cap_Sot said:**
> Hello and thank you for your reply!
Yes, I can hear other people's voices and other sounds (ie when somebody texts me etc) normally..In sound devices Microphone, Speakers and Ringing have the value: "PulseAudio server (local)".
In video devices section, when testing my camera, I can't see a thing..Only black screen..And also when calling echo, I can't hear my voice, back in the recorded message..
have you tried the camera with cheese? does it work?
did you try other sound drivers options in skype?
also you may try to change the video output driver in 
```
gstreamer-properties
```
type the command in terminal

---

### Post by Cap_Sot on 2011-07-05
> **autumnColors said:**
> I just got an update that caused the mic to stop recording. I can't remember if I used a default app, or if I installed it, but under System->Preferences there is an app/icon simply called "Sound". The window comes up with "Sound Preferences" in the title bar. Under the "Hardware" tab, there are 2 entries. One is for Internal Audio Output and one entry for my Logitech 9000 Pro webcam that has the mic in the camera body. There is a checkbox to mute the Output volume - make sure that is unchecked (it wasn't after the update). On the tab marked "Input", make sure the microphone selected is the one you are using. I only have the Logitech Webcam as an option. There is a second "Mute" checkbox in the Input tab, and it also needs to be unchecked. The "Sound Effect" also has a Mute checkbox for the Alert volume, but that came defaulted to unchecked. Hope this helps.

As for your camera, does it still work on a different computer? If the camera is working, there is usually a light somewhere on the device to let you know it's powered. I can't help much here because I haven't had any camera problems.


Every mute checkbox is unchecked!Thank you though...

> **gandaran said:**
> have you tried the camera with cheese? does it work?
did you try other sound drivers options in skype?
also you may try to change the video output driver in 
```
gstreamer-properties
```
type the command in terminal

Haven't tried cheese yet..with ```
gstreamer-properties
``` I found my webcam and it seems to work (I can see my face :P )but when I start my video in a call, my cam doesn't start..same problem with the sound settings... :(

---

### Post by marin123 on 2011-07-06
so, just to be sure.
i posted a screenshot how my sound preferences look like. do you have everything set correctly? on the input tab you have chosen the right device and connector and set levels to max.

another thing you can try is open the terminal and type alsamixer and see if mic is muted there...

---

### Post by Cap_Sot on 2011-07-06
Fortunately, after playing around with the audio setting (in System -> Preferences -> Sound) I pulled it off. Now, they can hear me perfectly and my sound works properly. However, he problem with the camera still stands..Skype gives me 2 options in Video Devices tab.
- Webcam Live! (which is my camera) and
- Unknown/generic

With both options, the video testing fails, showing me a black screen..

---

### Post by marin123 on 2011-07-06
have you tried with cheese? to test if your camera is working?

i have same weird problem on my desktop. the camera suddenly stopped working in skype, but its working in cheese. i even reinstalled skype but it didnt help. if we solve your problem, maybe we will solve mine :)

---

### Post by Cap_Sot on 2011-07-07
> **marin123 said:**
> have you tried with cheese? to test if your camera is working?

i have same weird problem on my desktop. the camera suddenly stopped working in skype, but its working in cheese. i even reinstalled skype but it didnt help. if we solve your problem, maybe we will solve mine :)

I just installed cheese and the cam is working fine. Also, Ubuntu recognize the type of the camera (mine, it's a usb cam) and from terminal:
```
 gstreamer-properties 
```
when choosing my webcam, video testing for default input succeeds but on the other hand, video testing for default output doesn't show what it should...

---

### Post by Highlands on 2011-07-08
Here is a link that helped me out : [http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html]("http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html")

 &#927; &#963;&#973;&#957;&#948;&#949;&#963;&#956;&#959;&#962; &#948;&#943;&#957;&#949;&#953; &#964;&#951; &#955;&#973;&#963;&#951; &#947;&#953;&#945; &#964;&#951; &#954;&#940;&#956;&#949;&#961;&#945;. &#931;' &#949;&#956;&#941;&#957;&#945; &#948;&#959;&#965;&#955;&#949;&#973;&#949;&#953; &#940;&#968;&#959;&#947;&#945;.
:lolflag:

---

### Post by ssreddy555 on 2011-07-08
I had similar problem wth video in Skype & sorted out in the same way. 

But the picture is too sluggish (Frame rate is very slow) & the whole picture is muddy.

For this, the solution suggested was to install "v4l2ucp" from the software center. This presents a UI for webcam controls like brightness, gamma, sharpness.

This did not improve the quality very much though.

This video problem was not seen with an earlier version of Skype - 2.1.

---

### Post by Cap_Sot on 2011-07-09
> **Highlands said:**
> Here is a link that helped me out : [http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html]("http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html")

 &#927; &#963;&#973;&#957;&#948;&#949;&#963;&#956;&#959;&#962; &#948;&#943;&#957;&#949;&#953; &#964;&#951; &#955;&#973;&#963;&#951; &#947;&#953;&#945; &#964;&#951; &#954;&#940;&#956;&#949;&#961;&#945;. &#931;' &#949;&#956;&#941;&#957;&#945; &#948;&#959;&#965;&#955;&#949;&#973;&#949;&#953; &#940;&#968;&#959;&#947;&#945;.
:lolflag:

Thank you so much &#966;&#943;&#955;&#949; &#956;&#959;&#965;, the skype problem has been solved and the cam works fine but unfortunately, another error showed up..This time with Update manager. The system cannot perform Ubuntu's updates giving me the following error:

```
 Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 63 in source list /etc/apt/sources.list (URI)' 
```

---

### Post by Cap_Sot on 2011-07-09
Ok, I fixed it! The last two lines of the file in the following path:

```
/etc/apt/sources.list
```

caused the specific error. 

```
# libv4l PPA
#deb 
#http://ppa.launchpad.net/libv4l/ppa/ubuntu natty main
```

Finally, I commented out the last two lines and now works like a charm! :)

Thank you all!

---

