---
title: "Gforce 6150le and garbled screen with nvida drivers"
date: 2010-01-11
forum: General Help
---

### Post by jdjones on 2010-01-11
I just switched from xp on a HP s7613w (gforce 6150 le) to ubuntu 9-10. I can not see anything over 800x600 to select unless i enable the nvida drivers. There are three choices and i have tried them all, After i activate them it will let me select the 1024x768 that i need but the screen is garbled. There will be garbled text till i run the curser over the text then it will stratin up. The buttons on a page will move down and to the right a little bit when i put the cursor over them. When i uninstall the nvida drivers everything goes back to 800x600 and the screen is fine. My monitor is a Sceptre X20 is that helps. I am new to linux so please use easy to follow instructions if you can help me. I tried pc linux and it did the same thing. I like this version better so i am going to try to get it to work. Thanks

---

### Post by jdjones on 2010-01-12
If there is no fix for this can someone suggest a version of Linux that will work with the nvida Gforce 6150le The box is an hp with Sempron (M) 3400+ W/1.8 gig ram. the reason im going with a new os is because XP will not authenticate and i am not going jump trough hoops to get permission from Gates to use software i paied for. I did that about a year ago and it took two or three days, Im not doing it again. If nothing else i guess i can use it for a 180 gig storage drive.

---

### Post by Tourdog on 2010-01-12
JD,
Look at my specs below and you'll see we have similar gear.   My screen comes up on 800 x 600 and I simply change it to 1280 x 1024.  It is razor sharp in all cases................ except I haven't figured out the Totem video yet.  Youtube plays clear but paid-for DVDs are still scrambled.   In other words ALL video is clear and sharp except for the DVDs.  Now if I could figure out how to change the Nvidia default to come up on 1280 x 1024?!

---

### Post by jdjones on 2010-01-12
Thank you for the reply, i will download that and give it a shot in the morning. I will post back what happens. Crossing my fingers.

---

### Post by jmszr on 2010-01-12
@Tourdog,

This Howto should be of help with your DVD issue: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) .

@jdjones,

Perhaps you'll find something here: [http://ubuntuforums.org/tags.php?tag=screen+resolution](http://ubuntuforums.org/tags.php?tag=screen+resolution) .

---

### Post by Tourdog on 2010-01-12
JM  
Thanks !  I was just over there and I have a couple sudos to work with now !   :)

---

### Post by jdjones on 2010-01-14
ok just figured out that Karmic Koala is the same thing as ubuntu. Im still stuck. I just tried it on an old E machines T-1840 with a celeron 1.8 with 1.2gig ram with an (845GL) controller and it works perfect so its not the monitor, woe is me. There has to be some version of Linux that will work with the Nvida 6150. Im off to Google to do some more searching.

---

### Post by Tourdog on 2010-01-14
jd,  (this info is really more pertinent for JM, just trying to help, not hijack a thread)
Here is a chronology of what worked for me:

 Smile  Re: Playing DVD's in Ubuntu 9.10 64-bit
I want to amplify the previous post:            filed DVD success  13 Jan 10

Here are the steps that finally worked for me:

1.
Quote:
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
2.
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar

3.
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 vlc


I did not run the 3rd sudo because those files were already showing installed using Synaptic. ( VLC media player had been installed basically to check against Totem.)

Both Totem and VLC would scramble, then lose (crash) within a minute upon playing a paid-for DVD. I went ahead and ran the 3 rd sudo and "voila"! (Ran, meaning right over the top of the same files)

Both Totem and VLC now play beautifully any DVD that we have. Video and sound have no shortcomings. Perfect!

So far I only see a long wait for BBC and downloads therein but YouTube is very fast considering our 2.4 gighertz wireless connect to a rural tower some 2 1/2 miles away plus my in house wifi (g) for broadband. This ISP can bog down to 1 mbit/s thru-put but normally is from 3 to 5 mbits/s with 30 m/s latency.

The first 2 sudos are available on the "MultiMedia & Video".................. (sticky) of this forum plus many postings (this thread).

Now for some reason I cannot find the "button" on either Totem or VLC to "eject" the DVD?! (Greyed out)  I use the "Terminal" to open it....... works!

Thanks to all who have helped out
__________________
Tourdog

HP 1630 desktop, 250 gig hd, Nvidia Gforce 6150, 2 gigs, Dual boot 9.10 Karmic Koala or XP. Tried Knoppix, then 9.10 Netbook Remix and have settled on Karmic 64 bit.
Last edited by Tourdog; 1 Minute Ago at 11:46 AM.. 

HTH   :)

---

