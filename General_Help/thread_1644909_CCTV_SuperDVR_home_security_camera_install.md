---
title: "CCTV SuperDVR home security camera install?"
date: 2010-12-13
forum: General Help
---

### Post by at100plus on 2010-12-13
Has anyone gotten a DVR card to work with Zoneminder?

I have a chinese DVR card in a Windows Box running 8 Cameras on software called SuperDVR.

It seems all of these camera cards are the same, some made by Avermedia,  or QSee.  My card actually came with SuperDVR software that didn't work  properly, the documentation was obviously bad chinese translation and I  had a really tough time getting it to work on the Windows box  initially.  Finally I found that it just won't work with Windows 7 or 64  bit, so I reinstaled WinXP 32 bit onto the box and found an upgraded  SuperDVR software on the QSee camera driver website.

Anyway,

I've started using Ubuntu exclusively and would love to make the switch to Ubuntu for my Camera box.

Anyone done this? 

I'm wondering if Ubuntu will recognize the camera card.  It's basically a  TV tuner card, has 2 plugs that allow BNC pigtails to be input.

I was even thinking maybe running Virtual Box ontop of Ubuntu and run the DVR in Virtual XP.

I'd really like to take advantage of the 64 bit hardware, so I was  thinking about running Ubuntu Server 10.10 64 bit on this machine, is  that a bad idea?

---

### Post by tredegar on 2011-01-11
The post above, by exactsecurity is SPAM. (Edit: The spam post has now been removed by the Mods /Edit)

Meanwhile, try this [link]("http://www.howtoforge.org/forums/showthread.php?t=50199")

---

### Post by freestyle45 on 2011-03-31
Don't know if you've moved on from this.... but....

I have a Q-see card like you're describing, which runs on a Techwell chip... mine is a TW-6800.  I tried for a LONG time, and I was never able to get Linux to recognize it as a video device.  The latest SuperDVR software on Q-see's site for Windows is actually pretty slick though -- light years ahead of the crap that came in the box with the card, and frankly, even more user friendly than Zoneminder.

I have a 2nd capture card based on a Conexant BT878 chip that runs very well in Ubuntu/Zoneminder, using the BTTV driver.

Where Zoneminder really stands out is when you're mixing and matching different type of cameras with different resolutions and inputs, or if you simply want really high resolution.  What I've ultimately found out is that BNC/Composite video cables can never quite produce a REALLY crisp 640x480 picture, regardless of how much money you throw at the cameras.

If you want my advice, get a pair of fifty dollar Logitech C310 webcams from anywhere (automatically detected by Ubuntu).  Then get yourself a pair of 30 foot ACTIVE USB extension cables for fourteen bucks a piece on Amazon.  It's a cinch to get both of them running in Zoneminder, and then you've got a high-definition surveillance system recording at 720p.  Mine can read license plates from 50 feet away.  Screw the framerate; it's not important for security.

---

### Post by at100plus on 2011-04-28
Thanks for your input.  I have a lot invested in my current analog cams and the wiring so I guess I'll either have to find a capture card that works or stick with Windows for now, I still want to learn Zoneminder though so I may try 1 of those usb cameras or maybe an ip camera on another box.

---

### Post by sl44n3sh on 2011-05-04
> **freestyle45 said:**
> 

If you want my advice, get a pair of fifty dollar Logitech C310 webcams from anywhere (automatically detected by Ubuntu).  Then get yourself a pair of 30 foot ACTIVE USB extension cables for fourteen bucks a piece on Amazon.  It's a cinch to get both of them running in Zoneminder, and then you've got a high-definition surveillance system recording at 720p.  Mine can read license plates from 50 feet away.  Screw the framerate; it's not important for security.

Hi,
I am trying to set up a Logitech C310 webcam with Zoneminder but I don t succeed. Ubuntu recognizes the cam, cheese and xawtv work fine.
I also tried to use mjp-stream and set it up as remote cam but I still can t get it to work. And I would prefer to use it as local cam.
If you could tell me how you got the C310 working it would really help.
Thank you.

---

### Post by no2498 on 2011-05-04
i know this is not the same cam you have but it may help you

[http://www.zoneminder.com/forums/viewtopic.php?p=63801](http://www.zoneminder.com/forums/viewtopic.php?p=63801)

---

### Post by at100plus on 2011-05-06
> **freestyle45 said:**
> Don't know if you've moved on from this.... but....

nder.

I have a 2nd capture card based on a Conexant BT878 chip that runs very well in Ubuntu/Zoneminder, using the BTTV driver.



Was just rereading your post.  Where did you get this card?   How would I find one and know it's a BT878 card?

---

### Post by J2897 on 2011-06-15
> **at100plus said:**
> Was just rereading your post.  Where did you get this card?   How would I find one and know it's a BT878 card?Click [here]("http://www.camsecure.co.uk/Zoneminder.html"). They're featured in the [ZoneMinder Shop]("http://www.zoneminder.com/shop").

---

### Post by J2897 on 2011-06-15
> **sl44n3sh said:**
> Hi,
I am trying to set up a Logitech C310 webcam with Zoneminder but I don t succeed. Ubuntu recognizes the cam, cheese and xawtv work fine.
I also tried to use mjp-stream and set it up as remote cam but I still can t get it to work. And I would prefer to use it as local cam.
If you could tell me how you got the C310 working it would really help.
Thank you.If someone wrote a guide on **how to get the Logitech C310 working in ZoneMinder**, that would be awesome!!! [-o<

---

### Post by aaronLund on 2011-08-09
> **freestyle45 said:**
> 

If you want my advice, get a pair of fifty dollar Logitech C310 webcams from anywhere (automatically detected by Ubuntu).  Then get yourself a pair of 30 foot ACTIVE USB extension cables for fourteen bucks a piece on Amazon.  It's a cinch to get both of them running in Zoneminder, and then you've got a high-definition surveillance system recording at 720p.  Mine can read license plates from 50 feet away.  Screw the framerate; it's not important for security.

Does Zoneminder play nice with a multiple usb webcams?

Not too sure why but I was under the assumption that multiple webcams (say 4?) doesn't bode well with most OS-es.

If it does work, I'd like to do 4 of those Logitech C310 cameras using 10.04 and Zoneminder.  Would that really work?

Good thread.

---

### Post by aaronLund on 2011-08-09
Also, in regards to another Logitech cam, the guy who did this blog: [http://www.r3uk.com/index.php/home/37-hardware/96-the-weatherproof-webcam](http://www.r3uk.com/index.php/home/37-hardware/96-the-weatherproof-webcam)

....mentions that using the camera with the usb extenders seem to deliver poor performance and had to be scrapped (?? I think).

Either way, it's not the camera in question (it's the Logitech 5000) so perhaps that's the issue?

Thanks.

---

