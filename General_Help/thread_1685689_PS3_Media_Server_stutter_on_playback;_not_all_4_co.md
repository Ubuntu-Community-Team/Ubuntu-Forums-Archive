---
title: "PS3 Media Server stutter on playback; not all 4 cores utilized?"
date: 2011-02-11
forum: General Help
---

### Post by veroslav on 2011-02-11
Hi all,

 
I am trying to set up and use PS3 Media Server (latest version, 1.20.412  Beta) on my new computer, and while it manages to find and stream HD  quality videos (720p and 1080p) to PS3, the stuttering is horrible. I  cant play even 3 seconds of video without the stutter.

The computer has an Intel 2.80 GHz i7 (4 cores) processor, which I think  should be more than enough for the transcoding. I have a wireless  router for the transmission between the computer and PS3 (I think the  router has 10/100 upload/download rate or something like that, not sure  on this one).

What could be the cause to the stuttering issue? My wireless router?  I've also read that it might be the fact that mencoder does not utilize  all of the cores for the encoding but only one, could this be the reason  as well? And if yes, how can I fix it? Where could I check how many  cores are actually used during the transcoding?

Anything else you suggest I might try to fix this problem?

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by mcduck on 2011-02-11
A wireless network isn't enough to transmit the encoded HD video. (after encoding it uses very low compression for comaptibility, which requires a fair amount of bandwidth) Connect the computer & PS3 to your router using Ethernet cable and the stuttering should disappear.

(the 100MB/s speed would be for wired network, the wireless connection gets nowhere near that)

Alternatively you can limit the quality of the video to suitable level for the bandwidth you have, although that option does have some problems and you'd have to limit the quality pretty much for a wireless connection.

(The amount of cores PS3 Media Server can use is configured on the Transcoding Settings-tab, under Common Transcoding Settings. Bandwidth limitation option is in the same place.)

---

### Post by veroslav on 2011-02-11
Thank you for your reply, mcduck. It has been informative.

I will try to fix a wired connection between the PS3/Router/Computer and see if it goes better (as it should) and also check the PS3 Media Player settings, if everything is ok.

Thanks again.

Kind Regards,
Veroslav

---

### Post by ruthlessrealm on 2012-02-20
I had the same problem for the longest... I finally figured it out, on my setup at least. I also have the i7, the way I figured it out was I downloaded a gadget for Windows called All CPU Meter (not for this reason, but it's what made me notice what was happening) and noticed that when I was streaming my all 8 Cores of my CPU were maxing out for every studder, until the PS3 video completely freezes and the cores are all completely stuck at 100% until I restart the PS3 Media server in services. Try this I hope it helps, Open PS3 Media Server program-> go to the Transcoding Settings. Look at the setting that says "Number of cores used for transcoding (it seems you have 8), (just don't set it to use all Cores cut the amount to use in half) my setting was at 8, I changed it to 4-> click save-> restart server-> also if you have it installed as a service you might also want to go to services and restart the PS3 media server service-> then vuala no more studdering, and now the cores don't even come close to being stressed. Another thing I did was went to services (click the Windows logo bubble and type services) open services-> scroll to the "Quality Windows Audio Video Experience"- double click and set to Automatic-> click Start. I've been off and on working on this issue for months, and got sick of hooking my PC directly to my TV. Although those of you using Wireless G might have a problem, my peak bitrate was 64Mb/s, and Wireless G maxes out at 54Mb/s so you might want to wire your PC via ethernet. The movie I streamed was a 1080P .MKV IMAX movie using the MEncoder as the Video file Engine.

Thought I'd mention, my PC is running wireless while my PS3 is wired, I will setup the PS3 wireless as well and report back if the studder also stops happening when the PS3 is set to wireless.

---

