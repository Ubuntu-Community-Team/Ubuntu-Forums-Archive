---
title: "Webcam Help"
date: 2011-05-01
forum: General Help
---

### Post by EGamerHDK on 2011-05-01
So, just got finished installing Ubuntu (Read Signature)

I installed "Cheese" web-cam software. Worked without a hitch. I've always heard Linux is hard with drivers and such but, everything works so far. I'm on a laptop so my main features (Track pad, web cam, Mic, audio) all work. I even plugged in an external mouse and external sound card and I had no problem. So, in a nutshell, so far I love Linux. Only two things giving me problems.

Compiz: Just trying to get that cube seems impossible. But, it looks like a lot of people are having a tough time with it. So, I'm just putting it off.

Second,

Web cam: So, like I mentioned before, I installed cheese. I saw some guy giving a Ubuntu Natty Narwhal Tutorial on You tube and that's what he was using. Essentially, it's just really slow and laggy for the lack of better terms. Is this a driver problem?

Also, really quick, in Windows theres Device Manager. Anything like that in Linux?

Lastly, it's been great to finally join the Linux community and hope to contribute as much as possible. Thanks in advance!

---

### Post by wgarcia on 2011-05-01
Linux works differently with respect to drivers. If they are free and open source they are handled directly in the kernel. If your hardware is supported by this type of drivers everything should work out of the box.

In any case if you open the Dash (Super Key) and you type "joc" you will be able to open the "Additional Drivers" application that will look for existing proprietary drivers that can be used for your hardware if you want. They are not always necessary, if everything works well with the free drivers it is better to use those.

As for the webcam, if you know the model it could be helpful to look for the level of compatibility with Linux. To know the exact model you can enter "Ter" the same way as before, open a terminal, and if it is an integrated webcam type:

dmesg | grep -i cam

if it is connected through USB 

lsusb | grep -i cam

---

### Post by VMC on 2011-05-01
> **EGamerHDK said:**
> So, just got finished installing Ubuntu (Read Signature)

....

Compiz: Just trying to get that cube seems impossible. But, it looks like a lot of people are having a tough time with it. So, I'm just putting it off.

Second,

Web cam: So, like I mentioned before, I installed cheese. I saw some guy giving a Ubuntu Natty Narwhal Tutorial on You tube and that's what he was using. Essentially, it's just really slow and laggy for the lack of better terms. Is this a driver problem?

Also, really quick, in Windows theres Device Manager. Anything like that in Linux?

Lastly, it's been great to finally join the Linux community and hope to contribute as much as possible. Thanks in advance!

I never tried the cube stuff.
I did install Cheese during one of the beta cycles. It work great as does my Skype and my internal web mic, which never worked in the past.

For Windows Device Manager try System Settings and see if that's what your after. Either through Dash or click on the off off, top righ and at the bottom you will find system Settings.

---

### Post by Oddvar on 2011-05-01
I have found the only program which support my webcam fully is Gyachi. Thats why after all, I have a webcam; To be able to chat and see family and friends. Maybe its not ready for 11.04 yet, but it will come.

---

### Post by EGamerHDK on 2011-05-01
Thanks for the replies. After entering that code for an integrated web cam into terminal I got:

[    5.343183] uvcvideo: Found UVC 1.00 device Integrated_Webcam_2M (0c45:63f1)
[    5.352354] input: Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7

---

### Post by EGamerHDK on 2011-05-04
Bumping with just the question of what to do with the output...

---

### Post by no2498 on 2011-05-04
this comes from cheese's top FAQ

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by EGamerHDK on 2011-05-05
> **no2498 said:**
> this comes from cheese's top FAQ

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

Sounds like it'll work, but... how do I run gstreamer-properties. Did I install this or is this just something that's installed in Ubuntu. Thanks in advance

---

### Post by no2498 on 2011-05-06
in a terminal type gstreamer-properties click enter
click video

---

### Post by EGamerHDK on 2011-05-07
Shows how much I know... I was entering it into the thing that comes up when I press Ctrl+Alt+F1. I opened terminal and the code worked in there. Oh Ubuntu. So much to learn hahaha.

It was on Auto. Changed it but no difference. Hmm.....
So far seems to be the only thing that works better in windows.

---

### Post by timgood on 2011-05-07
I had the same problem and installed guvcview which is much better than Cheese for capturing video without lag, and also has some very nice features to play with output. Install by:

```
sudo apt-get install guvcview
```

Hope this helps.

---

