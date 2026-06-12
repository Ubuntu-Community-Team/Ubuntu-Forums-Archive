---
title: "Adobe flash problems"
date: 2012-02-10
forum: General Help
---

### Post by crs501 on 2012-02-10
I run Ubuntu 10.04 (I believe it's a 32 bit system) with Firefox 10.0 and have been experiencing numerous problems with Adobe Flash Player. In order to NOT have problems I've had to leave Adobe Flash Plugin 10.2.159.1 on my computer. EVERY TIME without exception over the past week that I have tried installing what I'm told is the latest Adobe Flash (11.1.102.55) It crashes repeatedly. I was here to get advice a week ago and I tried Flash Aid but it did not help in any way. I ended up re-installing my OS and Browser to what I've told you about above and I get limited success with the 10.2.159.1 plugin. I am a Musician, I actually use YouTube to view both performance and instructional videos for learning new songs for my band. Plus I regularly receive videos from friends in e-mail and on Facebook, but lately most everything I need to view requires the latest Flash - 11. I've even seen several comments here indicating I'm NOT ALONE in experiencing problems with the newest Adobe Flash player. Why does the new Adobe Flash plugin 11 keep crashing on me and how do I solve this? I'm not a computer whiz, just a User, so complicated answers and code will might only contribute to my problem. 
    I just went to the Firefox add-ons page and tried to download Flash Aid - - I could not! I did get the following message each of the three time I tried to download & install it "...*there was an error downloading Flash Aid.*" I went to addons.mozilla,org and tried but no luck. I simply got the message: "...*the add-on could not be downloaded because of a connection failure on add-ons.mozilla.org*". Can somebody please suggest something helpful???  Richard...

---

### Post by collisionystm on 2012-02-10
Just to concur...

> I just went to the Firefox add-ons page and tried to download Flash Aid -  - I could not! I did get the following message each of the three time I  tried to download & install it "...*there was an error downloading Flash Aid.*" I went to addons.mozilla,org and tried but no luck. I simply got the message: "...*the add-on could not be downloaded because of a connection failure on add-ons.mozilla.org*". Can somebody please suggest something helpful???  Richard...


I get this too. I just installed adobe flash 11 from the software center

---

### Post by crs501 on 2012-02-10
Just saw your response "collisionystm" and went to the Software Center on my computer. The only Adobe Flash player available there is 10.2.159.1, the one I have right now that is working, albeit in a limited way. I went to the add-on's page and tried to 'enable' Shockwave Flash 11.1 r102 but each time I do Flash crashes repeatedly. As long as I leave that Shockwave Flash 'disabled' I'm OK. This is very frustrating!!!

---

### Post by pqwoerituytrueiwoq on 2012-02-10
alternative flash aid download link
direct link:
[https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.2-fx-linux.xpi](https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.2-fx-linux.xpi)
download page:
[https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads)

---

### Post by crs501 on 2012-02-10
Used Flash Aid - - it did nothing but replace my Flash player 10.2.159.1 which works OK on a limited basis with Flash player 11.1.102.55 which continues to crash repeatedly. I was able to retain the older Flash player that works but meanwhile my problem remains unsolved!!! Anybody have any other ideas?

---

### Post by efflandt on 2012-02-10
Do you have a link to an example flash video that gives you problems?

My old desktop is running 10.04 which is 64-bit, but it's early Athlon64 3200+ (2 GHz) cpu is missing an instruction for 64-bit flash, so it uses flashplugin-installer, which is 32-bit flash with a wrapper.  Firefox is 10.0 and add-ons says it is using Shockwave Flash 11.1r102. Other than occasionally dropping a video frame due to its legacy ATI X1300 video, it has no problems with FoxNews videos or almost a 10 minute 720p YouTube video about minecraft.  Although, that PC and its video is not fast enough to play minecraft (which works fine in 64-bit 11.10 on PC in my sig).

What video card or chip are you running and which driver (default, an ubuntu package, or other)?  I was going to ask if you had any other flash (like gnash) installed, but I think Flash Aid is supposed to remove any alternate flash like plugins.

---

### Post by crs501 on 2012-02-13
OK I'm gonna try this one last time: I have an old Dell computer that was refurbished by a Programmer-friend a couple years ago. It has a Pentium 4, 1500 Mhz processor, out of a total of 26.5 Gb I have about 18 Gigs available on the hard drive. I have no idea what cards or chips or drivers are inside nor do I have any idea how to find out. I run Ubuntu 10.04 (32 bit) with Firefox 10. About 10 days ago I ran Update Manager as usual and got an upgrade of my browser from Firefox 9 to 10. Almost immediately I began to see my Adobe (or Shockwave - I honestly don't understand if there is a difference) Flash plugin crash on a consistent basis. Thru a lot of trial and error I discovered I could leave the older flash plugin 10.2.159.1 in place and would be able to see Youtube and some other limited stuff. But each time I tried to upgrade to the more current 11.1.102.55 it begins crashing all over again. 

Now I don't know how to provide any proof of what I'm saying, I'm not technically skilled like many of you BUT I've just described in as detailed a manner as I know how exactly what the issue is that I'm dealing with. I would dearly love a solution as I am a working Musician who uses YouTube (& other video sources) to learn songs for my band from both performance and instructional vids. I receive stuff all the time from friends by e-mail and on Facebook that I presently cannot access, because the flash plugin that does work for me at present only works in a limited manner. I am constantly getting messages stating"*...you must download and install the latest version of Adobe Flash Player to view this content..."* - - when I try to do that Flash just crashes again!. And before anyone suggests FlashAid, I've tried it and it doesn't help!!! This is exceedingly frustrating - - - Is there any simple, practical help out there?

---

### Post by pqwoerituytrueiwoq on 2012-02-13
try this:
```
sudo su
mkdir /etc/adobe
echo "OverrideGPUValidation=false" > /etc/adobe/mms.cfg
echo "EnableLinuxHWVideoDecode=0" >> /etc/adobe/mms.cfg
exit
pkill -f flashplayer
firefox http://www.youtube.com/watch?v=IytNBm8WA1c
```also a 1.5Ghz P4 cpu does not meet the requirements for flash on Linux
[http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)
> 
[LIST]
[*] 2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
[*] Red Hat® Enterprise Linux (RHEL) 5.6 or later (32-bit  and 64-bit), openSUSE® 11.3 or later (32-bit and 64-bit), Ubuntu 10.04  or later (32-bit and 64-bit)
[*] Mozilla Firefox 4.0 or Google Chrome
[*] 512MB of RAM; 128MB of graphics memory
[/LIST]


---

### Post by crs501 on 2012-02-13
Thanks for your response. I see what you mean about my computer not meeting the system requirements for Flash 11. If that is the case, then what good can come of running the code you provided? Until I know what it will do and how to reverse it (should I need to) I'm hesitant to make any changes, as long as I have something in place that does work, albeit on a limited basis!

---

### Post by pqwoerituytrueiwoq on 2012-02-13
to undo it 
```
sudo rm /etc/adobe/mms.cfg
pkill -f flashplayer
```

that code i posted will disable hardware decode acceleration in flash (which seems unstable for me)
but odds are it is disabled on your system as it is anyway but i figured it would be worth a try

---

### Post by crs501 on 2012-02-15
Since I am now aware that my real problem is that my old computer does not meet the System Requirements for Adobe Flash Player 11 - I am going to mark this thread as solved and close it out. Thanks to anybody who read it and to those who tried to help!!! Richard...

---

