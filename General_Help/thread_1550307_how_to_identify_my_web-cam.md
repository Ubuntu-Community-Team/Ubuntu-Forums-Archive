---
title: "how to identify my web-cam"
date: 2010-08-10
forum: General Help
---

### Post by sysabod on 2010-08-10
deal all:
           i am using my laptop with a built-in web-cam, but i just wonder what interface it is connectied to,i.e. is it dc1394 or usb or any others &#65311;

Please help me, thanks in advance!

---

### Post by little_penguin on 2010-08-11
Many built-in webcams are connected to the usb bus. If yours is, you can enter this command to find out the make, model and ID:
 
```
lsusb
```

---

### Post by sysabod on 2010-08-11
> **little_penguin said:**
> Many built-in webcams are connected to the usb bus. If yours is, you can enter this command to find out the make, model and ID:
 
```
lsusb
```

thanks, it is connected to usb bus , isn't it mean that i should choose video4linux driver among many drivers?

---

### Post by no2498 on 2010-08-12
did it show up in the list of the lsusb

look in sound & video for cheese webcam booth
just try the cam in it first

hope this helps

---

### Post by little_penguin on 2010-08-12
Please paste the output of the lsusb command here. You can do that by copy-and-pasting it from the terminal. This will give us information on the make and model of your webcam, so we can see what driver it needs.

---

### Post by sysabod on 2010-08-12
> **little_penguin said:**
> Please paste the output of the lsusb command here. You can do that by copy-and-pasting it from the terminal. This will give us information on the make and model of your webcam, so we can see what driver it needs.

ok, it is so kind of you all,here is my command output

```
Bus 002 Device 004: ID 5986:0182 Acer, Inc 
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

it seems no clue to the web-cam ?

---

### Post by little_penguin on 2010-08-14
It's possibly the first entry, not sure, but before I try to hunt down the model according to the IDs from the lsusb command, please also post the output of ```
lspci
``` just in case, plus the output for ```
lshw
``` as well as ```
uname -r
``` 

Can you tell us what model of Acer laptop you have - is it very new, or is it a few years old? Could you also post a weblink showing the model you bought, I might then be able to find technical specs somewhere and see which webcam we are dealing with.

---

### Post by sysabod on 2010-08-14
> **little_penguin said:**
> It's possibly the first entry, not sure, but before I try to hunt down the model according to the IDs from the lsusb command, please also post the output of ```
lspci
``` just in case, plus the output for ```
lshw
``` as well as ```
uname -r
```Can you tell us what model of Acer laptop you have - is it very new, or is it a few years old? Could you also post a weblink showing the model you bought, I might then be able to find technical specs somewhere and see which webcam we are dealing with.

i have tried the 3 commands and got very long entry list, so i just paste the info related to USB.
if you wanna explore the whole stuff, just take a look at the attachments.

```
lspci | grep USB
```00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

```
lshw | grep USB
``` description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
```
uname -r 
```2.6.32-24-generic

Sincerely hope this help you

---

### Post by little_penguin on 2010-08-14
Thanks for the attachments. So it seems the laptop is a Haier T6 series notebook from a (Chinese) vendor called Haier Computers, is that correct? I must admit I have never heard of them before :) None of the information really tells us the model of the webcam in a descriptive way, which leaves us guessing a little bit, but I think the webcam ID must be this:

> ID 5986:0182 Acer, IncI would suggest trying it with the UVC-based programs, e.g. Skype, Ekiga and Cheese and let us know if they see your webcam at all. Ekiga and Cheese are in the repositories, you can download Skype for Linux from their website.

---

### Post by no2498 on 2010-08-14
this is not the code but is like dsmsg will look harder for the cam

---

### Post by little_penguin on 2010-08-14
Good idea, forgot about that. Sysabod, could you also attach the output of the command ```
dmesg
``` as suggested by no2498?

---

### Post by sysabod on 2010-08-14
> **little_penguin said:**
> Thanks for the attachments. So it seems the laptop is a Haier T6 series notebook from a (Chinese) vendor called Haier Computers, is that correct? I must admit I have never heard of them before :) None of the information really tells us the model of the webcam in a descriptive way, which leaves us guessing a little bit, but I think the webcam ID must be this:

I would suggest trying it with the UVC-based programs, e.g. Skype, Ekiga and Cheese and let us know if they see your webcam at all. Ekiga and Cheese are in the repositories, you can download Skype for Linux from their website.

Yes, you are right that  i am using a computer from a Chinese Vendor.

I did not try the programs you suggested ,yet, i check out the properties of my usb video device in the windows device manager, when switched to the details tab and select HardWare Ids from the droplist, i can see this which shows your guess about the webcam id is totally right.

```
USB\Vid_5986&Pid_0182&Rev_0008&MI_00
USB\Vid_5986&Pid_0182&MI_00

```

thanks for your time and energy

---

### Post by little_penguin on 2010-08-15
According to this website, your webcam is made by Bison Electronics (Vendor ID 5986). It might be supported by the UVC driver, see list of supported Bison webcams, although your product model (Product ID 0182) isn't explicitly listed, it might still be covered with a bit of luck. Try Skype, Ekiga and Cheese, and let us know.

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

---

### Post by sysabod on 2010-08-15
> **little_penguin said:**
> According to this website, your webcam is made by Bison Electronics (Vendor ID 5986). It might be supported by the UVC driver, see list of supported Bison webcams, although your product model (Product ID 0182) isn't explicitly listed, it might still be covered with a bit of luck. Try Skype, Ekiga and Cheese, and let us know.

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

i installed cheese but don't know how to get the result.

---

### Post by no2498 on 2010-08-15
this is the cheese help fie faq's


*

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
    
5.5.&#8195;Where does Cheese store my photos?


      Your photos are stored in ~/.gnome2/cheese/media. You can also save
      them to an alternate location from within Cheese. Please see the help
      topic titled "Saving photos and videos to an alternate location" for
      information on this.
    
5.6.&#8195;My Quickcam Express doesn't work with Cheese...


      or gstreamer, and I see errors like "Not enough buffers. We got 1, we
      want at least 2" in the Cheese output. With driver "qc-usb".
    


      Try running "qcset /dev/video0 compat=dblbuf" to enable double buffer
      compatibility mode, then restart Cheese
    
5.7.&#8195;Which cameras are supported


      Cheese uses gstreamer for video grabbing. So in principle Cheese supports 
      any camera that works with GStreamer. In principle that should be any camera
      which support video4linux or video4linux2.

---

### Post by little_penguin on 2010-08-15
Could you also try with Skype and Ekiga?

---

### Post by sysabod on 2010-08-15
> **little_penguin said:**
> Could you also try with Skype and Ekiga?
 
 I installed both and carefully scan each option , but still could not get the web-cam id info, 

 skype can open my video device while ekiga failed.

 Does they ever have the feature ? when  i click the "detect device" button in ekiga, it gives me no response.

---

### Post by little_penguin on 2010-08-16
Actually, in Ekiga I don't think the camera preview in the video settings always works. Could be a bug. I click "Detect device" and it doesn't do anything either. It is recognized though. Try actually making a test conference call, echo test, the Ekiga video usually shows up then. It does for me, anyway. I think if Skype can see your webcam, it should work with Ekiga as well.

---

### Post by no2498 on 2010-08-17
open a terminal put this in it, LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 

that should help with cheese

---

