---
title: "Noob question with mplayer"
date: 2006-03-07
forum: General Help
---

### Post by Strumming Hippy on 2006-03-07
I'm sure someone else has had this problem and I'm sure someone knows the answer.  I've got mplayer... I've got the codecs... Firefox won't play embedded quicktime files using mplayer though.  AGGRAVATION!!! Oh yeah, this has been days of google walk-about with no results.  

"H" is for hurry, "E" is for 'e'-rgent, "L" is for love me, "P" is for p-p-p-p-p-please HELP!

-Galen

---

### Post by rm -rf *.* on 2006-03-07
Did you install the mozilla mplayer plugin?

```
sudo apt-get install mozilla-mplayer
```

I'm pretty sure you have to have the multiuniverse set up in your sources.list

/etc/apt/sources.list

Good luck.

---

### Post by Strumming Hippy on 2006-03-20
Got the Codecs, Got the Player, Got the Plugin.  Seems to be a problem because Firefox looks for the quicktime player and then freaks when it isn't there and decides not to even bother looking for mplayer.  Not at all sure what to do, but darn it's aggrevating.

---

### Post by Strumming Hippy on 2006-03-21
Should it make any difference if I'm using FF 1.5?

Galen

---

### Post by cjazz on 2006-03-21
If all else fails, you might try installing the MediaPlayerConnectivity extension for Firefox.

---

### Post by damu on 2006-03-21
I have Firefox 1.5 and it works.

Did you try [Automatix]("http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29") ?

Once I had to reinstall the w32codecs_20050412-0.0_i386.deb after an update...don't ask me why, but it sorted my problem.
After download in your home folder, in a terminal window :
> sudo dpkg -i w32codecs_20050412-0.0_i386.deb

---

### Post by the_purulent on 2006-03-21
As I recall last time I set this up I had to remove the totem plugin for mozilla as well, cause each time I connected to media firefox would freak while it tried to load two plugins at once.

---

### Post by SqRt7744 on 2006-03-21
1

---

### Post by Strumming Hippy on 2006-03-21
Thanks everyone for all your help thus far.  Still battling it.

This is the page I'm trying to open ([http://www.apple.com/ipod/ads/](http://www.apple.com/ipod/ads/))  
When I attempt to open the page I get the lovely puzzle piece informing me that I'm missing a plugin, of course I can't download the plugin since apple won't release their magic quicktime to the linux community.

ok, steps taken.  
Removed and Reinstalled mplayer
Replaced the Firefox Plugin
   sudo apt-get install mozilla-mplayer
Replaced the w32 codecs.
Checked the plugins directory of firefox and found that I still had two pesky totem plugins present, and removed them.  

******
hippy@Hippy:/$ cd /usr/lib/mozilla-firefox/plugins
hippy@Hippy:/usr/lib/mozilla-firefox/plugins$ dir
mplayerplug-in-gmp.so   mplayerplug-in-rm.so   mplayerplug-in-wmp.xpt  nppdf.so
mplayerplug-in-gmp.xpt  mplayerplug-in-rm.xpt  mplayerplug-in.xpt
mplayerplug-in-qt.so    mplayerplug-in.so      nphelix.so
mplayerplug-in-qt.xpt   mplayerplug-in-wmp.so  nphelix.xpt
******

So it seems to me that the mplayer plugin is indeed present.

Now to check for the w32codecs

******
hippy@Hippy:/$ cd /usr/local/lib/win32
hippy@Hippy:/usr/local/lib/win32$ dir
acelpdec.ax          jp2avi.dll                   tsd32.dll
alf2cd.acm           l3codeca.acm                 tssoft32.acm
aslcodec_dshow.dll   l3codecx.ax                  tvqdec.dll
aslcodec_vfw.dll     LCMW2.dll                    ubv263d+.ax
asusasv2.dll         LCodcCMP.dll                 ubvmp4d.dll
asusasvd.dll         LCODCCMW2E.dll               ultimo.dll
ativcr2.dll          lhacm.acm                    VDODEC32.dll
atrac3.acm           lsvxdec.dll                  vdowave.drv
atrc.so.6.0          m3jp2k32.dll                 vgpix32d.dll
AvidQTAVUICodec.qtx  m3jpeg32.dll                 vid_3ivX.xa
avimszh.dll          m3jpegdec.ax                 vid_cvid.xa
avizlib.dll          mcdvd_32.dll                 vid_cyuv.xa
BeHereiVideo.qtx     mcmjpg32.dll                 vid_h261.xa
CLRVIDDC.DLL         mi-sc4.acm                   vid_h263.xa
clrviddd.dll         mpg4c32.dll                  vid_iv32.xa
cook.so              mpg4ds32.ax                  vid_iv41.xa
cook.so.6.0          msadp32.acm                  vid_iv50.xa
ctadp32.acm          msg711.acm                   ViVD2.dll
CtWbJpg.DLL          msgsm32.acm                  vivog723.acm
ddnt.so.6.0          msh261.drv                   vmnc.dll
DECVW_32.DLL         msms001.vwp                  voxmsdec.ax
divxa32.acm          msnaudio.acm                 vp31vfw.dll
divx_c32.ax          msrle32.dll                  vp4vfw.dll
divxc32.dll          msscds32.ax                  vp5vfw.dll
divxdec.ax           msvidc32.dll                 vp6vfw.dll
divx.dll             mvoiced.vwp                  vssh264core.dll
dnet.so.6.0          nsrt2432.acm                 vssh264dec.dll
drv2.so.6.0          pclepim1.dll                 vssh264.dll
drv3.so.6.0          qdv.dll                      vsslight.dll
drv4.so.6.0          qpeg32.dll                   vsswlt.dll
drvc.so              qtmlClient.dll               wma9dmod.dll
dspr.so.6.0          QuickTimeEssentials.qtx      wmadmod.dll
huffyuv.dll          QuickTimeInternetExtras.qtx  wmsdmod.dll
i263_32.drv          QuickTime.qts                wmspdmod.dll
iac25_32.ax          README                       wmv8ds32.ax
iccvid.dll           rt32dcmp.dll                 wmv9dmod.dll
icmw_32.dll          scg726.acm                   wmvadvd.dll
imaadp32.acm         sipr.so.6.0                  wmvdmod.dll
imc32.acm            sp5x_32.dll                  wmvds32.ax
ir32_32.dll          tm20dec.ax                   wnvplay1.dll
ir41_32.dll          tokf.so.6.0                  wnvwinx.dll
ir50_32.dll          tokr.so.6.0
ivvideo.dll          tsccvid.dll
hippy@Hippy:/usr/local/lib/win32$
******

There they are, and they're theoretically working since mplayer plays .wmv

So... ideas?

-Galen

---

### Post by Strumming Hippy on 2006-03-21
Ok, 

Automatix did the trick, but because I believe in using an atom bomb when a hammer will suffice I had it redo everything.  It's like a party on my laptop and every file type is invited.  

Thank you EVERYONE!!!!

-Galen

---

### Post by Strumming Hippy on 2006-03-22
Ok, new glitch!

When trying to open this page:
[http://www.fernandesguitars.com/sustainer/susvideodemos/susvideo_1.html](http://www.fernandesguitars.com/sustainer/susvideodemos/susvideo_1.html)

It buffers to 98% and then stops alltogether.  Is this just a file type that isn't actually supported by the codecs?

-Galen

---

### Post by Perfect Storm on 2006-03-22
Works fine here, but I'm using a newer version of mplayerplug-in: [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

If the version you use fail try right click on it and press the start/stop button again.

---

