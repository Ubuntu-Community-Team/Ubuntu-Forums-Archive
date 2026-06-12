---
title: "Picture on TV is too big"
date: 2010-11-02
forum: General Help
---

### Post by simonxy on 2010-11-02
I'm new to linux - do you know for some good book or pdf with basics of linux?
Do you have some url?

I have bought new zotac mini PC ZBOX HD-ND22:
[http://www.zotac.com/index.php?option=com_wrapper&view=wrapper&Itemid=100082](http://www.zotac.com/index.php?option=com_wrapper&view=wrapper&Itemid=100082)

I have installed the last Ubutnu version 10.10 (64bit) and connected Zotac to Panasonic plazma TV, 42". 
The problem I have is that the picture is a little too big to be seen on TV - I don't see menus. If I go into the settings I can change the resolution to smaller(default is 1280 x 800), but the picture is always little too big, no matter of resolution.
How can I repair that?
Should I install some other drivers - I get only windows drivers with my zotac computer and I even don't know if there exists some special drivers for linux. Currently installed drivers are default nvidia drivers already included in ubuntu.

Please help.

Thank you,
Simon

---

### Post by timgood on 2010-11-02
If you are using the latest NVidia drivers, you can use 'overscan compensation' to adjust the picture to fit inside your TV screen. To do that go to System/Administration/NVIDIA X SERVER SETTINGS and click on 'DFP 0' which you will find under the GPU 0 tab.

There you should see a setting for Overscan Compensation: drag the slider until the picture fits inside the TV. (picture here:) [IMG]http://eekageek.co.uk/uploads/images/Screenshot-NVIDIA%20X%20Server%20Settings.png[/IMG]

Robert should now be your father's brother. Hope this helps.

---

### Post by simonxy on 2010-11-02
Thank you very much for your answer. I'll try that as soon as I come home.

I bought zotac only for downloading torrents and watching movies.
I installed xbmc on ubuntu for playing movies, but the picture is not quite ok. 
At the top of the screen there is some bending line from time to time.
I tried with DVD and Mkv movies, both the same result.

Should I change some settings in ubuntu, maybe add some codecs or different drivers?
Or maybe try with different movie player?

Do you have some suggestion?

Best regards,
Simon

---

### Post by timgood on 2010-11-03
I have a similar set up using an Acer Aspire Revo - same processor and chipset (NVidia ION graphics). I have installed XBMC standalone and changed the bios settings to allow more memory for the graphics. I get great results from streaming video and music. No judder or lines. XBMC allows you to adjust overscan compensation within the settings tab.

The standalone version does not require loading within an existing OS, freeing up more resources for what it does best - playing media.

You can find out more about XBMC standalone [here]("http://xbmc.org/team-xbmc/2009/12/24/xbmc-9-11-camelot/").

Hope this helps.

---

### Post by simonxy on 2010-11-03
[FONT=Verdana][SIZE=2][SIZE=2]Hi,

thank you for your suggestion, I'll look for bios setting - do you know exactly what is the name of this setting?
Yes, Zotac has the same grafic chipset as Acer Aspire, but it has different processor - [FONT=Arial]Intel®  Celeron® SU2300 (dual-core) (1.2 GHz). - thay said it's better than atom.

[/FONT]Maybe there is some problem because of new processor - XBMC is optimized for atom procesors and Ubuntu also doesn't recognize it - because there is some different name if I go to system info.
[/SIZE][FONT=Arial][SIZE=2]
About XBMC, first, I installed standalone XBMC as you did, but there is no web browser and torrent client there. Without this, XBMC is useless for me, because I don't have another computer turned on 24h/day to download torents. I would like to do that with Zotac, because it is turned on all day with low power consumption and therefore ideal also for torrent downloading. I don't understand why XBMC and other similar media centers don't have option for search and download torrents - it's cruical if you want to watch movies - because first you must get them :)

So, I formatted disk and installed last Ubuntu version 10.10 and on top of it I installed XBMC.
In ubuntu I search for torrents with firefox, than use transmision(wich is included in ubuntu) for download [/SIZE][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=2][FONT=Arial][SIZE=2] them [/SIZE][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=2][FONT=Arial][SIZE=2](unfortunatelly, there is no uTorent for linux which works much faster in windows than transmission in ubuntu - i don't know why) and than I open XBMC to watch movies (while some torrents are still downloading in background). What I miss here is simple switching between ubuntu and xbmc. If I want to go from xbmc back to ubuntu I must close xbmc and than open it again when I go back. That is very uncomfortable. Is there some ALT+TAB option or something similar?

If I would use zotac just for watching movies and have another computer for downloading them(torrents), than I would buy popcorn instead of zotac, which has hardware specialized just for watching media. And is much better, it works also with 128mbit/s movies while on the other hand zotac works without problems only with 20mbit/s. But for now all mkv movies are 9 mbit/s, so 20Mbit/s is more than enough.

[/SIZE][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=2][FONT=Arial][SIZE=2]Do you have some better solution for my needs, some other combination?[/SIZE][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=2][FONT=Arial]

[/FONT]For some reason movies sometimes flicker and I don't know why. I hope bios setting will repair this. Maybe i don't have right codes or should I install some different program, maybe KMpalyer or any other idea?[/SIZE][/FONT]

Thank you for your help,
BR
Simon

---

### Post by timgood on 2010-11-03
This [thread]("http://forum.xbmc.org/showthread.php?t=61574") describes how to install Transmission into XBMC standalone. I believe you can also install Firefox. The xbmc forum is a good place to start - and there will probably also be someone there with the same hardware you have.

Hope this helps.

---

### Post by simonxy on 2010-11-03
Do you maybe know which would be the right version:
[http://openelec.tv/index.php?option=com_jdownloads&view=viewcategory&catid=25&Itemid=307](http://openelec.tv/index.php?option=com_jdownloads&view=viewcategory&catid=25&Itemid=307)

ION build is optimized for atom procesor - so not right procesor for me.

Intel build -the right procesor but not right graphic chipset.

I guess I should install ION build 64bit but I'm not sure.

br,
Simon

---

### Post by timgood on 2010-11-04
I would go for the ION build. I have no experience of OpenElec though, only xbmc. Why are you going for this, which is unstable, rather than xbmc camelot?

---

### Post by simonxy on 2010-11-04
Some people on net says that this version works better for them - I just want to try and test if that is true.
The problem is, that I can't find out why the picture sometimes flickers - today I'll try also with 32bit version of xbmc life from USB key (currently I have 64bit ubuntu and on top of it xbmc).

br, Simon

---

### Post by timgood on 2010-11-04
On the Revo, there is a setting in the bios under Advanced Chipset Features called iGPU Frame Buffer Detect. This is normally set to auto. You can change this to manual and then change the iGPU Frame Buffer Size to 512Kb. You will need at least 2Gb RAM to do this. With this setting changed and using VDPAU, even my single core Atom processor will give me 720p output without judder or delay.

Perhaps there is a similar setting for your hardware? XBMC comes with the ION drivers, you can set XBMC to use VDPAU and it does not matter what processor you are using. This should eliminate your graphics problems.

---

### Post by simonxy on 2010-11-05
Hi,

ubuntu 10.10. 64bit and dharma on top of it doesn't work well with my hardware.
I know that for sure now because I have instaled old xbmc 9.11 live version without ubuntu and the picture is enormous better than it was before.
Sharp, clear and no stutters or flickers. But this old version doesn't have so much plugins,... so i would like to have dharma.

I guess that dharma didn't work well because I had 64bit version of ubuntu. Maybe i should try 32bit version, what do you think? Also default media player in ubuntu had the same bad results. Maybe i need some different codecs to install or drivers? From zotac I got only windows drivers. Any suggestions?

Thank you very much for your help. I asked also on xbmc forum, but no answer yet.

I found some similar post on some other forum, also with no answer:"The graphics overlay system on Dharma doesn't run as smoothly as it  does with Camelot. The new features on Dharma are awesome, but a quite a  few files in my video library are playing as smoothly as they were  in Camelot. "

Regards,
Simon

---

