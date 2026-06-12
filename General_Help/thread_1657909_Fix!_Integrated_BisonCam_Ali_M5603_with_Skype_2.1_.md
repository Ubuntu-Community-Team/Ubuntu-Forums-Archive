---
title: "Fix! Integrated BisonCam Ali M5603 with Skype 2.1 Beta on Jaunty 9.04"
date: 2011-01-01
forum: General Help
---

### Post by Captaingracekidd on 2011-01-01
After 1,5 years of searching for a solution to get my bison 1.3 mpixel webcam to work in ubuntu tonight I got a picture. 

As I know a lot of people are experiencing problems with this I will here give a record on what I did and where I found the info:

Specs: [B]Zepto Znote 6025WD
Jaunty Jackalope 9.04 2.6.29-020629-generic
Integrated BisonCam Chipset Ali M5602
Skype 2.1 Beta (from website)[/B]

First of I had to turn on the button for the camera to start.
To see if the driver and the camera was working I followed this advice:

```
lsusb |grep 0402:5602
```

The result was:
```
lsusb |grep 0402:5602
Bus 002 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller

```

Next:
```
gstreamer-properties
```
Go to video tab, Default Input and make sure to choose Video for Linux (v4l2) as your choice. 
I was lucky and saw myself, even if it was poor quality. 
[B]
The Skype Factor[/B]
Then I just needed Skype to get that I DO have a webcam, it hadnt been found automatically and 2.1 doesnt support manual directing to the webcam. 
So then I found this amazing code:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"
``` 
from: [http://ubuntuforums.org/archive/index.php/t-1423686.html](http://ubuntuforums.org/archive/index.php/t-1423686.html)

When opening skype with this there appears a webcam option, in my case USB2.0 Camera (/dev/video0). I pressed test and the pic worked! 

After the normal way of opening skype did not show the camera as working even though the direction for the camera was showing I tried to change the menu listing for the application, but it failed due to menu not being able to understand the short code. After reading that many people experienced success with scripts that first took you to the actual destination and then running the program I decided to open my text editor and wrote a script like this:
```
#!/bin/bash
cd /usr/bin/
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype "$@"
```

I then ticked the box for making the file executable in the permissions tab and now I can run the file to run Skype with camera. There is also a possibility that skype will work from application menu like normal with a working cam after having found the direction for it and rebooted the system. I am to lazy to reboot right now soooo... i will update if this is the case and my little lazy script is just unnessecary.

I hope someone had some help from my experience. ):P

---

### Post by elpako on 2011-06-02
Thaaaaaaaaaaaaaank you!!!

Your instructions were exact! Finally my skype use the webcam!!
I have an Asus A6VA with a BisonCam integrated cam and i wan't be able to configure it!!

Now it works perfectly!
I tried to use the same trick also for firefox (to use cam in webchats as chatroulette), but it's not work...

However i made the following procedure to use the webcam also when launch Skype from the Program Panel (without launching explicitly these commands):

```
sudo mv /usr/bin/skype /usr/bin/skypeLauncher
sudo vi /usr/bin/skype
sudo chmod 777 /usr/bin/skype
```
 
and then i launched Skype by program panel and the cam worked!

Byee

---

### Post by no2498 on 2011-06-03
for the chat's you need to set the sites you use in the adobe settings manager to allow and remember

---

### Post by caminhante on 2011-09-30
Hi.

I did all you guys said, and now my cam is working in the teste of the video options tab.

But whem I try to use my cam in a call skype crashes. 

The audio is working fine, and I cam se the other person's webcam image. But when I start MY webcam skype crashes.

Why is that happening? Can anybody help me?

---------------------------

PS: The comand "xvinfo" gives the follow information:

$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

---

