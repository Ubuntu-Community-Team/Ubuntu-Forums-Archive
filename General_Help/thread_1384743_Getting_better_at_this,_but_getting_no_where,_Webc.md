---
title: "Getting better at this, but getting no where, Webcam, Skype, Cheese, Camorama"
date: 2010-01-18
forum: General Help
---

### Post by aquamammal on 2010-01-18
Dear Ubuntu maestros,

So I'm running Ubuntu 9.10. I can't seem to get skype to work. See, the person I'm chatting with can receive video and audio, I can receive audio, but I cannot see them, even when they engage their webcam.

My cheese can take pictures from my webcam, but I can't see the screen of the webcam before I take the picture, it's only black, and when I click on the take the picture, it'll take it, and display it correctly, but the screen is black. 

Now, I just dled camorama, but it's saying "Could not connect to video device C/dev/video0). please check connection." I don't know what this means.

My lsusb says: 

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0c45:62f1 Microdia 
Bus 001 Device 008: ID 19b9:4d10  
Bus 001 Device 003: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



The Ricoh Webcam is a built in cam, but it doesn't work either. I have an external cam that used to work, but the cam works, it's just the display that seems effed up.

---

### Post by aquamammal on 2010-01-19
I saw other threads on this topics:

[http://ubuntuforums.org/showthread.php?t=1161113](http://ubuntuforums.org/showthread.php?t=1161113)

[http://ubuntuforums.org/showthread.p...22#post8338722](http://ubuntuforums.org/showthread.p...22#post8338722)

But these threads seem to be talking about the Cairo docks. I'm running ubuntu at the lowest graphics setting possible. No dock or anything. Any help?

---

### Post by 3rdalbum on 2010-01-19
This might sound like it makes no sense at all, but try disabling Compiz and see if you can see your webcam's output.

---

### Post by aquamammal on 2010-01-20
Hey, thanks for the response.

I am uninstalling compiz to see if it will work. Because I am on the lowest settings, I don't even think I was using compiz, but I remember I had some problem like this way back in the day, with 8.10 or something, and compiz was messing around with my google earth, so I'll give this a try. 

I'll let you know what happens.

---

### Post by no2498 on 2010-01-20
open cheese click edit preference  an set the pic size to a smaller 1



Frequently Asked Questions

    * Cheese Manual

    * 6.1.&#8194;The video is sluggish/has a slow response. What can I do?
    * 6.2.&#8194;I have a Mac with iSight and a ATI graphics card, and the colors are weird.
    * 6.3.&#8194;My webcam works with gstreamer, but does not work with Cheese. What's wrong?
    * 6.4.&#8194;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?
    * 6.5.&#8194;Where does Cheese store my photos and videos?
    * 6.6.&#8194;My Quickcam Express doesn't work with Cheese...
    * 6.7.&#8194;"No Camera Found" Error Message
    * 6.8.&#8194;Which cameras are supported?

6.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by aquamammal on 2010-01-21
Thanks for the tip. I tried what you said:

> **no2498 said:**
> 

      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.   


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

But it seems like my settings were already at (X Window System (X11/XShm/Xv). I tried all the possibilities by pressing test, and everytime, the test screen would just be the window with the stuff behind it showing in the box, you know what I mean? It's like a window to the stuff behind it, and if you move the test window, it carries around the image of what was behind it inside.

:(

---

### Post by aquamammal on 2010-01-24
Anyone even have the same problem as me? Haha, I feel like I could be the only one. Scary thoughts.

---

### Post by aquamammal on 2010-01-26
Anyone?

---

### Post by no2498 on 2010-01-26
the bottom 1 is the cam test window

---

### Post by aquamammal on 2010-01-28
The bottom 1?

---

### Post by aquamammal on 2010-02-02
Anyone have the same problem as me?

---

### Post by no2498 on 2010-02-03
did you get ( wxcam )
it works for me

you can type ( cheese -v ) in a terminal see what it says
you got a black window so you are half way set

---

### Post by aquamammal on 2010-02-11
Help?

---

### Post by aquamammal on 2010-02-15
Hey No2498, 

Thanks for the response. I tried Cheese -v and it's a black screen, I can't see myself in the screen, but I can still take the shot. It's like that in Skype, I can't see the other person.

:(

What's wxcam?

---

### Post by *Boots* on 2010-02-22
I finally got my webcam working. This is how I did it (I've had two vollies of updates since I last tried getting this to work, and I installed a new program(mount manager) so maybe those did it):

I went to terminal and typed lsusb and got the following output: 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Then I pressed fn+ F6 together and got this output after waiting fifteen seconds:
boots@boots-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 003: ID 5986:0203 Acer, Inc 
[/COLOR]Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The difference between the two states is highlighted in red. 

After I saw that output that confirmed that my camera was there I opened cheeze and it worked!!! I was very surprised because I had tried this countless times without the terminal, but since I used the terminal it seems to have worked. Besides making no sense at all there may be another thing that worked, and this doesn't make sense either: 

I installed Mount Manager from the software center. 

Good luck to those of you who need your webcams!!!

Boots 
Running Ubuntu Netbook Remix 9.10 from the halls of the Karmic Koala!!!

short story 
1 run the updates 
2 installed the mount manager
3 did the terminal comparison with lsusb

---

### Post by *Boots* on 2010-02-24
It seems I've spoken too soon. I did get my camera working, and it works now, but it seems that at odd times it just decides to stop working. It seems to me that this is because the usb system isn't being dinged enough by the operating system.

The problem is sporatic. 

I think if there is a way, or a program, to get the computer to really get a solid connection to the usb system; then we'd probably not have so many problems with mounting our usb drives, or recognising our web-cams. 

Again with the good luck on the usb stuff like webcams ect....

Btw if there is something out there that can make the connection between the computer and its usb system better I'm game. I thought mount manager did it but thats not the case.

Boots running Ubuntu 9.10 Netbook Remix on dual boot partitions.

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 5986:0203 Acer, Inc 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I will post here again with a configuration when things aren't working again.

---

### Post by *Boots* on 2010-03-01
Well as promised here is the lsusb report for when its not working again(i.e. no thumbdrive or webcam): 

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0203 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

This is a bonafide bug in the system and needs to be fixed. I cannot recall the bug report number but its out there if you will please report your bugs. You'll find it in the launchpad under the following bug number: 
**#445160**

The URL to report the bug is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445160](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445160)

Boots

---

