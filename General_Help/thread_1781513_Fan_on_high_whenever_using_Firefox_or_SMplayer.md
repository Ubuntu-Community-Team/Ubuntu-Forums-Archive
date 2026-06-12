---
title: "Fan on high whenever using Firefox or SMplayer"
date: 2011-06-13
forum: General Help
---

### Post by typos1 on 2011-06-13
For the last 6 months the fan has been on more and more whenever I m online or listening/watching media.

Its getting to the point where the computer is virtually unusale as the noise is so louod and stress inducing-I ve posted in FF and SMplayer threads but no one has offered any help-could some one suggest something as its getting silly ? Does my cache need clearing and if so how do I do it?

(it seems to be "plugin container" thats usually causing the problem, but if you stop it then things dont work properly)

Thanks

---

### Post by StrayEddy on 2011-06-13
Do as said in this link to set control for your fan speed:

[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)

---

### Post by doas777 on 2011-06-13
plugin-container in this case means flash. 

basically both apps (depending on your content of course) really tax your system, so be glad your fan is spinning up. if it wasn't you might just have a useless brick instead of a laptop. 

my advice is to blow out your vents, get a cooling plate, and keep your laptop on a hard flat surrface (and on the pad).
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834997340](http://www.newegg.com/Product/Product.aspx?Item=N82E16834997340)
(that is a very nice cooling plate, but you can find them cheaper).

if you want to monitor your temp, look into lm-sensors and hardware-sensors-applet:
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by typos1 on 2011-06-13
Thanks, I have recently cleaned out the dust and its a desktop, not a laptop.

I m getting this even if I m just browsing a forum with no flash stuff and I only thought flash was used on webpages with flash movies, not SMplayer playing an avi, for instance.

Wouldnt altering the fan speed just cause the system to overheat ? 

Something is wrong somewhere, I d rather sort it out than jsut turn the fan off, its only been the last 6 months its been happening, the previous 18 months with ubuntu it didnt happen.

Could it be the memory cache ?

---

### Post by inkrypted on 2011-06-13
If the fan is making more noise than it used to it could be an indication that the fan is going bad as activities like that put more stress on the system and require the fan to spin faster.

---

### Post by doas777 on 2011-06-13
well, since it;s a desktop (sry bout that) there are some things you can do, so thats good.

first off, lets get some temp readings to determine what component is so hot. check out the link on lm-sensors to get you started. if your issue is memory caching, then somthing is terribly wrong. 

if you have cleaned the box, then the next step is to make sure that the heatsink is well attached to the CPU, with a good amount of thermal paste (a good amount is the least possible).[http://support.amd.com/us/System-Building-and-Compatibility/Pages/ProcessorInstallationVideos.aspx](http://support.amd.com/us/System-Building-and-Compatibility/Pages/ProcessorInstallationVideos.aspx)

also muck about in the bios to see if you have any overclocking/power management settings. my Abit board has copious settings for fine tuning voltages and fan speeds. 

if all else fails, it;s time to look into a better heatsink cooler. 
[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=574&name=CPU-Fans-Heatsinks](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=574&name=CPU-Fans-Heatsinks)

I remember my PentiumD circa 2006. I had to put 7 fans in the box to keep it cool enough to run a full virus scan. I got rid of it in favor of a Core2Duo a year later.

---

### Post by retchid on 2011-06-13
Had a similar problem with a Hewlett Packard - which is the one I'm on now

would spin then slow and spin ........... drove me nuts

Simple solution  - in bios set fan option to constantly on - ok I can hear it but its not driving me nuts just constant background noise now  



If you don't know how to set the bios look it up!

---

### Post by typos1 on 2011-06-13
Ok, I ll try all that, but I thought the component that was hot was the processor, as I thought that was what the fan was there to cool.

I m going to assume that the thermal paste issue isnt a factor as I ve never removed the cpu, unless its degraded with time or something.

Also not changed anything in the bios, a similar thing happened over 2 and a half years of using windows, was all sorted when I stared using ubuntu, now its back again.

I m not exactly an expert, but I reckon its something to do with processes rather than hardware. If your car's rad fan kept coming on there would clearly be a problem with the engine making too much heat, so making the fan come on at a higher temp would nt sort the problem, just hide it.

Since FF4, I ve had the problem just posting on forums and as I said theyre usually without flash videos. Plus using any media player makes it happen now.

---

### Post by no2498 on 2011-06-14
this does happen 

I m going to assume that the thermal paste issue isnt a factor as I ve never removed the cpu, unless its degraded with time or something.

install htop type it in a terminal click enter it tells you how to install it
after installed type htop click enter
look to find what is hitting the cpu or memory

have you installed the flash aid plugin for fire fox and ran it ?

try the opera browser 

also for totem try setting the plugin to x window system no xv in gstreamer-properties

in a terminal type gstreamer-properties click enter
click video

that comes from the cheese help FAQ'S

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by typos1 on 2011-06-14
Installed htop, it seems to show the same info as the processes tab in system monitor, it shows firefox plugin container or SMplayer as taking up most cpu usage when on web pages or playing media, just like system monitor shows.

Tried changing to X Window System (No Xv) and X Window System (X11/XShm/Xv) but it makes no difference-it was on "autodetect before I changed it.

Does this mean that my gpu isnt working ?!

Will try the flash aid thing next.

---

### Post by no2498 on 2011-06-15
you may have needed to do a restart to see if this helped

Tried changing to X Window System (No Xv) and X Window System (X11/XShm/Xv) but it makes no difference-it was on "autodetect before I changed it.

no its working just not for video

flash aid is a plugin for fire fox look in tools type in flash aid install and then run it

---

### Post by typos1 on 2011-06-21
Think I ve sorted it-I cleaned out the pc about 9 months ago, but i didnt take the fan off the cpu's heatsink and there was masses of dust under it-removed it this time and cleaned it all out, problem sorted. Well noise has gone, cpu usage remains the same, I ll install the flash thing anyway as it sounds useful.

Thanks ! :)

---

