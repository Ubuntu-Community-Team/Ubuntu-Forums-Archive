---
title: "The Acer Revo R3610 thread"
date: 2010-01-12
forum: General Help
---

### Post by Kevbert on 2010-01-12
Documentation for this nettop PC is very basic and that is the reason for this thread. 

**_Specification:_**
Model: 92.NVFYZ.U2N
CPU:   Intel Atom 330 1.6GHz
RAM:   4Gb** DDR2
HDD:   500Gb
Video: nVidia ION integrated
WLAN:  Atheros AR5007EG 802.11a/b/g
Interfaces: 6xUSB 2.0, eSATA, SPDIF*, Headphone, Microphone, LAN, HDMI, Monitor, Multiformat flashcard reader
OS:    Windows7 Home Premium
* Not available on some US versions
  802.11n available on some US models
** Even though 4Gb is installed only 3 Gb is available for the operating system. The remaining memory is allocated to graphics as there is no separately dedicated graphics card. Confirmed with Acer Software Engineer. 

**_What it comes with:_**
Small form factor Windows wireless keyboard
Two button scrolling wireless mouse
Wireless USB adapter (stored in mouse battery compartment)
Power supply and lead
TV Monitor mounting adapter
Stand
Very basic instructions

**_What it doesn't come with:_**
Display adapter cables
Stereo Speakers (single internal PC speaker only)* 
External drives
*Some US versions come with mini stereo speakers

**_Reviews_**
[Computershopper]("http://computershopper.com/desktops/reviews/acer-aspire-revo-r3610-u9012") [Gnome Commentary]("http://davidnielsen.wordpress.com/2009/11/14/i-love-my-acer-aspire-revo-r3610/") [TestSeek]("http://www.testseek.com/computers/desktops/acer_aspire_r3610_revo-p-8c147ca1-40e8-ff6b-20e3-a365a2e924b9.html")

---

### Post by Kevbert on 2010-01-12
**_Default Setup:_**
1) Fit wireless adapter in one of the USB ports.
2) Fit batteries in mouse and turn underside switch to on.
3) Connect Revo to power and display and turn on.
4) Fit keyboard batteries and then press underside 'Connect' for a minimum of 1 second*.
5) Run Windows 7 setup. 

* If the keyboard does not respond when required then remove batteries for ten seconds and then repeat 4).

500Gb Hard drive partitioned as four primary drives by default (225Gb for system, 225Gb for data, 100Mb boot, 15Gb protected restore).

---

### Post by Kevbert on 2010-01-12
**_Dual Booting Win7 with Ubuntu_**

_Pre-requisits_
PC with Ubuntu 9.04 or later
1Gb or larger USB drive

Prior to installing Ubuntu, [COLOR="Red"][backup all files]("http://windows.microsoft.com/en-us/windows7/Back-up-your-programs-system-settings-and-files")[/COLOR] as the Revo doesn't come with a system restore CD (in case of problems). By default this backup is 21Gb!!! 
With the Ubuntu PC, download the iso of your choice (I've used [COLOR="Red"][9.04 64 bit]("http://releases.ubuntu.com/9.04/")[/COLOR] as it's stable IMHO)
Plug-in the USB drive into the Ubuntu PC by going to System-Administration-USB Startup Disk Creator.  The persistent drive size where documents and extra settings are stored is not important. Once the USB drive has been set-up right-click on the desktop icon and select 'Unmount Volume' prior to removing it.
Fit the Ubuntu USB drive in any one of the Revo USB sockets. Turn on and as soon as the Revo starts press F12 (in order to select the boot sequence). Select the USB drive. Now when the Ubuntu menu is displayed select 'Try Ubuntu...'
Next select System-Administration-Partition Editor to run GParted. It is necessary to remove one primary partition as the maximum allowed is four. Highlight the DATA partition with the mouse and select Partition-Delete, then click on Apply. Now select the 'unallocated' space and create a new extended partition by selecting New and then Extended Partition in the 'Create as:' drop-down box, click on Add and then Apply. Within this empty space you can create a new Logical Partition formatted FAT32 and called Data, size could be 50Gb (for Windows if required). Do not format the remaining space (we'll do that later).
Close The partition Editor and then reboot Ubuntu pressing F12 as the PC boots up (just to make sure that the Revo boots from the hard disk).  This step is necessary as Windows may complain and run Chkdsk as the drive partitions have changed.
Once the Windows log-in window appears,reboot the Revo and press F12 to select the USB drive to boot first.
Install Ubuntu. When setting up the partitions use 'Manual' and select 4Gb as the Swap space and use the rest for Ubuntu (mounted / format to ext3) in the unused/unallocated space.
Once the install is complete, reboot and check that Ubuntu runs.

_Links_
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) - Another method of installing via USB.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) - Installing via CD.

---

### Post by Kevbert on 2010-01-12
**_Grub Legacy Menu_**
In Ubuntu 9.04 you'll need to edit /boot/grub/menu.lst as two instances of the Windows Bootloader appear. Select Applications-Accessories-Terminal and enter
```
sudo gedit /boot/grub/menu.lst
```
Find the lines that say
```
title Windows Vista (loader)
rootnoverify	**(hd0,0)**
savedefault
chainloader	+1 
```
and change the title line to 
```
title Windows7 eRecovery
```
Now find 
```
title Windows Vista (loader) 
rootnoverify	**(hd0,1)**
savedefault
chainloader	+1
```
and change the title line to 
```
title Windows7 (loader) 
```
(this one is the one to run Windows 7 from).
Save and exit menu.lst.

---

### Post by Kevbert on 2010-01-12
**_Poor HD Graphics_**
While running Miro using various high definition videos files, the videos stuttered and did not run smoothly. When running XBMC the program ran very slowly. To get round this problem a new video driver was installed.
Normally a restricted driver is installed, but in this case the default driver seemed fine for general desktop use. Going to System-Administration-Hardware Drivers nothing was displayed.
To install the recommended driver for the nVidia ION go to System-Administration-Synaptic and install the nvidia-glx-180 driver. Next log out of Ubuntu and then back in and then Miro will run smoothly and XBMC will be responsive.

---

### Post by Kevbert on 2010-01-12
**_Wireless No Longer Works_**
The WLAN is based on the Atheros AR5700 and uses the AR242X driver by default. Occasionally wireless is temporarily unavailable according to Network Manager.
One way to get around this problem is to power down the Revo, remove the wireless USB adapter and then restart the PC. As soon as Ubuntu starts to load, refit the USB adapter and wireless will start to work again.

---

### Post by stillnotcool on 2010-01-13
Thanks for all this, Kevbert.  It's all extremely valuable.

Reading more about the Revo, I've noticed that Acer ships a model with 1GB of RAM, a 8GB SSD, and Linux preinstalled ([link]("http://www.trustedreviews.com/pcs/news/2009/04/27/Acer-Confirms-Aspire-Revo-Price---Release-Date/p1")).  However, I can't find this model for sale in the United States.  Does anyone know if it's available in the US?

---

### Post by Kevbert on 2010-01-14
Normally I try [http://www.streetprices.com](http://www.streetprices.com) but even they don't seem to have it.  Nor do Newegg. ???

---

### Post by stillnotcool on 2010-01-14
Perhaps it was already discontinued.  I'll keep searching.  Thanks, Kevbert.

---

### Post by Kevbert on 2010-01-14
The problem with the Revo is that it's very popular and sells out quickly. I had trouble getting mine as everyone I tried was out of stock on the 4Gb version even Amazon.  The typical spec Revo R3610 I could find in the US was a 2Gb version with 160Gb hard drive. Other Revo models were based on the 230 and 260 Intel based processors (I assume that these are a slower than the 330).
Also the nVidia display adapter is starting to appear with the ION LE graphics processor (not sure of the difference between this and the standard ION).

---

### Post by Kevbert on 2010-01-14
_**Additional Useful Links**_
These links may be of interest:
[[COLOR="Red"]Intel Atom[/COLOR]]("http://en.wikipedia.org/wiki/Intel_Atom") - Wikipedia page for Atom processors
[COLOR="Red"][Nvidia ION]("http://en.wikipedia.org/wiki/Nvidia_ION")[/COLOR] - Wikipedia page for Motherboard/Graphics
[[COLOR="Red"]Installing XBMC on the Revo[/COLOR]]("http://xbmc.org/forum/showthread.php?t=53888") - XBMC forum page
[[COLOR="Red"]Minimal Ubuntu install[/COLOR]]("http://xbmc.org/forum/showthread.php?t=53812") - XBMC forum page
[[COLOR="Red"]Installing 9.10 and boxee tv on the revo[/COLOR]]("http://www.greenhughes.com/content/how-install-ubuntu-910-and-boxee-beta-acer-aspire-revo-including-64-bit-option")
[[COLOR="Red"]How to open the Revo case[/COLOR]]("http://www.youtube.com/watch?v=7ayQOyTEWRw"). This may invalidate any warranty.
[[COLOR="Red"]Adding extra memory[/COLOR]]("http://www.bit-tech.net/news/hardware/2009/04/27/inside-the-acer-revo/1")
[[COLOR="Red"]Avforums Revo experience thread[/COLOR]]("http://www.avforums.com/forums/home-entertainment-pcs/1115503-any-experiances-new-acer-revo.html")
[[COLOR="Red"]Full Circle magazine Boxee article[/COLOR]]("http://fullcirclemagazine.org/2010/01/30/issue-33-is-out-creating-a-media-center-education-and-sync/") - Boxee on Ubuntu 9.10 Revo PC
[[COLOR="Red"]HTPC Guild for HDMI[/COLOR]]("http://blog.mybarachois.com/b1/play/xbmc/htpc-nvidia-ion-1080pxbmcubuntu-guide/") - This uses the same HDMI settings as the Revo
[[COLOR="Red"]A good place for links[/COLOR]]("http://www.mywikibiz.com/Acer_Aspire_Revo_3610")
[[COLOR="Red"]Revo User Forum[/COLOR]]("http://www.revouser.com/forum/viewforum.php?f=2")
I intend to add new links as I find them...

---

### Post by rasheedl on 2010-03-07
I wonder if anyone can help me - I've really hit a dead-end and have been searching all over the place without luck.

I have a Revo 3610 with Ubuntu 9.10, Nvidia latest drivers - 195.36.03 activated, Flash 10.1.51.95 & I can't for the life of me get iplayer or any other flash video in firefox to run smoothly in fullscreen, it's extremely choppy, but super-smooth at it's normal size.

If I play DVD rips or even 1080p videos in Smplayer, XBMC or Boxee at fullscreen, they run fine.

Any ideas, I really don't want to resort to Win 7 (urgh - the thought of it!).

Thanks

---

### Post by Kevbert on 2010-03-08
Have you tried boxee ? It seems to run BBC iPlayer videos fine for me (you may need to add the app. My only problem is broadband bandwidth is no so hot here (just outside London!)

---

### Post by moongia on 2010-03-12
Just a quick question,my friend has one it came with xp and he added a bit more ram to it.So now he wants to give ubuntu 9.10 a go.I just wanted to know if compiz and the cube works well if at all on it.Thanks.

---

### Post by Kevbert on 2010-03-12
9.10 64 bit works fine on my R3610. Compiz works fine.

---

### Post by moongia on 2010-03-12
Thank you,I'm installing it this weekend for him,his new to ubuntu but he has used mine many times, and loves it.Thanks again.

---

### Post by zach.detton on 2010-03-14
What video output are you using. I have been thinking of getting the Asus EEE PC Net-Top with the same ION Chipset ([This one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883220021")) and wanted to know if the HDMI output would work in Ubuntu. If the HDMI output is working, what is the max resolution you've been able to run X.org at?

---

### Post by Kevbert on 2010-03-14
I'm not currently using HDMI and am not aware of any video problems. I've added a separate link for setting up HDMI sound (see above). I'm currently using the Revo PC video output to an old Mitac monitor.

---

### Post by colferma on 2010-04-05
Hi Kevbert,

Firstly, many thanks for all the above information. I've been searching around for ubuntu/revo 3610 threads and it's by far the best I've seen. I'm on 3610, dualbooting 9.10 and windows 7 and I have a few questions that maybe you could help me with?

a) My wireless on ubuntu is way slower than windows, despite my disabling ipv6 on firefox and throughout the system in general. Have you ever come across that?

b) Ubuntu only allows me to connect to the wireless when there's no password involved. Once there is a password, I just keep getting prompted for it over and over again (even though I enter the correct one).

Any help is appreciated,

Martin

---

### Post by Kevbert on 2010-04-06
Assuming that your using the Atheros WLAN that came with the Revo it's probably a driver problem (the Atheros is known to be a bit temperamental). Mine is poor on both Win7 and 9.10 (I may eventually change it). [[COLOR="Red"]This[/COLOR]]("http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu") may be of use as it details how to install the madwifi driver.
Failing that, with a connection made, what is the Applications-Accessories-Terminal output of
```
iwconfig
iwlist scanning
```
It may be due to interference or other wifi networks using the same channel.

---

### Post by rplay on 2010-04-14
> **Kevbert said:**
> **_Poor HD Graphics_**
While running Miro using various high definition videos files, the videos stuttered and did not run smoothly. When running XBMC the program ran very slowly. To get round this problem a new video driver was installed.
Normally a restricted driver is installed, but in this case the default driver seemed fine for general desktop use. Going to System-Administration-Hardware Drivers nothing was displayed.
To install the recommended driver for the nVidia ION go to System-Administration-Synaptic and install the nvidia-glx-180 driver. Next log out of Ubuntu and then back in and then Miro will run smoothly and XBMC will be responsive.

Hi Kevbert,

I use linux since 2-3 years, last week I buy revo R3610 (2GB, 160 GB ) and now I've got a problem .... I try to play an *.mkv video with vlc ..... video codec: avc1, 1280x720 pixels .... audio codec a52
but it didn't run .... there is the same effect like by you, but I've got the new NVIDIA driver (the actual restricted driver for ubuntu lucid 10.04) I've got the nvidia-glx-180 driver to .. but it will not be better
do You know the solution?
avi videos run smoothly and without errors on display .....

thx
rplay

---

### Post by Kevbert on 2010-04-15
You may have problems playing these files in Linux. Please take a look at [http://ubuntuforums.org/showthread.php?t=679320&page=2](http://ubuntuforums.org/showthread.php?t=679320&page=2) especially the last post. It may also be worth running
```
top
```
in terminal while trying to run the .mkv file to see if the CPU is the problem. What's the resolution/bitrate of the file you're trying to play ?
Is it 720p/1080p or i ? Can you post a link to the file ?

---

### Post by rplay on 2010-04-20
> **Kevbert said:**
> Please take a look at [http://ubuntuforums.org/showthread.php?t=679320&page=2](http://ubuntuforums.org/showthread.php?t=679320&page=2) especially the last post. What's the resolution/bitrate of the file you're trying to play ?
Is it 720p/1080p or i ? Can you post a link to the file ?

Hi Kevbert,

I think, it's a 720p File ....... but I'm not sure ..... here the mkvinfo .... I've got a german ubuntu and so, the mkvinfo is in german to ;-(


+ EBML-Kopf                                                                                                          
|+ Dokumententyp:matroska
|+ Dokumententyp Version: 1
|+ Dokumententyp Leseversion: 1
+ Segment, Größe 2346129595
|+ Seek-Kopf (Untereinträge werden ausgelassen)
|+ EbmlVoid (Größe: 4027)
|+ Segment-Information
| + Zeitstempelskalierungsfaktor: 1000000
| + Muxeranwendung: libebml v0.7.7 + libmatroska v0.8.1
| + Schreibende Anwendung: mkvmerge v2.0.2 ('You're My Flame') built on Jul 16 2008 20:03:58
| + Dauer: 4880.000s (01:21:20.000)
| + Datum: Wed Feb  3 05:49:55 2010 UTC
| + Segment-UID: 0x7b 0x25 0x07 0x88 0x7e 0xb1 0xfc 0x38 0x18 0x29 0x06 0xcb 0x81 0xda 0x9b 0x6b                     
|+ Segment-Tracks                                                                                                    
| + Ein Track                                                                                                        
|  + Tracknummer: 1
|  + Track UID: 1                                                                                                    
|  + Tracktyp: video                                                                                                 
|  + Aktiv: 1                                                                                                        
|  + Standardtrack-Flag:1                                                                                           
|  + Flag für erzwungene Anzeige: 0
|  + Flag für Paketbündelung: 0
|  + MinCache: 1
|  + Zeitstempelskalierungsfaktor: 1
|  + Maximale BlockAddition ID: 0
|  + **Codec-ID: V_MPEG4/ISO/AVC**
|  + Codec alle frames decodieren: 1
|  + private Codecdaten, Länge 40
|  + Standarddauer: 41.708ms (23.976 Bilder pro Sekunde im Falle eines Videotracks)
|  + Sprache: eng
|  + Video-Track
|   + **Pixelwidth: 1280**
|   + **Pixelhigh: 720**
|   + **Interlaced: 0**
|   + Anzeigebreite: 16
|   + Anzeigehöhe: 9
| + Ein Track
|  + Tracknummer: 2
|  + Track UID: 4160788995
|  + Tracktyp: audio
|  + Aktiv: 1
|  + Standardtrack-Flag: 1
|  + Flag für erzwungene Anzeige: 0
|  + Flag für Paketbündelung: 1
|  + MinCache: 0
|  + Zeitstempelskalierungsfaktor: 1
|  + Maximale BlockAddition ID: 0
|  + Codec-ID: A_AC3
|  + Codec alle frames decodieren: 1
|  + Standarddauer: 32.000ms (31.250 Bilder pro Sekunde im Falle eines Videotracks)
|  + Sprache: und
|  + Audio track
|   + Abtastrate: 48000
|   + Kanäle: 6
|+ EbmlVoid (Größe: 1024)
|+ Cluster

a link to the file is not so easy .... it's on a News Server .... if You've got an account, search for "lost s06e01".

I read the link You send me .... it sounds not good ....:

"You're going to have trouble playing that because there's no GPU rendering in linux for mkv, so it's gonna be CPU only."

is there solution in the near future or now? the post was from July 24th, 2008.... it is 2 years back ....

thx, rplay

---

### Post by Kevbert on 2010-04-20
I can play some .mkv 720p files smoothly via Miro, the problem I have is that I can't stream video straight from the net, but have to download them first due to poor wireless (this also occurs with Win7 on Revo). The Atheros Wifi adapter is known give low signal strength compared to Broadcom, Intel even when both are close to each other. I'm trying to replace the default wifi adapter with a different one but am currently hitting a brick wall as the keyboard and mouse seem to use the same wifi adapter.

---

### Post by rplay on 2010-04-20
> **Kevbert said:**
> I can play some .mkv 720p files smoothly via Miro, the problem I have is that I can't stream video straight from the net, ....

hi,

I think WLAN should not be the problem, I use "normal" wire-LAN and it doesn't work ...
even if I copy the file to the revo, revo can't play it from the "local" hard disk ....

what do you mean with "miro", is this what you mean?:
 p, li { white-space: pre-wrap; }     [RIGHT]Details:[/RIGHT]
  Miro (previously known as Democracy Player) is a platform for Internet television and video. It allows you to download and watch videos from RSS feeds (including podcasts, video blogs, and BitTorrent feeds).
  p, li { white-space: pre-wrap; }  [[COLOR=#0057AE]_http://www.getmiro.com_[/COLOR]]("http://www.getmiro.com/")

---

### Post by Kevbert on 2010-04-21
That's the program. It's also possible that your problem is possibly due to either codecs or the video driver. The problem seems to be some codecs/programs/drivers work and others don't (sorry for being a little vague - this is my experience on 4 different PCs). 
I've not tried 10.04 on the Revo, but 9.10 and 9.04 seem to work for me.

---

### Post by rjs1064 on 2010-04-22
is get iplayer pvr still working

---

### Post by Kevbert on 2010-04-22
> **rjs1064 said:**
> is get iplayer pvr still working

Do you mean the BBC iPlayer ? If so, it is working fine.

---

### Post by hoanghien on 2010-05-01
My revo wireless card is ralink rt3090. will this card work in 10.04? Anyone has the same version?

---

### Post by MatrixCat on 2010-05-03
Just adding my two cents' worth.  Neither included drivers nor madwifi ([even hal-0.10.5.6 though it might work for you]("http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu")) worked so I went [the ndiswrapper route]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  As per video, with nVidia's latest driver (195 as of writing this) stutter is almost non-existent for VDPAU supported playback even at 1080p.  Unfortunately VLC (my fave) isn't so good at support so try mplayer.  I use [Big Buck Bunny]("http://www.bigbuckbunny.org/index.php/download/") for testing and then run:
```
mplayer -vo vdpau -vc ffh264vdpau big_buck_bunny_1080p_h264.mov
```
from the command line.  However, smooth full-screen Flash playback still eludes me to this day.  Hope this helps.

---

### Post by Kevbert on 2010-05-04
Nice video MatrixCat, I downloaded it prior to running as my Broadband is so slowwww. 
In 9.04, Mplayer seems to stutter a bit (especially when zooming in on the rabbit hole at the beginning) on my Athlon 64X2, with Nvidia 7600 and the 180.44 driver. VLC and XBMC are a little better but still stutter slightly. Miro is much smoother. Will try on Revo later with 9.10 (yet to try 10.04).

---

### Post by Kevbert on 2010-05-04
> **hoanghien said:**
> My revo wireless card is ralink rt3090. will this card work in 10.04? Anyone has the same version?

Please take a look at [[COLOR="Red"]this[/COLOR]]("http://forum.xbmc.org/showthread.php?t=71332").

---

### Post by arst06d on 2010-05-14
Can anyone recommend an external cd/dvd rewriter that will work with this machine and ubuntu 10.04?  Preferably available in UK.

I've taken the dvd drive out of my old pc and housed it in a caddy, connected up to power and USB and it doesn't recognise it.  I can see it in Computer but it disappears when I put a disk in.

Tried different usb cables, and I know the drive was working with my old pc under XP.

Rather than fiddling about with different caddies I might as well get a "proper" external optical drive.

So - recommendations please.  Need CD +/- DVD +/- DL R/RW (in fact all combinations of every format).

Thanks.

---

### Post by wenzi on 2010-05-14
> **hoanghien said:**
> My revo wireless card is ralink rt3090. will this card work in 10.04? Anyone has the same version?

I just bought a Revo 3610 last week and it had a RALink rt3090 also. I downloaded  2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2 from the ralink site, unpacked  and did the usual

```
make
sudo make install
```Rebooted and everything worked fine. No problems whatsoever.

---

### Post by rasheedl on 2010-05-15
[B]@arst06d
[/B]
I recently bought this one from Argos:

[LiteOn 8x Slim External DVDRW Drive]("http://www.argos.co.uk/webapp/wcs/stores/servlet/ProductDisplay?storeId=10001&catalogId=1500002201&langId=-1&productId=1500629051")

It works fine, doesn't need external power & is good value. The cable is a little short - u might want to get an extension.

BTW, how's fullscreen flash with you?

---

### Post by arst06d on 2010-05-15
**@rasheedl**

Haven't had the need for full screen flash as yet - not using it as a media centre as such, just a general pc.

Scratch the above.  Just tried BBC iPlayer in full screen mode and it works just fine.

Thanks for the pointer to the optical drive.  Any others appreciated, especially non-bus powered ones.

---

### Post by JMcFly on 2010-05-17
My R3610's wireless g experience (Ralink, 9.10) has been abysmal, regardless of what I try (router settings, Revo orientation, etc) I can't connect to the router 15' away when my Eee can see it with full strength from the same spot (not sure if its a network manager problem or a driver problem, about half the time I do not get a wireless connection option the rest of the time it acts like it is trying to connect and asks for the password endlessly). I have a 3945ABG from an old laptop so I'm going to see if that will work until I can snake a Cat5 cable to the Revo.

---

### Post by Kevbert on 2010-05-19
> **JMcFly said:**
> My R3610's wireless g experience (Ralink, 9.10) has been abysmal, regardless of what I try (router settings, Revo orientation, etc) I can't connect to the router 15' away when my Eee can see it with full strength from the same spot (not sure if its a network manager problem or a driver problem, about half the time I do not get a wireless connection option the rest of the time it acts like it is trying to connect and asks for the password endlessly). I have a 3945ABG from an old laptop so I'm going to see if that will work until I can snake a Cat5 cable to the Revo.

I've finally given up with the Revo wireless and am now using [[COLOR="Red"]homeplugs[/COLOR]]("http://www.faculty-x.net/compare%2085%20homeplugs.htm") instead.

---

### Post by scokem on 2010-05-19
Well, I've joined the club - ordered me one of [these bad boys]("http://www.ebuyer.com/product/182588") earlier and it's arriving tomorrow :)

My plan is to get Ubuntu on there and whack XBMC on top of that so I can have it as my media centre.  I've got a project on the go involving backing up my entire DVD collection and encoding the video using x264 so I've got high quality, small files for streaming from my NAS to various devices around the house and this is going to be the main attraction.

Thanks to the OP for the useful links as I'm sure I'll be needing something in there.  I'll be post back with how I get on with it and I'll even put up some pics when it's complete.

---

### Post by Kevbert on 2010-05-19
Welcome to the club. You may need to max out the memory to 4Gb as the display adapter uses some of the memory. The wireless isn't all that brilliant whether internal (as in US versions) or external (it's probably supplied in the mouse battery compartment if you can't find it), take a look at hotplugs (link in my previous post).
Good luck. I run mine 24/7 as it's continually uploading weather data to the web.
Cheers
Kevin.

---

### Post by sinkyboy2000 on 2010-05-23
I've installed mythbuntu on mine and I love it!

It's taken me a while as I'm pretty new to linux. I was wondering if someone could help with my only remaining problem.  It's already mentioned on this thread, but i don't see a definite answer.

Full screen flash is really choppy, which is a shame as I'd like to use BBC iplayer alot.  I've installed the 185 drivers.  Installing 195 seems pretty complicated and I'm concerned about screwing up the whole system after taking so long to get it working, but is this the only thing that's likely to fix the problem?

---

### Post by sinkyboy2000 on 2010-05-23
Dp

---

### Post by scokem on 2010-05-28
Right then, after I had been messing around with my Revo I decided that I loved it enough already to warrant buying some upgrades for it :)  They arrived today and all work flawlessly:

640GB Western Digital HDD
Intel PCI-E 5100 Wireless card
Keysonic ACK-540 RF v2 Keyboard/trackpad combo

I've reinstalled Ubuntu and have xbmc back on there already.  Gonna have a play with it over the weekend and see how it manages with just the stock 2GB RAM regarding playback etc and then if it needs it, I'll upgrade to 4GB.

---

### Post by avcar on 2010-06-05
hi i have got myself a r3610 2gb came with linpus linux got nowhere with that. so installed ubuntu installed vlc avi's play ok, however mkv files stutter alot. how does the mkv files work on the xbmc?

---

### Post by ePierre on 2010-06-11
Hi!

I bought an Acer Revo R3610 yesterday, but I experienced problems with my HDTV...

I explained the problem but got no help so far... anyone could help me on this one?

The thread is here: [http://ubuntuforums.org/showthread.php?t=1506914](http://ubuntuforums.org/showthread.php?t=1506914)

Thanks in advance!

---

### Post by Kevbert on 2010-06-11
ePierre. What does the Nvidia Setting X Server say for the model of display (see first attachment)? It may be that the monitor is not recognized by Ubuntu. 
I'm using a Panasonic HDTV with the default Nvidia 10.04 display driver (195.36.15) and have to use Overscan Compensation with Ubuntu 10.04 (see second attachment) in order to view the complete desktop. I have to do something similar in Windows 7.

---

### Post by Kevbert on 2010-06-11
_**System Hardware Terminal Outputs**_
Attached is the terminal outputs for my Revo Model: 92.NVFYZ.U2N for
```
lshw
lspci
glxgears
glxinfo
```
I've had to chop the glxinfo output in two in order to upload it here.

---

### Post by ePierre on 2010-06-11
Hey Kevbert,

thanks for your support!

I did'nt know what "overscan compenation" was, it's interesting...

Anyway, I re-selected 1920x1080, clicked "Apply", and... it worked! And I don't have to use overscan compensation.

So I don't know what I did wrong last time... Maybe I forgot to reboot or something like this (rebooting is something you get used to with Windows, but after almost 6 years of Ubuntu, you easily forget... ;))

Anyway, thanks for your help!

---

### Post by matthazley on 2010-06-27
for anyone experiencing .mkv playback issues (ie choppiness and dropped frames) then I may have a possible fix. 

I just got my Revo and installed 10.04 and Boxee and I was getting realllly choppy playback on the mkv's - tried VLC and it was even worse. 

After some digging, I found a line on the wiki for XBMC that said this...

> For NVidia hardware acceleration (VDPAU) in Ubuntu 10.04 install the following packages:

```
sudo apt-get install libvdpau1 nvidia-185-libvdpau
```

I did this, and now my MKV files seem to play in boxee without a problem.

---

### Post by pcpa on 2010-07-05
After rebooting the image is shifted to the left behind the screen.
"Auto setup" function of the monitor can fix this, but this isn't good  solution :)

Does anybody know how to fix this issue?
Does anybody can show xorg file ready for r3610?

Ubuntu 10.4, NVidia drivers 195.36.24  are installed.

**UPD: The problem seems to have resolved itself magically after some Ubuntu updates **:)

---

### Post by easyease on 2010-07-20
Hi, ive got one of these and Im playing wow on it, it can handle 10 man raids well but when i get in 25 mans the fps drops down to 2 frames per second from about 36. I have 2gb of ram in it and am wondering if i bought more would this be an improvement?
 I know there are two 1gb sticks in the machine at the mo so i would need to buy two 2gb sticks. also Im totally unsure what kind of memory this needs, can anyone help me by providing a link to the correct ram on ebuyer.com?
 Sorry for all these questions. I just dont want to spend £80 plus if its not going to make a difference.

---

### Post by Android07 on 2010-08-08
Just got my Revo this week. I installed XBMC Live on it and everything seemed to work. Have it connected to my TV via HDMI. I'm using it for both video and audio.
Today I decided to install Xubuntu with XBMC on top so I have a desktop I can use as well. After installing it popped up saying I needed propriatory Nvidia drivers so I installed them. The video works now but I have no sound. I've tried several things but I've never had to deal with sound before, it has always just worked so I don't know where to start.
I've seen a few posts about it with people posting .asoundrc files etc. but nothing seems to work so any help would be appreciated.

Thanks

---

### Post by scokem on 2010-08-23
> **easyease said:**
> Hi, ive got one of these and Im playing wow on it, it can handle 10 man raids well but when i get in 25 mans the fps drops down to 2 frames per second from about 36. I have 2gb of ram in it and am wondering if i bought more would this be an improvement?...

Little late here with advice but have you made sure the BIOS is set to allow the GPU to use the max (512MB) of the system RAM for the graphics?  Bear in mind that the Revo isn't really designed for gaming though (I'm not a WoW player and have no idea what kind of spec it requires either) 

> **Android07 said:**
> Just got my Revo this week. I installed XBMC  Live on it and everything seemed to work. Have it connected to my TV via  HDMI. I'm using it for both video and audio.
Today I decided to install Xubuntu with XBMC on top so I have a desktop I  can use as well. After installing it popped up saying I needed  propriatory Nvidia drivers so I installed them. The video works now but I  have no sound. I've tried several things but I've never had to deal  with sound before, it has always just worked so I don't know where to  start...

I ran into the same issue when I was setting mine up (I've gone for plain Ubuntu 10.04 64 bit with xbmc bolted on-top).  It's been a few months now, but I believe it was the "Sound" section of the following guide that resolved it for me:

[Greenhughes guide to installing Ubuntu 9.10 and the Boxee Beta on an Acer Aspire Revo (including 64 bit option) ]("http://www.greenhughes.com/content/how-install-ubuntu-910-and-boxee-beta-acer-aspire-revo-including-64-bit-option")

Unfortunately, I can't check and confirm if that is the right guide at the mo (I'm at work and I know there was another guide I was looking at too) so I'll check once I'm home and let you know if it's a different link you need.

---

### Post by Android07 on 2010-08-23
Thanks. I mainly have it working now. The sound works in videos all the time. For some reason the sound only works in the menus for a while. I haven't figured out yet when it stops working. I often don't turn it off. When I first turn it on, everything works perfectly. After a while sound disappears in the menus but keeps working in the videos and music. I'm not too bothered about it, just thought it was strange. 
I normally log in to an XBMC session, I don't think there is any sound in the gnome sessions either.
I only don't turn it off because I haven't set up the wake on USB so I can turn it on with my remote although I haven't tried to do it yet so I don't know if that will be a problem.

I'm looking at buying a surround sound kit at some point in which case I'll probably want to use the SPDIF output but I don't have anything yet that I can connect that to.

---

### Post by scokem on 2010-08-24
Make sure you create the .asoundrc file under your home directory containing the following:
```

pcm.!default {
type plug
slave {
pcm "hdmi"
}
}
```This will enable the menu sounds in xbmc. If you've already done this and are seeing issues then I don't know what else to really suggest as mine is working ok. You could always log into a gnome session and check that the audio is working under there and if not, mess around with the sound output settings until you find the setup that works for you.

---

### Post by pinchez on 2010-08-29
Just bought one of these (R3610 + 4GB, 500GB HD and Windows 7) and would like some advice.

My idea for this machine is to have it as a HTPC for the lounge, I would like to dual boot Windows 7 and Ubuntu (both 64bit). I'm thinking of formating the Revo and re-installing windows 7 then installing Ubuntu and using grub to select OS on boot. One of the floors in my plan is installing Windows 7 as it doesn't come with a physical disk i can work with so is there any way i can download a copy of Windows 7 64bit OEM  to use with my Revo and It's genuine Key?

---

### Post by red321 on 2010-10-16
I have mythtv working well on my 3610. I have the smartfan set in bios, but that only seems to run the fan at a pretty constant 2800 rpm. I wanted to play with fancontrol, which I have used in the past, but neither lm-sensors (sensors-detect) or pmwconfi can find the fanspeed/control fan. Anybody solved this ?

---

### Post by twills805 on 2010-11-05
Hi all, I have had my r3610 for 5 days now and so far utterly impressed. Followed a mish-mash of guides from across the net and in no time had the little thing pumping out HD movies.

Wireless was the only thing that did not work out of the box; it is the one with the RaLink rt3090 chipset, but one of the ebuyer reviewers had already posted a link for the lucid driver. 

However, there is one thing small issue I'd like to get to the bottom of - HDMI sound works, but with a noticeable background hiss. I have ruled out problems with both speakers and TV (xbox 360 hdmi sound works fine), and have unmuted everything I'm meant to in alsamixer (I have nVidia MCP7A sound card which has three S/PDIF options to unmute).

I do not have an .asoundrc file, would this help? At the moment I am swapping external TV speakers from TV headphone jack to Revo headphone jack, with Ubuntu sound output set to analogue... not ideal but it works just fine (also means TV remote doesn't control sound!)

Not sure what to try next...? Any ideas?

Apart from that this really is a little beast, very impressed.

Regards, 
Tom

Edit: seems to be 'hissing' with only a small variety of sound files, with .avi and flash video (i.e. about 90% of what actually gets played on the thing) seemingly OK. Also have the Wii remote fully integrated so I'm all sorted.

---

### Post by mente on 2011-05-02
Hello all,

Recently became the owner of this glancy Acer Revo 3610 :).
Ran into problem. Generally UI is slow. Firefox rendering is slow, unity effects are slow. However HD video rendering works just fine.
Installed proprietary version of nvidia drivers (270). Didn't help. Additional drivers says,that driver is activated but not in use.
Any ideas?

Thanks

---

### Post by timgood on 2011-05-02
> **mente said:**
> Hello all,

Recently became the owner of this glancy Acer Revo 3610 :).
Ran into problem. Generally UI is slow. Firefox rendering is slow, unity effects are slow. However HD video rendering works just fine.
Installed proprietary version of nvidia drivers (270). Didn't help. Additional drivers says,that driver is activated but not in use.
Any ideas?

Thanks

This is a known bug. No fix as yet. See my experiences at [http://teknolegy.blogspot.com/](http://teknolegy.blogspot.com/)

Hope this helps.

---

### Post by mente on 2011-05-03
> **timgood said:**
> This is a known bug. No fix as yet. See my experiences at [http://teknolegy.blogspot.com/](http://teknolegy.blogspot.com/)

Hope this helps.

Thanks for info. Can you share the link to this bug posted?

---

### Post by Kevbert on 2011-05-03
Mente, does this problem occur when using the classic desktop instead of the unity one ?

---

### Post by timgood on 2011-05-03
> **mente said:**
> Thanks for info. Can you share the link to this bug posted?

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/772204](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/772204)

---

### Post by mente on 2011-05-03
> **Kevbert said:**
> Mente, does this problem occur when using the classic desktop instead of the unity one ?

Ubuntu Classic with no effects works smoothly. Ubuntu Classic has the same problem. Looks like problem in compiz.

---

### Post by mente on 2011-05-03
> **timgood said:**
> [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/772204](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/772204)

Looks like it's a simple indicator problem. I don't think it can be mine issue.

---

### Post by Nitros on 2011-06-03
Hello,

First of all, I hve to say I've been running Ubuntu 11.04 Desktop since it's release and I've tried both 64 and 32 bits versions, both with fresh installs.

With my R3610, from the first moment I've installed this new Ubuntu version, my video keeps being laggy in most media player, including Totem, GNOME Mplayer and any flash video on my browser. It stays for a while, usually the firsts minutes and then it runs smoothly the rest of the video.

When it comes to VLC, instead of resulting on laggy video, it results on cracking audio for the same amount of time than video in other players, but video runs smoothly here all the time.

If I try to open two players at the same time, they have troubles at the same time, and they start to run smoothly at the same time as well.

It does not matter if video is HD or low quality, the result is the same, and I have to say it's quite annoying, but I can live with it and wait until this is fixed, even not knowing which is the problem to begin with.

I'm actually running Ubuntu Classic with no desktop effects (metacity), but I've tried it with Unity (compiz) and the result is the same.

Drivers are the Nvidia ones provided by the "Additional Drivers" feature of Ubuntu.

Am I the only R3610 user having this problem? Or is it something that happens to everybody?

Kind regards

PD: Google videochat feature with the browser works perfectly, it never gives me video lag problems.

---

### Post by calcio1 on 2011-06-28
Hi 

Acer R3610 ubuntu 10.30

wireless keyboard and mouse have stopped working overnight for no reason.

Batteries and wireless dongle definitely fine.

Have rebooted, taken out batteries, pressed connect on keyboard etc, won't connect

Any ideas?

thanks

---

### Post by prupert on 2011-07-06
> **calcio1 said:**
> Hi 

Acer R3610 ubuntu 10.30

wireless keyboard and mouse have stopped working overnight for no reason.

Batteries and wireless dongle definitely fine.

Have rebooted, taken out batteries, pressed connect on keyboard etc, won't connect

Any ideas?

thanks

Did you find a fix for this as I have the same issue?

---

### Post by pouark on 2011-10-04
I'm running Ubuntu 10.04 on my Revo 3610, and after long internet search, i still have same problems :

- How can i play flash video on fullscreen (1080p TV) without lag?

is there a new tips to correct this issue?
I've tried a lot of flash version, but problem remains.

Playing flash streamed video is crappy, even more a RTSP flash video, completely laggy

I noticed a little video performance gain with the following procedure:
- enable the hardware accelleration in flash (right clic on the video)
- then desactivate flash control with the following command:
sudo mkdir /etc/adobe && echo "OverrideGPUValidation=true"|sudo tee /etc/adobe/mms.cfg
(or by this command : echo OverrideGPUValidation=true >> ~/.adobe/mms.cfg)

- Better performance by switching to metacity :
metacity --replace


But it absolutly not work with RTSP video....

Anyone have an idea??

NB :
1080p mkv or avi file work just fine with VDPAU in smplayer or with the following command :
mplayer -vo vdpau -vc file.avi

NB:
Excuse me in advance for my english

---

