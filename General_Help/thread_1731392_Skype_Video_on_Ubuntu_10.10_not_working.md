---
title: "Skype Video on Ubuntu 10.10 not working"
date: 2011-04-17
forum: General Help
---

### Post by lucast on 2011-04-17
Hi,

I have just completed a fresh install of Ubuntu 10.10 and installed Skype 2.2.0.25 from the Ubuntu Software Center.  When I go to Options > Video Devices > Test, the camera doesn't display a picture.  It is also not working during a call.

The webcam is a Creative Webcam Live! and it shows up in the Skype video device screen as WebCam Live! (/dev/video0).

I installed Cheese Webcam Booth and the webcam works perfectly. Again it shows up as WebCam Live! (/dev/video0) so I guess everything is ok and must be a problem with Skype?

Any ideas how I can get the camera working in Skype?

Tim

---

### Post by TeoBigusGeekus on 2011-04-17
Old one but it could still apply:
Try to load skype from terminal with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by lucast on 2011-04-17
Hi TeoBigusGeekus,

Your a star, it worked :-)

If its not too much trouble could you explain what the command does, just so I learn?  If not then I am just happy that it now works :-D

last question. How can I change the launcher properties to use this command.  I right clicked on the Skype icon and clicked on properties, changed the command to the one you gave me, but when I run it I get the following message:

Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory)

It works perfectly from the terminal though.


Thank you 

Tim

---

### Post by TeoBigusGeekus on 2011-04-17
Glad you've made it.
The command preloads a certain library (video for linux) before loading skype.

To make it launchable from the menus, open gedit, create a new file and put this line in it
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
Save it as skype_launch in your home folder and exit.
Open a terminal and make the script executable
```
chmod +x ~/skype_launch
```
Edit your menus and replace the Skype command with this
```
bash ~/skype_launch
```
Post back with results.

---

### Post by lucast on 2011-04-17
Done and very happy :-D

Thank you so much!

Tim

---

### Post by pierreu1 on 2011-04-18
> **TeoBigusGeekus said:**
> Old one but it could still apply:
Try to load skype from terminal with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Thank you, but I guess this warning and it does not help with the video issue. Maybe I need to do something beforehand. Not sure! Can you help me please?

(process:13558): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

---

### Post by TeoBigusGeekus on 2011-04-18
> **pierreu1 said:**
> Thank you, but I guess this warning and it does not help with the video issue. Maybe I need to do something beforehand. Not sure! Can you help me please?

(process:13558): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

Perhaps [this]("http://community.activestate.com/forum/if-you-receive-error-gtk-warning-locale-not-supported-c-library").

---

### Post by pierreu1 on 2011-04-18
> **TeoBigusGeekus said:**
> Perhaps [this]("http://community.activestate.com/forum/if-you-receive-error-gtk-warning-locale-not-supported-c-library").

Thanks!

This is what happened. Of course, it was early in the morning when I did this and did not see that the $ had to be excluded from the cut-and-paste operation. Oops! On the other hand, I am not too sure why one includes the $ sign in the code when it seems to be needed all the time, but maybe the terminal application is the odd application that automatically includes the $ when used. ANyway, your help would be much appreciated. Thanks.


...:~$ $ /usr/lib/locale
$: command not found
...:~$ sudo /usr/lib/locale
[sudo] password for ....: 
sudo: /usr/lib/locale: command not found
...:~$ $ sudo ln -s en_US.utf8 en_US
$: command not found
...:~$ /usr/lib/locale
bash: /usr/lib/locale: is a directory
...:~$ sudo ln -s en_US.utf8 en_US
...:~$

This is for MAverick 10.10

---

### Post by TeoBigusGeekus on 2011-04-18
I think it means navigate to the directory
```
cd /usr/lib/locale
```
and then give the link command
```
sudo ln -s en_US.utf8 en_US
```

---

### Post by buzzlightyear2 on 2011-04-27
Thanks, this thread helped, was having the same dark age video :D

---

### Post by cyber187 on 2011-04-27
My video in Skype works perfect , but my microphone doesn't. I'm Using a HP Webcam model HD-4110. Running Ubuntu 10.10 on a HP desktop. The Cam is connected via a USB>

---

### Post by nortexoid on 2011-05-04
Doesn't work on Kubuntu 11.04 using Skype 2.2.0.25. The camera worked perfectly fine in previous versions of skype and it works perfectly fine in Kopete. Why is skype for linux such a huge piece of my SHEEEEIT?

---

### Post by pressureman on 2011-05-25
The v4l1compat LD_PRELOAD trick did not work for me, nor did the upstream package from skype.com themselves.

I have the following camera:

```

Bus 001 Device 004: ID 17ef:4807 Lenovo UVC Camera

```

So it uses the uvcvideo module. This can be controlled with uvcdynctrl, from the package of the same name.

```

daniel@thinkpad:~$ uvcdynctrl -l
Listing available devices:
  video0   UVC Camera (17ef:4807)

```

```

daniel@thinkpad:~$ uvcdynctrl -c
Listing available controls for device video0:
  Exposure, Auto Priority
  Sharpness
  Power Line Frequency
  Gamma
  Hue
  Saturation
  Contrast
  Brightness

```

```

daniel@thinkpad:~$ uvcdynctrl -g "Exposure, Auto Priority"
1

```

I found that Skype is disabling auto exposure as soon as it starts video (even testing your video in the Skype options dialog). You can use uvcdynctrl to re-enable auto exposure once the video stream has started with:

```

daniel@thinkpad:~$ uvcdynctrl -s "Exposure, Auto Priority" 1

```

The video capture should brighten up considerably then. If it's still not satisfactory, try some of the other manual settings in uvcdynctrl, such as brightness and gamma.

Unfortunately this will have to be done each time you start a video call, but it's better than nothing.

---

### Post by belza_jaid on 2011-05-26
hi TeoBigusGeekus thanks a lotssssssssssssss!!!!!!!!!!!!!!!!!!!!!! 
you make my skype complete!.. your the best!.!..

---

### Post by belza_jaid on 2011-05-26
hi TeoBigusGeekus thanks a lotssssssssssssss!!!!!!!!!!!!!!!!!!!!!! 
you make my skype complete!.. your the best!.!..!!!!!!!!more power to ubuntu!

---

### Post by harshavin on 2011-06-03
Hi, I have Ubuntu 10.4 and my Webcam doesn't work on Skype 2.2.0.25 Beta.
I have an "I Smart Infocomm Model:SC-12" WebCam. When I say Test Video on Skype, screen remains blank. However the Webcam works fine on Cheese Webcam Booth. 
I did try the LD_PRELOAD option - but it still doesn't work with in Test or a Call. 
Any Ideas? 
I'm a beginner with Ubuntu, so would be grateful if your'll could use Laymans Terms in the reply. Thank you.

---

### Post by boxcorner on 2011-06-18
@ TeoBigusGeekus
Me too, my video wasn't working and I got it working by following the first part of your your instructions #4. Thank you. However, I'm now having difficulty making it launchable from the menus. When I select Skype from the menu, nothing happens. However, if I type *bash ~/skype_launch* in Terminal, Skype starts ok.

---

### Post by pierreu1 on 2011-06-18
Same problem as #16.

The webscam works fine in Cheese, but when I use it in Skype, I can see the other person's webcam, but she cannot see mine. When I test it in Skype, options,... the black screen stays black! :) The webcam worked perfectly in MAverick/Skype! My system is upgraded. The camera is a Rocketfish cam.

---

