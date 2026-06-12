---
title: "Problems with wireless speed, heat and HD video playback."
date: 2010-05-19
forum: General Help
---

### Post by 300Z on 2010-05-19
I'm experiencing severe wireless speed drop while using torrent, it's so bad to the point where no web-page will load on either chrome or firefox but ktorrent will still work fine (occasionally it will slow down as well but not often), but if I close ktorrent everything gets back to normal. I'm using ktorrent instead of transmission because transmission is even worse.
Any clues what could be causing this?

Another problem is heat, listening to music and web-browsing temps stay around 54 degrees but if I watch any videos the temperatures will spike to anywhere above 60 to as high as 78 (82 on the second core) degrees. If no programs are running the temps will drop to ~38-40 degrees. I can hear the fans working fine and I have cleaned all the air vents but that didn't help and this temperature issue doesn't happen while running windows7. 

Playing HD video is also being a problem, some 720p videos will play fine but others will stutter (not terribly) and CPU usage will reach 100%.
I have the video driver installed that I downloaded from the ATI site.

My laptop is an Acer Aspire 5536, Athlon 64 X2 QL64 2.1ghz, 3bg of ram, ATI Radeon HD-3200 graphics and I'm running Ubuntu 10.04 64bit. Previously I was running 9.04 and didn't really had any of these issues. :(

This is just frustrating. :(

---

### Post by Lord.Quackstar on 2010-05-19
Torrents are bandwidth hogs. You could try setting the priority lower, but it might not be just on your end. Router's and bandwidth limitations bight be the issue here. If you want, you can try using QoS in your router.

Flash is the issue with overheating. Tried going back a version?

---

### Post by 300Z on 2010-05-19
The wireless speed problem also happens when no torrent is actually active, just starting ktorrent the wireless speed will drop.

Never heard of QoS. :confused:

How do I go back to an older version of flash?

Thank you so far.

---

### Post by lovinglinux on 2010-05-20
> **300Z said:**
> I'm experiencing severe wireless speed drop while using torrent, it's so bad to the point where no web-page will load on either chrome or firefox but ktorrent will still work fine (occasionally it will slow down as well but not often), but if I close ktorrent everything gets back to normal. I'm using ktorrent instead of transmission because transmission is even worse.
Any clues what could be causing this?

You need to setup your UPLOAD limit to 80% of your actual UPLOAD bandwidth limit, otherwise the torrent traffic will clog your network and even making the browser unusable. Since it seems you also have the problem with the connection being dropped, then this symptom would be more pronounced. See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

> **300Z said:**
> Another problem is heat, listening to music and web-browsing temps stay around 54 degrees but if I watch any videos the temperatures will spike to anywhere above 60 to as high as 78 (82 on the second core) degrees. If no programs are running the temps will drop to ~38-40 degrees. I can hear the fans working fine and I have cleaned all the air vents but that didn't help and this temperature issue doesn't happen while running windows7. 

Playing videos can be a very CPU intensive task, depending your hardware (specially graphics card), but as already stated, flash based videos are the worse. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **300Z said:**
> Playing HD video is also being a problem, some 720p videos will play fine but others will stutter (not terribly) and CPU usage will reach 100%.
I have the video driver installed that I downloaded from the ATI site.

My laptop is an Acer Aspire 5536, Athlon 64 X2 QL64 2.1ghz, 3bg of ram, ATI Radeon HD-3200 graphics and I'm running Ubuntu 10.04 64bit. Previously I was running 9.04 and didn't really had any of these issues. :(

I don't know about ATI cards, but could be an issue with the driver/ubuntu version combination.

Anyway, HD videos are CPU intensive if you don't have a video card that support hardware decoding, since the processing would be done by the CPU instead of the GPU.

BTW, I would recommend creating separate threads for each of your issues next time.

---

### Post by 300Z on 2010-05-20
> You need to setup your UPLOAD limit to 80% of your actual UPLOAD bandwidth limit, otherwise the torrent traffic will clog your network and even making the browser unusable. Since it seems you also have the problem with the connection being dropped, then this symptom would be more pronounced. See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

I always set my upload bandwidth limit to ~70%, so I don't understand what's causing this but I'll try the suggestions on the link you posted.

> Playing videos can be a very CPU intensive task, depending your hardware (specially graphics card), but as already stated, flash based videos are the worse. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Funny you linked that because that's what I used to do on my old computer but had forgotten about... I'll try it and see if it helps.

> I don't know about ATI cards, but could be an issue with the driver/ubuntu version combination.

Anyway, HD videos are CPU intensive if you don't have a video card that support hardware decoding, since the processing would be done by the CPU instead of the GPU.

I think you may be right because everything seemed to work just fine under Ubuntu 9.04.
That and I just realized that "No proprietary drivers are in use" on >>Hardware Drivers. Even tho I installed the ATI driver downloaded from the ATI website. :confused:

> BTW, I would recommend creating separate threads for each of your issues next time.
I'll remember that next time.

Thank you.

---

### Post by 300Z on 2010-05-20
> **lovinglinux said:**
>  [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).
1 down 2 to go, wireless speed is back to normal. :)

Thank you.

---

### Post by 3Miro on 2010-05-20
I have had some bad experiance with Torrents + Wireless. When I use torrents, I prefer a wire.

You are not supposed to install proprietary ATI drivers downloaded form ATI. The correct method is to use the repository (the inbuilt Hardware drivers tool).

Flash under 64-bit can be a problem. Look around for optimizations and specific howtos, but my solutions have been:

Install Swiftfox, it is a 32-bit build so you can use the 32-bit flashplugin.so library from Adobe.

Install 64-bit flash.

Install flash-block addons for Firefox and Chrome. Many pages will load way too many flash apps/adds and this can really slow down the machine.

---

### Post by 300Z on 2010-05-20
> **3Miro said:**
> 
You are not supposed to install proprietary ATI drivers downloaded form ATI. The correct method is to use the repository (the inbuilt Hardware drivers tool). 
But this is how I have done and worked best on my machine in the past.

I already did all the flash tweaks that I could find and nothing has seem to have improved. :(
Worth mentioning is that I mostly use Chrome instead of firefox.
I just did a browser benchmark and this is result for chrome...
[IMG]http://i24.photobucket.com/albums/c31/CorradoVR6z/Screenshot.png[/IMG]
Firefox scored half of that. :/

I'm starting to wonder if my issue is the fact that I went from 32 to 64bit and 64 bit just isn't working so great on my laptop... I'm thinking about going back to 32bit.

---

### Post by 300Z on 2010-06-05
So I went back to 32bit and at first things seemed a little better but after a week of use I think it's about the same RAM use is a little less in some situations but at the same time if "feels" a little less responsive as well. :/

Now I'm having a problem with the Movie player were occasionally it closes by itself and wont't let me play any videos again on any players unless I restart the computer. :(

I think I may go back to 64bit since it didn't really fix any of the problems I was experiencing.

---

### Post by ario on 2010-12-17
> **300Z said:**
> I'm experiencing severe wireless speed drop while using torrent, it's so bad to the point where no web-page will load on either chrome or firefox but ktorrent will still work fine (occasionally it will slow down as well but not often), but if I close ktorrent everything gets back to normal. I'm using ktorrent instead of transmission because transmission is even worse.
Any clues what could be causing this?

Another problem is heat, listening to music and web-browsing temps stay around 54 degrees but if I watch any videos the temperatures will spike to anywhere above 60 to as high as 78 (82 on the second core) degrees. If no programs are running the temps will drop to ~38-40 degrees. I can hear the fans working fine and I have cleaned all the air vents but that didn't help and this temperature issue doesn't happen while running windows7. 

Playing HD video is also being a problem, some 720p videos will play fine but others will stutter (not terribly) and CPU usage will reach 100%.
I have the video driver installed that I downloaded from the ATI site.

My laptop is an Acer Aspire 5536, Athlon 64 X2 QL64 2.1ghz, 3bg of ram, ATI Radeon HD-3200 graphics and I'm running Ubuntu 10.04 64bit. Previously I was running 9.04 and didn't really had any of these issues. :(

This is just frustrating. :(

Did you finally solved the heat problem? I have the same problem.
this is the sensors output:
```
Adapter: Virtual device
temp1:       +57.0°C  (crit = +99.0°C)                  
temp2:       +50.0°C  (crit = +126.0°C)                  


```
and this is the hddtemp /dev/sda output:
```
/dev/sda: WDC WD3200BEVT-22ZCT0: 57°C
```
Every thing is really hot! I decided to not to use my laptop until I find the solution:(
Please help me!

---

### Post by 300Z on 2010-12-17
It's been running fine on Maverick with the latest ATI drivers (10.12 if I remember correctly).
I guess my initial problems where due to the video drivers that I used at the time. I started using Elive instead of Ubuntu for a while and went to Ubuntu with the release of Maverick and it's been fine ever since.

---

### Post by ario on 2011-01-21
> **300Z said:**
> It's been running fine on Maverick with the latest ATI drivers (10.12 if I remember correctly).
I guess my initial problems where due to the video drivers that I used at the time. I started using Elive instead of Ubuntu for a while and went to Ubuntu with the release of Maverick and it's been fine ever since.

After months of fighting with air conditions of my laptop, decided to not continue with solving heat problem and start a new way of using my laptop:
[LIST]
[*]My hard drive temperature never dropped 50 degrees. I know that this temperature will cause the hard drive to burn smoothly. Completely removed my hard-drive, put that in a USB box, and installed a new 10.10 system on a 16GB SD card. It's very disgusting, I know!
[*]Installing ATI propriety driver from either AMD website or Ubuntu repositories solved Alpha Blur issue with compiz, reduced power consumption from 30Watts to 15Watts, increased battery life from 1:30' to 2:50' and finally reduced CPU and GPU temperatures from 50,60 to 43,50. But it's still too hot.
[/LIST]
I think this model is as is, and although I paid for my laptop (It's not an Open Hardware project!), I must forget about using my hard drive and use the laptop with a slow SD card on it:(

---

