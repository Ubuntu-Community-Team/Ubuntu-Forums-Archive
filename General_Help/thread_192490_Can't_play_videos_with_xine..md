---
title: "Can't play videos with xine."
date: 2006-06-08
forum: General Help
---

### Post by YourSurrogateGod on 2006-06-08
Every time that I want to play either an *.avi or an *.mkv, I get a warning message saying that the Xvid or Win32 codec is unsupported. And yes I've gone through the whole routine of installing the necessary codecs as is outlined in the dapperguide and whatnots that are related to xine. So what could possibly be the problem?

---

### Post by scxtt on 2006-06-08
all you should need to do is place any/all codec files in whatever directory is specified in xine's config file ... you'll still run into problems if a specific codec doesn't exist in the folder you tell xine your codecs are in ...

check out mplayerhq.hu (yes, i realize it's not an xine site) and look for their "all" codec package ... unpack it and tell xine where it is, should help in some way - unless you're using codecs that are too "new" ...

---

### Post by YourSurrogateGod on 2006-06-08
I just had a look at the config file of xine that's in my home folder, I can't find a path to any other file in my entire system.

---

### Post by scxtt on 2006-06-08
you can use the gui xine provides to edit the config file ... right click on the display window, then choose settings --> setup & set yourself to "master of the known universe" ['configuration experience level' in gui tab] and edit the "path to win32 codec" under the decoder tab ... make sure to hit apply, maybe after experience level, then restart xine before editing decoder tab ...

---

### Post by YourSurrogateGod on 2006-06-08
I just tried that, it didn't work.

---

### Post by scxtt on 2006-06-08
i haven't looked @ the guide you mention, so i don't know what codec set you're using - did you try using the one's from mplayerhq? - i haven't had any .avi problems ... and i just did an slocate .avi and was able to play the one avi that's currently on my box ...

```
madiera [~]
:> sudo slocate -u
Password:
madiera [~]
:> slocate .avi
/usr/share/xine/visuals/default.avi
madiera [~]
:> xine /usr/share/xine/visuals/default.avi
```and it played fine (no errors @ least) ...

---

### Post by YourSurrogateGod on 2006-06-08
[QUOTE=scxtt]i haven't looked @ the guide you mention, so i don't know what codec set you're using - did you try using the one's from mplayerhq? - i haven't had any .avi problems ... and i just did an slocate .avi and was able to play the one avi that's currently on my box ...

```
madiera [~]
:> sudo slocate -u
Password:
madiera [~]
:> slocate .avi
/usr/share/xine/visuals/default.avi
madiera [~]
:> xine /usr/share/xine/visuals/default.avi
```and it played fine (no errors @ least) ...[/QUOTE]
I put the 'all' codecs into /usr/lib/codecs/ directory and set the win32 codecs thingy to point there...

---

### Post by scxtt on 2006-06-09
did it work?, or were you saying that's what you did before you said:> I just tried that, it didn't work.is it possible for you to supply an avi file that isn't working for you, so i can see if it works for me?

---

### Post by YourSurrogateGod on 2006-06-09
[QUOTE=scxtt]did it work?, or were you saying that's what you did before you said:[/quote]
No, it didn't. Sorry for the confusion.
[quote=scxtt]is it possible for you to supply an avi file that isn't working for you, so i can see if it works for me?[/QUOTE]
Well, it's like 174 megs, so...

---

### Post by scxtt on 2006-06-10
just for kicks, do a "file" on the avi in question, like this:```
$hostname [~]
:> file /usr/share/xine/visuals/default.avi
/usr/share/xine/visuals/default.avi: MPEG sequence, v1, progressive Y'CbCr 4:2:0  video@ML interlaced Y'CbCr 4:4:4 video, 25 fps
```i'm kinda curious if there's something special about how it was encoded ...

---

### Post by YourSurrogateGod on 2006-06-10
Sure.
```
file witchblade_01.avi
witchblade_01.avi: RIFF (little-endian) data, AVI, 640 x 480, 23.98 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)
```

---

### Post by YourSurrogateGod on 2006-06-10
Damn, this is so frustrating. I don't know what else I could possibly install in order to make xine play simple avis. Anyone else have a similar problem?

---

### Post by jatilq on 2006-06-11
I have xgl and playing video has been a chore. I would suggest using VLC first then mplayer, gxine/xine, kaffeine and totem.. That seems to work for me. There is also a script floating around that will install mplayer for you from source.

[http://forum.pcmech.com/showthread.php?t=159774](http://forum.pcmech.com/showthread.php?t=159774)

I always try to use VLC first before I go to other players. The advantage of mplayer is you can do the command line and see whats causing problems.

---

### Post by scxtt on 2006-06-12
when i first saw the output of your 'file' i thought "ah, xvid, bet that's it!" (yes, i did forget that you mentioned it above) ... so i scoured the web for an xvid encoded video (found an Enya video from LotR :p) ... but alas, it plays just fine on xine for me and my 'all' codec pack ...

did this video play for you somewhere else? (windows perhaps?)

---

### Post by YourSurrogateGod on 2006-06-12
[QUOTE=scxtt]when i first saw the output of your 'file' i thought "ah, xvid, bet that's it!" (yes, i did forget that you mentioned it above) ... so i scoured the web for an xvid encoded video (found an Enya video from LotR :p) ... but alas, it plays just fine on xine for me and my 'all' codec pack ...[/quote]
Honeslty, I think I screwed up when it came time to putting in that 'all' codec pack. I'm not sure where though...
[quote=scxtt]did this video play for you somewhere else? (windows perhaps?)[/QUOTE]
It plays fine in VLC. I did what jatilq said and it works, the only reason why I wanted it to play in xine is because I'm so used to it.

---

### Post by scxtt on 2006-06-12
[quote=Y.S.G.]Honeslty, I think I screwed up when it came time to putting in that 'all' codec pack. I'm not sure where though...[/quote]hmm, all you should need to do is right click on the archive, select "extract here" and then move all the files to some general area (not necessary, but i moved mine to /usr/lib to a folder called codecs --> /usr/lib/codecs) ... here's what my /usr/lib/codecs folder contains:```
$hostname [~]
:> ll /usr/lib/codecs/
total 31M
-rw-r--r-- 1 scxtt scxtt  870 2005-01-14 18:53 README
-rwxr-xr-x 1 scxtt scxtt  64K 2002-05-22 13:05 atrc.so.6.0
-rwxr-xr-x 1 scxtt scxtt  76K 2002-05-22 13:05 cook.so.6.0
-rwxr-xr-x 1 scxtt scxtt  64K 2002-05-22 13:05 ddnt.so.6.0
-rwxr-xr-x 1 scxtt scxtt  57K 2002-05-22 13:05 dnet.so.6.0
-rwxr-xr-x 1 scxtt scxtt 199K 2002-05-17 09:52 drv2.so.6.0
-rwxr-xr-x 1 scxtt scxtt 297K 2002-05-17 09:52 drv3.so.6.0
-rwxr-xr-x 1 scxtt scxtt 331K 2002-05-17 09:52 drv4.so.6.0
-rwxr-xr-x 1 scxtt scxtt  69K 2002-05-22 13:05 dspr.so.6.0
-rwxr-xr-x 1 scxtt scxtt  62K 2002-05-22 13:05 sipr.so.6.0
-rwxr-xr-x 1 scxtt scxtt  22K 2002-05-22 13:05 tokf.so.6.0
-rwxr-xr-x 1 scxtt scxtt  59K 2002-05-22 13:05 tokr.so.6.0
-rw-r--r-- 1 scxtt scxtt  38K 2002-01-06 18:00 alf2cd.acm
-rw-r--r-- 1 scxtt scxtt  94K 2001-02-14 18:00 atrac3.acm
-rw-r--r-- 1 scxtt scxtt  12K 2003-09-09 00:18 ctadp32.acm
-rw-r--r-- 1 scxtt scxtt 281K 2000-12-29 14:58 divxa32.acm
-rw-r--r-- 1 scxtt scxtt  19K 2001-03-29 19:16 imaadp32.acm
-rw-r--r-- 1 scxtt scxtt  96K 2000-12-17 19:32 imc32.acm
-rw-r--r-- 1 scxtt scxtt 294K 2000-12-21 16:40 l3codeca.acm
-rw-r--r-- 1 scxtt scxtt  33K 2002-04-21 05:09 lhacm.acm
-rw-r--r-- 1 scxtt scxtt  56K 2004-02-14 15:10 mi-sc4.acm
-rw-r--r-- 1 scxtt scxtt  18K 2000-07-30 00:36 msadp32.acm
-rw-r--r-- 1 scxtt scxtt  11K 1999-05-05 17:22 msg711.acm
-rw-r--r-- 1 scxtt scxtt  25K 1999-05-05 17:22 msgsm32.acm
-rw-r--r-- 1 scxtt scxtt  78K 2001-10-11 09:10 msnaudio.acm
-rw-r--r-- 1 scxtt scxtt  49K 2002-04-20 21:30 nsrt2432.acm
-rw-r--r-- 1 scxtt scxtt  13K 2003-12-03 16:29 scg726.acm
-rw-r--r-- 1 scxtt scxtt 9.3K 2002-04-20 20:55 tssoft32.acm
-rw-r--r-- 1 scxtt scxtt 120K 2001-05-03 09:34 vivog723.acm
-rw-r--r-- 1 scxtt scxtt  61K 2001-04-10 15:39 acelpdec.ax
-rw-r--r-- 1 scxtt scxtt 234K 2000-12-21 16:34 divx_c32.ax
-rw-r--r-- 1 scxtt scxtt 424K 2001-08-28 16:36 divxdec.ax
-rw-r--r-- 1 scxtt scxtt 195K 2004-06-02 12:37 iac25_32.ax
-rw-r--r-- 1 scxtt scxtt  82K 2001-01-02 19:44 l3codecx.ax
-rw-r--r-- 1 scxtt scxtt  53K 2001-05-09 21:51 m3jpegdec.ax
-rw-r--r-- 1 scxtt scxtt 257K 2001-05-10 18:04 mpg4ds32.ax
-rw-r--r-- 1 scxtt scxtt  75K 2001-12-07 08:27 msscds32.ax
-rw-r--r-- 1 scxtt scxtt 172K 2002-04-23 09:51 tm20dec.ax
-rw-r--r-- 1 scxtt scxtt 236K 2001-07-03 10:01 ubv263d+.ax
-rw-r--r-- 1 scxtt scxtt  55K 1999-04-15 10:10 voxmsdec.ax
-rw-r--r-- 1 scxtt scxtt 273K 2001-05-01 03:46 wmv8ds32.ax
-rw-r--r-- 1 scxtt scxtt 257K 2001-04-01 23:30 wmvds32.ax
-rw-r--r-- 1 scxtt scxtt 116K 2004-03-24 01:21 aslcodec_dshow.dll
-rw-r--r-- 1 scxtt scxtt  76K 2004-03-24 01:21 aslcodec_vfw.dll
-rw-r--r-- 1 scxtt scxtt  86K 2001-01-21 19:49 asusasv2.dll
-rw-r--r-- 1 scxtt scxtt  35K 1999-09-09 13:12 asusasvd.dll
-rw-r--r-- 1 scxtt scxtt 147K 2000-08-02 01:28 ativcr2.dll
-rw-r--r-- 1 scxtt scxtt  68K 2001-05-03 09:30 avimszh.dll
-rw-r--r-- 1 scxtt scxtt 112K 2001-05-03 09:30 avizlib.dll
-rw-r--r-- 1 scxtt scxtt 132K 2002-04-20 19:52 clrviddd.dll
-rw-r--r-- 1 scxtt scxtt 403K 2001-01-24 04:28 divxc32.dll
-rw-r--r-- 1 scxtt scxtt 508K 2001-08-28 16:26 divx.dll
-rw-r--r-- 1 scxtt scxtt  33K 2000-08-23 20:00 huffyuv.dll
-rw-r--r-- 1 scxtt scxtt 108K 2000-03-09 14:15 iccvid.dll
-rw-r--r-- 1 scxtt scxtt 300K 2001-05-03 09:29 icmw_32.dll
-rw-r--r-- 1 scxtt scxtt 195K 2000-07-13 23:52 ir32_32.dll
-rw-r--r-- 1 scxtt scxtt 722K 1997-07-07 05:32 ir41_32.dll
-rw-r--r-- 1 scxtt scxtt 738K 2000-03-09 14:17 ir50_32.dll
-rw-r--r-- 1 scxtt scxtt 220K 2001-11-03 18:40 ivvideo.dll
-rw-r--r-- 1 scxtt scxtt  88K 2002-11-30 17:55 jp2avi.dll
-rw-r--r-- 1 scxtt scxtt 240K 2004-03-22 18:57 LCMW2.dll
-rw-r--r-- 1 scxtt scxtt 331K 2002-04-21 14:13 LCodcCMP.dll
-rw-r--r-- 1 scxtt scxtt  80K 2004-03-22 18:57 LCODCCMW2E.dll
-rw-r--r-- 1 scxtt scxtt 200K 2004-11-14 16:02 lsvxdec.dll
-rw-r--r-- 1 scxtt scxtt 413K 2002-11-12 03:53 m3jp2k32.dll
-rw-r--r-- 1 scxtt scxtt 259K 2001-09-03 07:08 m3jpeg32.dll
-rw-r--r-- 1 scxtt scxtt 258K 2001-10-11 06:34 mcdvd_32.dll
-rw-r--r-- 1 scxtt scxtt  96K 2001-04-01 23:57 mcmjpg32.dll
-rw-r--r-- 1 scxtt scxtt 249K 1999-06-26 09:31 mpg4c32.dll
-rw-r--r-- 1 scxtt scxtt  28K 1999-05-05 16:22 msrle32.dll
-rw-r--r-- 1 scxtt scxtt  30K 2001-03-23 13:30 msvidc32.dll
-rw-r--r-- 1 scxtt scxtt  44K 2001-11-16 14:10 pclepim1.dll
-rw-r--r-- 1 scxtt scxtt 221K 2001-01-29 03:08 qdv.dll
-rw-r--r-- 1 scxtt scxtt  34K 1996-12-15 18:00 qpeg32.dll
-rw-r--r-- 1 scxtt scxtt 220K 2002-11-08 14:04 qtmlClient.dll
-rw-r--r-- 1 scxtt scxtt 292K 2002-04-20 21:32 rt32dcmp.dll
-rw-r--r-- 1 scxtt scxtt 128K 2002-09-09 14:01 sp5x_32.dll
-rw-r--r-- 1 scxtt scxtt 108K 2002-04-21 08:38 tsccvid.dll
-rw-r--r-- 1 scxtt scxtt  16K 2002-04-05 17:00 tsd32.dll
-rw-r--r-- 1 scxtt scxtt 560K 2004-12-19 11:51 tvqdec.dll
-rw-r--r-- 1 scxtt scxtt 116K 2002-04-21 11:35 ubvmp4d.dll
-rw-r--r-- 1 scxtt scxtt  28K 2003-10-29 10:40 ultimo.dll
-rw-r--r-- 1 scxtt scxtt  75K 1996-11-12 04:12 VDODEC32.dll
-rw-r--r-- 1 scxtt scxtt  75K 2002-03-12 08:22 vgpix32d.dll
-rw-r--r-- 1 scxtt scxtt 207K 2003-03-28 10:03 ViVD2.dll
-rw-r--r-- 1 scxtt scxtt 152K 2005-04-10 12:06 vmnc.dll
-rw-r--r-- 1 scxtt scxtt 452K 2001-09-22 09:17 vp31vfw.dll
-rw-r--r-- 1 scxtt scxtt 456K 2004-04-27 18:39 vp4vfw.dll
-rw-r--r-- 1 scxtt scxtt 364K 2004-04-27 18:40 vp5vfw.dll
-rw-r--r-- 1 scxtt scxtt 428K 2004-02-12 03:39 vp6vfw.dll
-rw-r--r-- 1 scxtt scxtt  48K 2003-04-09 18:49 vssh264core.dll
-rw-r--r-- 1 scxtt scxtt 412K 2003-04-09 18:49 vssh264dec.dll
-rw-r--r-- 1 scxtt scxtt  96K 2003-04-09 18:49 vssh264.dll
-rw-r--r-- 1 scxtt scxtt 444K 2005-05-03 10:23 vsshdsd.dll
-rw-r--r-- 1 scxtt scxtt 691K 2003-04-09 18:48 vsslight.dll
-rw-r--r-- 1 scxtt scxtt 164K 2003-04-09 18:48 vsswlt.dll
-rw-r--r-- 1 scxtt scxtt 401K 2002-10-29 11:03 wma9dmod.dll
-rw-r--r-- 1 scxtt scxtt 401K 2002-10-28 09:11 wmadmod.dll
-rw-r--r-- 1 scxtt scxtt 756K 2004-08-10 19:44 wmsdmod.dll
-rw-r--r-- 1 scxtt scxtt 476K 2004-04-27 18:43 wmspdmod.dll
-rw-r--r-- 1 scxtt scxtt 789K 2002-11-20 16:03 wmv9dmod.dll
-rw-r--r-- 1 scxtt scxtt 1.2M 2004-10-18 03:33 wmvadvd.dll
-rw-r--r-- 1 scxtt scxtt 789K 2002-10-28 09:12 wmvdmod.dll
-rw-r--r-- 1 scxtt scxtt 124K 2004-07-02 18:36 wnvplay1.dll
-rw-r--r-- 1 scxtt scxtt  91K 2004-07-02 18:36 wnvwinx.dll
-rw-r--r-- 1 scxtt scxtt  80K 2006-04-24 20:17 zmbv.dll
-rw-r--r-- 1 scxtt scxtt 306K 2002-04-20 19:58 CLRVIDDC.DLL
-rw-r--r-- 1 scxtt scxtt  80K 2002-04-21 05:22 CtWbJpg.DLL
-rw-r--r-- 1 scxtt scxtt  87K 1996-08-14 06:41 DECVW_32.DLL
-rw-r--r-- 1 scxtt scxtt 383K 2000-08-01 16:41 i263_32.drv
-rw-r--r-- 1 scxtt scxtt 164K 2001-06-26 11:53 msh261.drv
-rw-r--r-- 1 scxtt scxtt  81K 2003-08-18 12:52 vdowave.drv
-rw-r--r-- 1 scxtt scxtt 4.4M 2003-05-27 06:42 QuickTime.qts
-rw-r--r-- 1 scxtt scxtt  90K 2004-07-04 12:19 AvidQTAVUICodec.qtx
-rw-r--r-- 1 scxtt scxtt  75K 2001-04-18 05:54 BeHereiVideo.qtx
-rw-r--r-- 1 scxtt scxtt 550K 2003-05-27 06:42 QuickTimeEssentials.qtx
-rw-r--r-- 1 scxtt scxtt 884K 2003-05-27 06:42 QuickTimeInternetExtras.qtx
-rwxr-xr-x 1 scxtt scxtt  42K 2005-02-15 14:39 cook.so
-rwxr-xr-x 1 scxtt scxtt 314K 2005-02-15 14:40 drvc.so
-rw-r--r-- 1 scxtt scxtt 415K 1999-04-15 14:10 msms001.vwp
-rw-r--r-- 1 scxtt scxtt 214K 1999-04-15 14:10 mvoiced.vwp
-rwxr-xr-x 1 scxtt scxtt 312K 2004-07-24 09:41 vid_3ivX.xa
-rwxr-xr-x 1 scxtt scxtt 6.5K 2004-07-24 09:41 vid_cvid.xa
-rwxr-xr-x 1 scxtt scxtt 3.2K 2004-07-24 09:41 vid_cyuv.xa
-rwxr-xr-x 1 scxtt scxtt  70K 2004-07-24 09:41 vid_h261.xa
-rwxr-xr-x 1 scxtt scxtt 122K 2004-07-24 09:41 vid_h263.xa
-rwxr-xr-x 1 scxtt scxtt 106K 2004-07-24 09:41 vid_iv32.xa
-rwxr-xr-x 1 scxtt scxtt 185K 2004-07-24 09:41 vid_iv41.xa
-rwxr-xr-x 1 scxtt scxtt  86K 2004-07-24 09:41 vid_iv50.xa
```and of course you'll need to point xine's config in that direction, as i mentioned above ...

---

### Post by scxtt on 2006-06-12
well, i've come to the conclusion that there is some sort of problem w/ Dapper and xine ...

all the "do this/that cause it works for me" info i was giving you was based off of Breezy - and when i tried it in Dapper it didn't work (just as it hasn't been for you) ... so it's beyond me why it seems to be ignoring where we are storing codecs ...

seems like a bug to me ...

---

### Post by scxtt on 2006-06-15
i've got xine 0.99.3 working in dapper - and the codecs work just fine ... so i think there's either a problem w/ the engine or libraries 0.99.4 use or that version and dapper just don't get along ...

all i did was replace my dapper sources.list w/ breezy's sources.list and install it that way (it even removed 0.99.4's engine/library) - worked w/o a hitch!

:D

---

### Post by YourSurrogateGod on 2006-06-23
[QUOTE=scxtt]i've got xine 0.99.3 working in dapper - and the codecs work just fine ... so i think there's either a problem w/ the engine or libraries 0.99.4 use or that version and dapper just don't get along ...

all i did was replace my dapper sources.list w/ breezy's sources.list and install it that way (it even removed 0.99.4's engine/library) - worked w/o a hitch!

:D[/QUOTE]
That's cool. I'm doing fine with VLC, so I can't really complain (the controls are similar to what I'm used to in xine, so...) Thanks for your help.

---

### Post by YourSurrogateGod on 2006-07-05
[QUOTE=scxtt]i've got xine 0.99.3 working in dapper - and the codecs work just fine ... so i think there's either a problem w/ the engine or libraries 0.99.4 use or that version and dapper just don't get along ...

all i did was replace my dapper sources.list w/ breezy's sources.list and install it that way (it even removed 0.99.4's engine/library) - worked w/o a hitch!

:D[/QUOTE]
Could you please get me the link for that specific tarball? I installed what I thought was it, but it turns out that it's not. You can PM me if you wish.

---

### Post by YourSurrogateGod on 2006-07-20
Ok. I can't find the all-codec that you're describing. Yes, I've looked at the site that you mentioned. The only thing that I found there was an 'essential' codec, which doesn't do what I want. Could you please post a link to the all codec so that I could simply download it? Does anyone else know where that thing is? Or any other solution to my problem? Anyone?

---

### Post by YourSurrogateGod on 2006-07-20
> **scxtt said:**
> all i did was replace my dapper sources.list w/ breezy's sources.list and install it that way (it even removed 0.99.4's engine/library) - worked w/o a hitch!
How did you do that?

[edit]

Never mind, problem resolved... all of them.

---

