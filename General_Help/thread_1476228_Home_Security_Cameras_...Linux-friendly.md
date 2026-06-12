---
title: "Home Security Cameras ...Linux-friendly?"
date: 2010-05-07
forum: General Help
---

### Post by Th3Professor on 2010-05-07
I'm looking for home security cameras that work with Linux as well as (hopefully) a secured internet connection. ...it'd be nice if they work indoors, outdoors, have concealed night vision, motion detection, or any kind of bells and whistles. Though, a basic but clear video type of camera works too. Thanks for any input! :D

---

### Post by WinterRain on 2010-05-07
[Zoneminder]("http://www.zoneminder.com/") runs on linux.

Feature List

	Runs on any Linux distribution!
	Supports video, USB and network cameras.
	Support Pan/Tilt/Zoom cameras, extensible to add new control protocols.
	Built on standard tools, C++, perl and php.
	Uses high performance MySQL database.
	High performance independent video capture and analysis daemons allowing high failure redundancy.
	Multiple Zones (Regions Of Interest) can be defined per camera. Each can have a different sensitivity or be ignored altogether.
	Large number of configuration options allowing maximum performance on any hardware.
	User friendly web interface allowing full control of system or cameras as well as live views and event replays.
	Supports live video in mpeg video, multi-part jpeg and stills formats.
	Supports event replay in mpeg video, multi-part jpeg, stills formats, along with statistics detail.
	User defined filters allowing selection of any number of events by combination of characteristics in any order.
	Event notification by email or SMS including attached still images or video of specific events by filter.
	Automatic uploading of matching events to external FTP storage for archiving and data security.
	Includes bi-directional X.10 (home automation protocol) integration allowing X.10 signals to control when video is captured and for motion detection to trigger X.10 devices.
	Highly partitioned design allow other hardware interfacing protocols to be added easily for support of alarm panels etc.
	Multiple users and user access levels
	Multi-language support with many languages already included
	Full control script support allowing most tasks to be automated or added to other applications.
	Support external triggering by 3rd party applications or equipment.
	xHTML mobile/cellular phone access allowing access to common functions.

---

### Post by Th3Professor on 2010-05-10
Thank you for your reply, **WinterRain**. It is greatly appreciated!

I'll try Zoneminder out.

It looks like it supports the ability to record video for playback (viewing later) and also live monitoring from a remote source via the internet, is that right?

> **WinterRain said:**
> Uses high performance MySQL database.
User friendly web interface allowing full control of system or cameras as well as live views and event replays.
Automatic uploading of matching events to external FTP storage for archiving and data security.
Support external triggering by 3rd party applications or equipment.
xHTML mobile/cellular phone access allowing access to common functions.

I'm guessing that by "3rd party" that it means that particular software does not have external triggering features built-in?

Also, your message says it supports video/USB/network cameras...

I'm looking for some good security cameras - the actual hardware - that I can use.

Are there any recommendations or suggestions?

One will be placed in a window and aimed outside where vehicles are parked.

One will be placed somewhere inside and aimed at the main door.

I would like for them to have:

* night-vision if at all possible
* motion detection (only if possible, this is optional)
* a fairly decent range/distance
* a clear nonpixelated video (for either playback and/or live viewing (via either the home computer or live via a web browser))
* quick response time to motion/movement (not "delayed")

I'm not sure what kind of actual home security cameras (the hardware) would be worth getting. I've done research on this but haven't really made much headway.

---

### Post by no2498 on 2010-05-10
go to the site and read it
it is free
you can get better elsewhere $ talks
use windows for free

---

### Post by Th3Professor on 2010-05-11
> **no2498 said:**
> go to the site and read it
it is free
you can get better elsewhere $ talks
use windows for free
What is that an advertisement for a reply? I don't understand what you are trying to say with your message. It is unclear. It is confusing. I did go to that site, and I did read it. Yes that software is free. And yes, I am sure "better elsewhere" if I pay for something else. And what's this about "use windows for free"?

Did you read my previous message?

I am asking about home security cameras, hardware, the devices I buy, not the software... not the windows operating system.

Cameras. Hardware.

Thank you.

Anyway, if anybody has any input I'd greatly appreciate it. Thanks!

---

### Post by Aimay on 2010-05-11
> **Th3Professor said:**
> What is that an advertisement for a reply? I don't understand what you are trying to say with your message. It is unclear. It is confusing. I did go to that site, and I did read it. Yes that software is free. And yes, I am sure "better elsewhere" if I pay for something else. And what's this about "use windows for free"?

Did you read my previous message?

I am asking about home security cameras, hardware, the devices I buy, not the software... not the windows operating system.

Cameras. Hardware.

Thank you.

Anyway, if anybody has any input I'd greatly appreciate it. Thanks!
hi, friend. I know rarely about Home Security Cameras. But you can check this [home security cameras]("http://ubuntuforums.org/home%20security%20cameras") site to search more. Hope this helps!

---

### Post by Th3Professor on 2010-05-12
> **Aimay said:**
> hi, friend. I know rarely about Home Security Cameras. But you can check this [home security cameras]("http://ubuntuforums.org/home%20security%20cameras") site to search more. Hope this helps!
Your link is this:
[http://ubuntuforums.org/home%20security%20cameras](http://ubuntuforums.org/home%20security%20cameras)
...did you mean to provide another link?

Does anybody know of home security type cameras - the hardware - that are compatible with software on Linux?

---

### Post by Th3Professor on 2010-05-15
Does anybody know of home security type cameras - the hardware - that are compatible with software on Linux?

---

### Post by StuartN on 2010-05-15
> **Th3Professor said:**
> Does anybody know of home security type cameras - the hardware - that are compatible with software on Linux?

Depending on your budget and required reliability, I guess the three options are (from cheapest)

1. As many USB webcams as you need. The longest run I tried was about 5 metres of USB cable including the hub. Check Video4Linux or other sites for the cameras, and test them with your software (I was using Motion).

2. The standard video home security cameras (Maplin etc) and a video converter to interface the video to your PC. There are a lot more options in terms of lighting, nightlighting, telezoom etc in video cameras. I think there are also hard-disk controller boxes that can be interrogated from a PC, with all the video interfacing and control in the box.

3. Some IP wireless or ethernet network cameras, most expensive, but easiest to locate and remotely control.

---

### Post by bumanie on 2010-05-15
Have a look at [motion]("http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome") - it is the program that runs on linuxmce for security camera control - there is a list of a number of [cameras that work]("http://alpha.dyndns.org/ov511/cameras.html") and there are more being coded for all the time

---

### Post by Th3Professor on 2010-05-23
Hi! I saw your replies... really busy lately but I'll be looking into the things you all have mentioned so far.

> **StuartN said:**
> Depending on your budget and required reliability, I guess the three options are (from cheapest)

1. As many USB webcams as you need. The longest run I tried was about 5 metres of USB cable including the hub. Check Video4Linux or other sites for the cameras, and test them with your software (I was using Motion).

2. The standard video home security cameras (Maplin etc) and a video converter to interface the video to your PC. There are a lot more options in terms of lighting, nightlighting, telezoom etc in video cameras. I think there are also hard-disk controller boxes that can be interrogated from a PC, with all the video interfacing and control in the box.

3. Some IP wireless or ethernet network cameras, most expensive, but easiest to locate and remotely control.
I'm not sure how dependable webcams are for use as "home security cameras".

I'd rather not have the limitation of X-length USB cable if that's at all possible. Though if it's a different kind of cable that plugs into an external box of some sort (which, in turn, might be USB-connected to the computer), that's okay. I will need to have flexibility of placement.

One camera will basically be in a windowsill aimed at my parking spot outside.

One camera will be in the opposite side of my home aimed at my main door.

> **bumanie said:**
> Have a look at [motion]("http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome") - it is the program that runs on linuxmce for security camera control - there is a list of a number of [cameras that work]("http://alpha.dyndns.org/ov511/cameras.html") and there are more being coded for all the time
Hmm, two people mentioning "motion". I'll definitely look into that.

That's a pretty big list of "cameras that work", I don't know where to start. :confused:

---

### Post by StuartN on 2010-05-23
> **Th3Professor said:**
> I'm not sure how dependable webcams are for use as "home security cameras".

I have had an ordinary Creative WebCam under a plastic cover outside my house for over a year. I sealed the microphone and snapshot button with mastic. I attached it by USB to a PC running motion to grab snapshots on change, and it records all I need for security monitoring the front of my home and parking area. If I had more serious needs, then I would add a second camera to capture licence plates and possibly identifiable faces, but I don't have that need.

In terms of resolution, webcams are good, but they are not hard-wearing and are not built for outdoors use. I would not put one where people could reach it, or in direct rain or sun.

> **Th3Professor said:**
> I'd rather not have the limitation of X-length USB cable if that's at all possible.

By chance, I was just ogling a review of the IP70 by Compro ([http://www.comprousa.com/en/product/ip70/ip70.html](http://www.comprousa.com/en/product/ip70/ip70.html)) and I am sure that there are other brands and models - for 90 GBP you get a web interface IP camera that serves 15fps at 1280 by 1024, and can save to FTP without intervention - and a built-in IR floodlight. It just needs power and wired ethernet. There are wireless ones that just require power.

I have seen other IP cameras by Cisco, D-Link and Axis before, outside the budget for my needs at 200-300 GBP.

You might want to install motion and buy the very cheapest webcam you can find to see how much you need to spend.

---

### Post by Th3Professor on 2010-05-24
> **StuartN said:**
> I have had an ordinary Creative WebCam under a plastic cover outside my house for over a year. I sealed the microphone and snapshot button with mastic. I attached it by USB to a PC running motion to grab snapshots on change, and it records all I need for security monitoring the front of my home and parking area. If I had more serious needs, then I would add a second camera to capture licence plates and possibly identifiable faces, but I don't have that need.

In terms of resolution, webcams are good, but they are not hard-wearing and are not built for outdoors use. I would not put one where people could reach it, or in direct rain or sun.



By chance, I was just ogling a review of the IP70 by Compro ([http://www.comprousa.com/en/product/ip70/ip70.html](http://www.comprousa.com/en/product/ip70/ip70.html)) and I am sure that there are other brands and models - for 90 GBP you get a web interface IP camera that serves 15fps at 1280 by 1024, and can save to FTP without intervention - and a built-in IR floodlight. It just needs power and wired ethernet. There are wireless ones that just require power.

I have seen other IP cameras by Cisco, D-Link and Axis before, outside the budget for my needs at 200-300 GBP.

You might want to install motion and buy the very cheapest webcam you can find to see how much you need to spend.

Thank you for the input!

I won't be buying cheap webcams this time around. I've been through plenty of them already and I'm pretty much finished with the cheap ones. It's time to upgrade to the more pricey camera for home security.

That Compro IP70 looks like it might be a good choice for my purposes. I'd like to compare it to similar cameras by those other brands (Cisco, D-Link, Axis, etc.). Hopefully the IP70 is compatible with Linux applications like Motion.

---

### Post by StuartN on 2010-05-24
> **Th3Professor said:**
> Hopefully the IP70 is compatible with Linux applications like Motion.

I don't think that you would have a problem with any IP camera in Motion because it is a driverless solution - in fact the camera serving to FTP may be a complete solution in itself. But, as far as I know, the ethernet-connected cameras all use very standard methods for passing frame data back to an application, and are easily configured.

There was a very good article in Linux User, perhaps 2-3 years ago, with a multiple (USB webcam and IP) camera setup. I don't remember if it used Zoneminder or Motion, but I remember Motion suited me better after reading it. It might be linked to off one of the websites:

[http://www.zoneminder.com/](http://www.zoneminder.com/)
[http://www.linuxscrew.com/2007/11/05/howto-home-video-security-with-zoneminder-and-ubuntu/](http://www.linuxscrew.com/2007/11/05/howto-home-video-security-with-zoneminder-and-ubuntu/)

[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)
[http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)

---

### Post by nickmcg on 2010-06-07
It's not necessarily the camera, but the video capture board.

I have 4 CCTV cameras connected to a generic 4-port bttv video card via coax cable, zoneminder on my ubuntu box.

The board does work, but not brilliantly - my fault, I bought a cheap chinese one!

Look at:
[http://www.faqs.org/docs/Linux-mini/BTTV.html](http://www.faqs.org/docs/Linux-mini/BTTV.html)
[http://www.linux.org/docs/ldp/howto/BTTV/hardware.html](http://www.linux.org/docs/ldp/howto/BTTV/hardware.html)
among others.

The longest run is 100m from computer to camera.

HTH

Nick

---

