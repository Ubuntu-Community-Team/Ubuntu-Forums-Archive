---
title: "Connecting Garmin Forerunner 405CX and Pytrainer to Ubuntu..."
date: 2010-05-16
forum: General Help
---

### Post by jjmil03 on 2010-05-16
Hello all! First post so here goes...

I am pretty new to Ubuntu and would like to try and get my Garmin Forerunner 405CX working with Pytrainer. I'm having a few problems however. First, when I try to import the data from my watch in Pytrainer using the GPS Babel, it tells me that I need an earlier version of GPS Babel, version 1.3.5 (1.3.6 is installed) Second, I installed Gebabbel to try and see if I could pull any data from it at all. It tells me that it can't access the watch to pull data. I did a lsusb command to see what was showing up for USB devices. It shows the wireless ANT stick as plugged in, though I can't connect to it. I've seen a few other posts on here about this, but I am pretty much lost so I figured I would just post this out here and see if anyone has a good guide on how to do it. One post mentioned a blacklist of some sort, but I didn't find any entries anywhere.

Some more random questions...

How do I know it has a driver for the Garmin watch? Where would I find it?

How do i see what port it is using? I've seen references to USB:TTY0 but have no clue as to how they found this out...I have the Gebabbel pointed to just usb:


I am using Lucid Lynx. And the Lynx is winning. Any help would be appreciated. 


Jon

---

### Post by MockY on 2010-05-24
I would like to know exactly the same.
I already have my Forerunner 305 hooked up and it works perfectly with pyTrainer. My wife bought a 405 for herself and I am now facing the same issue as you.

---

### Post by gabak on 2010-06-04
here it explain how to do it

[http://jhau.maliwi.de/linux/gpssw.html](http://jhau.maliwi.de/linux/gpssw.html)

---

### Post by CITS Fixed on 2010-07-20
I am ready to switch 100% to ubuntu/mint with zero windoze dependency if I can get my Garmin 405 and/or nike+ to work natively in linux.
 
So there is no way to do this in Linux with out the help of windoze running in virtual box??

---

### Post by McEye on 2010-09-06
This is how I got it to work on Lucid Lynx
 
 install pyTrainer (right now at version 1.7.1)
 install garmin-tools
 
 In pyTrainer go to GPS Plugins and select "Garmin via garmin-tools".
 
 Downloads all runs to pyTrainer.
 
 The heart rate is there too although I cannot see it under the heart  rate tab. Nontheless, it is present in the graphs, for instance when  comparing speed vs. heart rate.
 

 cheers
 -Mc-

---

### Post by jblance on 2010-10-31
The problem with the 405 Garmin units is they connect via ANT+ (a wireless protocol) so they do not show up as USB devices (well in the same way)

The only way I have found to get the data from these devices is using a tool called gant [http://cgit.get-open.com/cgit.cgi/gant](http://cgit.get-open.com/cgit.cgi/gant)

You need to compile it (follow the instructions in the readme)

Once you have gant working it will download from the 405 and create TCX files for each activity.

These can be imported into pytrainer or Garmin's online tracker etc.

---

### Post by p5yc071c on 2011-01-03
Has anyone figured out how to make Pytrainer use Gant?  Maybe a newer version of Pytrainer?

---

### Post by KendrickHamilton on 2011-01-05
I tried the version of gant posted in the previous link with my 405 (not 405cx) but it did not work my 64bit linux systems. I downloaded a copy from:

[https://forums.garmin.com/showthread.php?t=9799](https://forums.garmin.com/showthread.php?t=9799)

That version works on my system. I found out I needed the auth405 from the other unit and I could not have spaces in the name when pairing. 

Some times you need to restart gant. There is also a python monitor you can run. Again, most of the time it works; sometimes you need to restart.

Once the download from your garmin is finished, you will have one or more TCX files. In pytrainer:

select tools->plugins
enable garmin training center file v2
file import from garmin file v2 and select the TCX file

---

