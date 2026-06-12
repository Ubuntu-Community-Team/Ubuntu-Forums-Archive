---
title: "3 Issues, all with my ION and HTCP"
date: 2011-09-15
forum: General Help
---

### Post by guod5 on 2011-09-15
I have been trying for the past 2 days to get my Ubuntu HTPC working. I purchased this [http://www.newegg.com/Product/Product.aspx?Item=N82E16856119042](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119042) and from the reviews on there, it seems like people were able to get a solid ubuntu build on there with full hardware acceleration. I installed Ubuntu 11.04 and  have 3 problems. 

1. When it is plugged into my TV via HDMI, the scaling is WAY off. It is as if I can only see the middle of my desktop, but with a regular monitor, it is fine. I&#8217;ve read on here and saw that some people had an overscan setting in their Nvidia X server settings, but I do not have one. SO how can I correct this? 

2. I have NO hardware acceleration.  I tried going to youtube and playing a video in 360p and it is very choppy. I am assuming this is tied into my driver issue, as after reading, it seems as if I do not have VDPAU configured correctly or at all, right?  Any ideas on this?

3. I have no sound via HDMI. Will this get corrected if I get the other 2 issues sorted out? Or is this another issue all together? 

I have done my best to search and mess around with it, but I am out of ideas or skills here. Not sure if it is a kernal issue, driver issue, or all of the above, any help would be greatly appreciated.

Comp Specs:
Atom 330
2GB Ram
Nvidia ION
60GB OCZ 3 SSD

---

### Post by papibe on 2011-09-15
Let's tackle on problem at a time. Let's start with video acceleration. In order to use Nvidia VDPAU you need to have installed the Nvidia proprietary driver (highly recommended the one suggested on 'Additional drivers'.

In order to make sure you are running the Nvidia driver:

Backup your X config file first:
```
# sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then run the Nvidia X Server Setings:
```
$ gksudo nvidia-settings
```
Select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine.

To make 100% sure you are using the driver, the result of these command:
```
$ grep -i nvidia /var/log/Xorg.0.log
```
Should be something similar to this:
```
(--) PCI:*(0:1:0:0) 10de:0640:3842:c959 nVidia Corporation G96 [GeForce 9500 GT] rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/524288
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "CustomEDID" "DFP-1:/home/pablo/xfiles/newedid.bin"
(**) Sep 15 09:08:17 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 15 09:08:17 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 15 09:08:17 NVIDIA(0):     enabled.
(II) Sep 15 09:08:19 NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
(--) Sep 15 09:08:19 NVIDIA(0): Memory: 1048576 kBytes
...

```
With no errors (indicated by EE)

Once that's out the way: there's 2 ways to get video hardware acceleration (VHA). Using nvidia's vdpau or the generic vaapi. I don't have experience with vaapi, so here we go with vdapau.

First check if the library is installed:
```
$ apt-cache policy libvdpau1
```
If installed the output should look something like this:
```
libvdpau1:
  **Installed: 0.3-2build1**
  Candidate: 0.3-2build1
  Version table:
 *** 0.3-2build1 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
```
If it's not installed, do it like this:
```
$ sudo apt-get install libvdpau1
```
Try again the 'policy' to make sure was installed correctly.

Now you need to test some videos. You need a media player and some HD videos.

For videos, you need to download HD demos, or clips. YouTube videos won't do it (not exactly true, but we can return to this later). Here's an excellent page to download HD test videos (all legal): [http://www.h264info.com/clips.html]("http://www.h264info.com/clips.html")

The best and easy way is to use SMplayer. Install it from the Software Center. Before playing any video, go to Options -> Preferences -> General -> Video. There, set the Output driver to vdpau. Restart SMplayer and test your HD videos.

Tell us how it goes,
Regards.

---

### Post by guod5 on 2011-09-15
your post just blew my mind. I cannot wait to get out of work to go try this. thanks man. I hope this works. I will report as soon as I test it out.:)

---

### Post by guod5 on 2011-09-15
I followed the steps and downloaded a file from your website. It was playing smoothly for a bit, but then got very laggy and choppy. I do not think anything worked. here is the code below.

This was one command
```
   	 	 	 	 	 	  [    11.179] (II) Module glx: vendor="NVIDIA Corporation"  
 [    11.179] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011  
 [    11.183] (II) LoadModule: "nvidia" 
 [    11.183] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so  
 [    11.191] (II) Module nvidia: vendor="NVIDIA Corporation"  
 [    11.195] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011  
 [    11.197] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs  
 [    11.206] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so  
 [    11.209] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32  
 [    11.209] (==) NVIDIA(0): RGB weight 888  
 [    11.209] (==) NVIDIA(0): Default visual is TrueColor  
 [    11.209] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)  
 [    11.209] (**) NVIDIA(0): Option "TwinView" "0"  
 [    11.209] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"  
 [    11.905] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-1)) does not support NVIDIA 3D Vision  
 [    11.905] (II) NVIDIA(GPU-0):     stereo.  
 [    11.909] (II) NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)  
 [    11.909] (--) NVIDIA(0): Memory: 524288 kBytes  
 [    11.909] (--) NVIDIA(0): VideoBIOS: 62.79.66.00.00  
 [    11.909] (--) NVIDIA(0): Interlaced video modes are supported on this GPU  
 [    11.909] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0  
 [    11.909] (--) NVIDIA(0):     SAMSUNG (DFP-1)  
 [    11.909] (--) NVIDIA(0): SAMSUNG (DFP-1): 165.0 MHz maximum pixel clock  
 [    11.909] (--) NVIDIA(0): SAMSUNG (DFP-1): Internal Single Link TMDS  
 [    12.019] (II) NVIDIA(0): Assigned Display Device: DFP-1  
 [    12.020] (II) NVIDIA(0): Validated modes:  
 [    12.020] (II) NVIDIA(0):     "nvidia-auto-select+0+0"  
 [    12.020] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080  
 [    12.057] (--) NVIDIA(0): DPI set to (304, 304); computed from "UseEdidDpi" X config  
 [    12.057] (--) NVIDIA(0):     option 
 [    12.058] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.  
 [    12.066] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"  
 [    12.213] (==) NVIDIA(0): Disabling shared memory pixmaps  
 [    12.213] (==) NVIDIA(0): Backing store disabled  
 [    12.213] (==) NVIDIA(0): Silken mouse enabled  
 [    12.214] (**) NVIDIA(0): DPMS enabled  
 [    12.216] (II) NVIDIA(0): [DRI2] Setup complete  
 [    12.372] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event6)  
 

 
```

and this was the other
```
   	 	 	 	 	 	  

 libvdpau1:  
   Installed: 0.4.1-2ubuntu1  
   Candidate: 0.4.1-2ubuntu1  
   Version table:  
  *** 0.4.1-2ubuntu1 0  
         500 http://us.archive.ubuntu.com/ubuntu/ natty/main i386 Packages  
         100 /var/lib/dpkg/status  
 
```

based on this, shouldn't i have a screen that does not overscan and hardware acceleration?

---

### Post by papibe on 2011-09-15
Did you change the output in SMplayer (Options -> Preferences -> General -> Video, set to VDPAU) ?

If not, could you post the video log that generates Mplayer?

While playing the file on SMplayer, go to Options -> View logs -> Mplayer. Copy/paste what it is on that window.

Note that we need the log of Mplayer which is the underneath player do it the heavy lifting (SMplayer is just the interface).

Regards.

---

### Post by guod5 on 2011-09-15
> **papibe said:**
> Did you change the output in SMplayer (Options -> Preferences -> General -> Video, set to VDPAU) ?

If not, could you post the video log that generates Mplayer?

While playing the file on SMplayer, go to Options -> View logs -> Mplayer. Copy/paste what it is on that window.

Note that we need the log of Mplayer which is the underneath player do it the heavy lifting (SMplayer is just the interface).

Regards.

yeah i did that. Here is the log
```
  p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 60817749 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/stream/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -nocache -osdlevel 0 -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/stream/Desktop/The Bourne Ultimatum - Trailer.mp4
  MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
  Playing /home/stream/Desktop/The Bourne Ultimatum - Trailer.mp4.
 libavformat file format detected.
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=und
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [H264]  1920x816  24bpp  23.976 fps  7403.5 kbps (903.8 kbyte/s)
 Clip info:
  major_brand: isom
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=isom
  minor_version: 1
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=1
  compatible_brands: isomavc1
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isomavc1
 ID_CLIP_INFO_N=3
 ID_FILENAME=/home/stream/Desktop/The Bourne Ultimatum - Trailer.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=7403536
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=816
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=94760
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=89.22
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Couldn't open video filter '***'.
 ***: cannot add video filter
 [***] Init
 [***] Updating font cache
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 AUDIO: 48000 Hz, 2 ch, s16le, 94.8 kbit/6.17% (ratio: 11845->192000)
 ID_AUDIO_BITRATE=94760
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=faad
 Starting playback...
 [VD_FFMPEG] Trying pixfmt=0.
 Movie-Aspect is undefined - no prescaling applied.
 VO: [vdpau] 1920x816 => 1920x816 H.264 VDPAU acceleration 
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 [Mixer] No hardware mixing, inserting volume filter.
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
              ************************************************
            **** Your system is too SLOW to play this!  ****
            ************************************************
  Possible reasons, problems, workarounds:
 - Most common: broken/buggy _audio_ driver
   - Try -ao sdl or use the OSS emulation of ALSA.
   - Experiment with different values for -autosync, 30 is a good start.
 - Slow video output
   - Try a different -vo driver (-vo help for a list) or try -framedrop!
 - Slow CPU
   - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
     e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
 - Broken file
   - Try various combinations of -nobps -ni -forceidx -mc 0.
 - Slow media (NFS/SMB mounts, DVD, VCD etc)
   - Try -cache 8192.
 - Are you using -cache to play a non-interleaved AVI file?
   - Try -nocache.
 Read DOCS/HTML/en/video.html for tuning/speedup tips.
 If none of this helps you, read DOCS/HTML/en/bugreports.html.
  Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
   Exiting... (End of file)
 ID_EXIT=EOF
 
```

any chance you could log in through teamviewer and work some magic?

---

### Post by papibe on 2011-09-15
I downloaded the same video to compare results. So far the main differenc is that I'm using alsa as audio output, and you pulse.

Go to Options -> Preferences -> General -> Audio
Set the 'Output driver:' to 'User default'. That will enable the next field.
Set that to:
```
alsa,
```
(there's a comma at the end).

Restart SMplayer, and tell me how it goes.
Regards.

---

### Post by guod5 on 2011-09-15
I did that and it is MUCH smoother. The sound still is not coming through HDMI, and only comes through the speaker built into the computer. This is still progress though.

I am assuming you mean user defined, not default, right? 

Here is my code```
  p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 60817778 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/stream/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -nocache -osdlevel 0 -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/stream/Desktop/The Bourne Ultimatum - Trailer.mp4
  MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
  Playing /home/stream/Desktop/The Bourne Ultimatum - Trailer.mp4.
 libavformat file format detected.
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=und
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [H264]  1920x816  24bpp  23.976 fps  7403.5 kbps (903.8 kbyte/s)
 Clip info:
  major_brand: isom
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=isom
  minor_version: 1
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=1
  compatible_brands: isomavc1
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isomavc1
 ID_CLIP_INFO_N=3
 ID_FILENAME=/home/stream/Desktop/The Bourne Ultimatum - Trailer.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=7403536
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=816
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=94760
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=89.22
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Couldn't open video filter '***'.
 ***: cannot add video filter
 [***] Init
 [***] Updating font cache
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 AUDIO: 48000 Hz, 2 ch, s16le, 94.8 kbit/6.17% (ratio: 11845->192000)
 ID_AUDIO_BITRATE=94760
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=faad
 Starting playback...
 [VD_FFMPEG] Trying pixfmt=0.
 Movie-Aspect is undefined - no prescaling applied.
 VO: [vdpau] 1920x816 => 1920x816 H.264 VDPAU acceleration 
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 [Mixer] No hardware mixing, inserting volume filter.
 
```

---

### Post by guod5 on 2011-09-15
I got HDMI sound to work by downloading the gnome alsa mixer and unmuting the channel.

---

### Post by papibe on 2011-09-15
To change the sound to the HDMI output, you have to change the system sound settings. It should be very simple. Follow this [tutorial]("http://ubuntuforums.org/showthread.php?t=1741294") with pictures.

Regards.

---

### Post by guod5 on 2011-09-15
> **papibe said:**
> To change the sound to the HDMI output, you have to change the system sound settings. It should be very simple. Follow this [tutorial]("http://ubuntuforums.org/showthread.php?t=1741294") with pictures.

Regards.

yeah,in the post above, i got the sound to work. that was pretty cool. thanks for the info.


so the 2 major issues right now are:

lag of any flash or video playing in something other than SMplayer

and

major overscaning on my desktop (can't see top bar and only see half of ubuntu taskbar)

---

### Post by papibe on 2011-09-15
Regarding the over scaning: in the case of my Sony Bravia and my brother's Samsung, the problems was in the TV side. It seems that most HDTV follow the same standard as old analog TVs and crop (mild zoom actually) the signal by default.

In the Sony you can fix it by setting 'Full Pixel' to Screen -> Display Area. In the Samsung set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Regards.

---

### Post by guod5 on 2011-09-15
> **papibe said:**
> Regarding the over scaning: in the case of my Sony Bravia and my brother's Samsung, the problems was in the TV side. It seems that most HDTV follow the same standard as old analog TVs and crop (mild zoom actually) the signal by default.

In the Sony you can fix it by setting 'Full Pixel' to Screen -> Display Area. In the Samsung set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Regards.

Wow. I just did the screen size thing, and now it is great. No overscanning at all.

any ideas as to how to fix this choppy video and stuff?

---

### Post by papibe on 2011-09-15
Could you post a couple of screenshots of your settings in these two tabs in SMplayer:
```
Options -> Preferences -> General -> Video
```
and this one:
```
Options -> Preferences -> General -> Audio
```
Regards.

---

### Post by guod5 on 2011-09-15
here you are sir.

[[IMG]http://img.photobucket.com/albums/v258/DouGMoD/th_videosetting.png[/IMG]](http://img.photobucket.com/albums/v258/DouGMoD/videosetting.png)
[[IMG]http://img.photobucket.com/albums/v258/DouGMoD/th_audiosetting.png[/IMG]](http://img.photobucket.com/albums/v258/DouGMoD/audiosetting.png)

[URL="http://img.photobucket.com/albums/v258/DouGMoD/audiosetting.png"]
[/URL]

---

### Post by papibe on 2011-09-15
Also try this: it looks like the 'audio equalizer' produce some trouble for some people. Disable it, restart SMplayer and test the video again.

BTW, is it the only one you downloaded? It could be good to test another videos.

Regards.

---

### Post by guod5 on 2011-09-15
I disabled that and I still notice a little bit of lag in the playback. i am getting 2 more test videos as we speak. Do the settings in this smplayer somehow go global? As in, if we get the SMplayer settings down, will we have figured out why flash, divx-webplugin, etc, is slow?

---

### Post by guod5 on 2011-09-15
Got 2 videos, I am legend 1080p sample and Fantastic 4 sample. 

Both still lag.

Here is the I am legend code
```
  p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 37749091 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/stream/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -nocache -osdlevel 0 -slices -channels 2 -softvol -softvol-max 110 /home/stream/Desktop/I Am Legend - Trailer.mp4
  MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
  Playing /home/stream/Desktop/I Am Legend - Trailer.mp4.
 libavformat file format detected.
 [aac @ 0xa040540]Duplicate channel tag found, attempting to remap.
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=und
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [H264]  1920x816  24bpp  23.976 fps  7979.5 kbps (974.1 kbyte/s)
 Clip info:
  major_brand: isom
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=isom
  minor_version: 1
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=1
  compatible_brands: isom
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isom
 ID_CLIP_INFO_N=3
 ID_FILENAME=/home/stream/Desktop/I Am Legend - Trailer.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=7979480
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=816
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=2.3529
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=258320
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_START_TIME=0.00
 ID_LENGTH=123.24
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Couldn't open video filter '***'.
 ***: cannot add video filter
 [***] Init
 [***] Updating font cache
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 AUDIO: 48000 Hz, 2 ch, s16le, 258.3 kbit/16.82% (ratio: 32290->192000)
 ID_AUDIO_BITRATE=258320
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=faad
 Starting playback...
 [VD_FFMPEG] Trying pixfmt=0.
 Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=2.3529
 VO: [vdpau] 1920x816 => 1920x816 H.264 VDPAU acceleration 
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 [Mixer] No hardware mixing, inserting volume filter.
              ************************************************
            **** Your system is too SLOW to play this!  ****
            ************************************************
  Possible reasons, problems, workarounds:
 - Most common: broken/buggy _audio_ driver
   - Try -ao sdl or use the OSS emulation of ALSA.
   - Experiment with different values for -autosync, 30 is a good start.
 - Slow video output
   - Try a different -vo driver (-vo help for a list) or try -framedrop!
 - Slow CPU
   - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
     e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
 - Broken file
   - Try various combinations of -nobps -ni -forceidx -mc 0.
 - Slow media (NFS/SMB mounts, DVD, VCD etc)
   - Try -cache 8192.
 - Are you using -cache to play a non-interleaved AVI file?
   - Try -nocache.
 Read DOCS/HTML/en/video.html for tuning/speedup tips.
 If none of this helps you, read DOCS/HTML/en/bugreports.html.
  Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 
```

Fantastic 4
```
  p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 37749091 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/stream/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -nocache -osdlevel 0 -slices -channels 2 -softvol -softvol-max 110 /home/stream/Desktop/Fantastic Four - Rise of the Silver Surfer - Trailer.mp4
  MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
  Playing /home/stream/Desktop/Fantastic Four - Rise of the Silver Surfer - Trailer.mp4.
 libavformat file format detected.
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=und
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [H264]  1280x544  24bpp  23.976 fps  5714.4 kbps (697.6 kbyte/s)
 Clip info:
  major_brand: isom
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=isom
  minor_version: 1
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=1
  compatible_brands: isomavc1
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isomavc1
  artist: 20th Century Fox
 ID_CLIP_INFO_NAME3=artist
 ID_CLIP_INFO_VALUE3=20th Century Fox
  title: Fantastic Four: Rise of the Silver Surfer - Theatrical Trailer
 ID_CLIP_INFO_NAME4=title
 ID_CLIP_INFO_VALUE4=Fantastic Four: Rise of the Silver Surfer - Theatrical Trailer
  date: 2007
 ID_CLIP_INFO_NAME5=date
 ID_CLIP_INFO_VALUE5=2007
 ID_CLIP_INFO_N=6
 ID_FILENAME=/home/stream/Desktop/Fantastic Four - Rise of the Silver Surfer - Trailer.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=5714400
 ID_VIDEO_WIDTH=1280
 ID_VIDEO_HEIGHT=544
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=123552
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=129.24
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Couldn't open video filter '***'.
 ***: cannot add video filter
 [***] Init
 [***] Updating font cache
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 AUDIO: 48000 Hz, 2 ch, s16le, 123.6 kbit/8.04% (ratio: 15444->192000)
 ID_AUDIO_BITRATE=123552
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=faad
 Starting playback...
 [VD_FFMPEG] Trying pixfmt=0.
 Movie-Aspect is undefined - no prescaling applied.
 VO: [vdpau] 1280x544 => 1280x544 H.264 VDPAU acceleration 
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 [Mixer] No hardware mixing, inserting volume filter.
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
              ************************************************
            **** Your system is too SLOW to play this!  ****
            ************************************************
  Possible reasons, problems, workarounds:
 - Most common: broken/buggy _audio_ driver
   - Try -ao sdl or use the OSS emulation of ALSA.
   - Experiment with different values for -autosync, 30 is a good start.
 - Slow video output
   - Try a different -vo driver (-vo help for a list) or try -framedrop!
 - Slow CPU
   - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
     e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
 - Broken file
   - Try various combinations of -nobps -ni -forceidx -mc 0.
 - Slow media (NFS/SMB mounts, DVD, VCD etc)
   - Try -cache 8192.
 - Are you using -cache to play a non-interleaved AVI file?
   - Try -nocache.
 Read DOCS/HTML/en/video.html for tuning/speedup tips.
 If none of this helps you, read DOCS/HTML/en/bugreports.html.
  Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 
```

---

### Post by papibe on 2011-09-15
Unfortunately no, but if it works on SMplayer will probably work on XBMC (which is the preferred tool for most HTPC running Linux). Are you planning to install it BTW?

I moved to my laptop (it has 11.04 and an HDMI ouput). I didn't realize that you can also select the Nvidia audio directly. I have this additional options on Audio -> Output driver:
[INDENT]alsa (1.3 HDA - Nvidia)
alsa (1.6 HDA - Nvidia)[/INDENT]
Try if they improve the playing.

Regards.

---

### Post by guod5 on 2011-09-15
> **papibe said:**
> Unfortunately no, but if it works on SMplayer will probably work on XBMC (which is the preferred tool for most HTPC running Linux). Are you planning to install it BTW?

I moved to my laptop (it has 11.04 and an HDMI ouput). I didn't realize that you can also select the Nvidia audio directly. I have this additional options on Audio -> Output driver:[INDENT]alsa (1.3 HDA - Nvidia)
alsa (1.6 HDA - Nvidia)[/INDENT]Try if they improve the playing.

Regards.
I only have options for also .0, .1, .3...Mine od not show 1.x like yours. I tried with .3. Below are the results.

BTW, if I put XBMC on here, would I still have a browser and would the browser get the hardware acceleration? That way I can watch things like  youtube, hulu, cnn, etc.


```
  p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa:device=hw=0.3 -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 37749091 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/stream/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -nocache -osdlevel 0 -slices -channels 2 -softvol -softvol-max 110 /home/stream/Desktop/I Am Legend - Trailer.mp4
  MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
  Playing /home/stream/Desktop/I Am Legend - Trailer.mp4.
 libavformat file format detected.
 [aac @ 0x970f540]Duplicate channel tag found, attempting to remap.
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=und
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [H264]  1920x816  24bpp  23.976 fps  7979.5 kbps (974.1 kbyte/s)
 Clip info:
  major_brand: isom
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=isom
  minor_version: 1
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=1
  compatible_brands: isom
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isom
 ID_CLIP_INFO_N=3
 ID_FILENAME=/home/stream/Desktop/I Am Legend - Trailer.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=7979480
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=816
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=2.3529
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=258320
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_START_TIME=0.00
 ID_LENGTH=123.24
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Couldn't open video filter '***'.
 ***: cannot add video filter
 [***] Init
 [***] Updating font cache
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 AUDIO: 48000 Hz, 2 ch, s16le, 258.3 kbit/16.82% (ratio: 32290->192000)
 ID_AUDIO_BITRATE=258320
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=faad
 Starting playback...
 [VD_FFMPEG] Trying pixfmt=0.
 Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=2.3529
 VO: [vdpau] 1920x816 => 1920x816 H.264 VDPAU acceleration 
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 [Mixer] No hardware mixing, inserting volume filter.
 Too many buffered pts
 Too many buffered pts
              ************************************************
            **** Your system is too SLOW to play this!  ****
            ************************************************
  Possible reasons, problems, workarounds:
 - Most common: broken/buggy _audio_ driver
   - Try -ao sdl or use the OSS emulation of ALSA.
   - Experiment with different values for -autosync, 30 is a good start.
 - Slow video output
   - Try a different -vo driver (-vo help for a list) or try -framedrop!
 - Slow CPU
   - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
     e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
 - Broken file
   - Try various combinations of -nobps -ni -forceidx -mc 0.
 - Slow media (NFS/SMB mounts, DVD, VCD etc)
   - Try -cache 8192.
 - Are you using -cache to play a non-interleaved AVI file?
   - Try -nocache.
 Read DOCS/HTML/en/video.html for tuning/speedup tips.
 If none of this helps you, read DOCS/HTML/en/bugreports.html.
  Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 Too many buffered pts
 
```

---

### Post by papibe on 2011-09-15
It has been suggested that the installation of ffmpeg (a command line video converting tool) can be improve the use of VDPAU.

It won't hurt if you install it:
```
$ sudo apt-get -s install ffmpeg
```
Regards.

---

### Post by guod5 on 2011-09-15
> **papibe said:**
> It has been suggested that the installation of ffmpeg (a command line video converting tool) can be improve the use of VDPAU.

It won't hurt if you install it:
```
$ sudo apt-get -s install ffmpeg
```Regards.

i already have it right? ```

sudo apt-get -s install ffmpeg
[sudo] password for stream: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

thanks

---

### Post by papibe on 2011-09-15
Sorry that we are little stuck on this.

In the mean time, let's add VDPAU to the flashplayer in Firefox.

First check if the flashplayer you have installed have VDPAU support:
```
$ strings /usr/lib/firefox/plugins/flashplugin-alternative.so  |grep -i vdpau

```
The output should be something like this:
```

H264 - VDPAU - CPU
H264 - VDPAU - VDPAU
libvdpau.so
libvdpau.so.1
GL_NV_vdpau_interop
glVDPAUInitNV
glVDPAUFiniNV
glVDPAUUnregisterSurfaceNV
glVDPAUSurfaceAccessNV
glVDPAUMapSurfacesNV
glVDPAUUnmapSurfacesNV
glVDPAURegisterOutputSurfaceNV

```
If so, we are on business.

Edit (or create) this file /etc/adobe/mms.cfg:
```
$ cd /etc/
$ sudo mkdir adobe
$ cd adobe
$ gksudo gedit mms.cfg
```
Edit the file so the content have these two lines:
```
OverrideGPUValidation=true
EnableLinuxHWVideoDecode=1
```
Save and close the file, and restart Firefox. Go to youtube and play an HD video.

Regards.

EDIT: for example [this]("http://www.youtube.com/watch?v=XITHbsUUlYI") one. BTW even if can play it smoothly, you probably won't be able to stream it as fast as it needs to be played. Just paused it and wait it gets downloaded.

---

### Post by guod5 on 2011-09-16
I get stuck here. I put this code in but nothing happens, it goes to the next line in terminal, like nothing happened.

```

gksudo mms.cfg
```

i tried doing it like this, ```
sudo gedit mms.cfg
```

this created the file with those 2 lines in it, but no go on video accel.

---

### Post by papibe on 2011-09-16
Oops, my mistake. It should be:
```
$ gksudo gedit mms.cfg
```
(already corrected above)

---

### Post by papibe on 2011-09-16
A few ideas before going to bed:

If by choppy video you mean [screen tearing]("http://en.wikipedia.org/wiki/Video_tearing"). You can fix that by enabling 'Sync to VBlank' in the 'Nvidia X Server Settings'. It's in two places: 'X Server XVideo Settings' and 'OpenGL Settings'.

Maybe it is necessary to update your BIOS in order to take fully advantage of the hardware. This blog [post]("http://joel.thegoodmanblog.com/2119/getting-xbmc-onto-a-foxconn-nt330i/") has some guidelines at the end of the page.

Let's continue tomorrow,
Good Night.


Edit1: It could be a good idea to also test some 720p videos.

Edit2: It looks like the RAM that the graphic card is set on the BIOS, check that is set to 512Mb instead of the 256Mb default.

---

### Post by guod5 on 2011-09-16
A couple of things here...

1. no need to  apologize, you have have gone above and beyond. Even though it is taking a while, as you can see, you are the only one that was nice enough / brave enough to take on this mission hah. so thank you very much.

2. I tried to do the gedit with gksudo and added the text to the cfg file. I hit save and closed it. After I closed it, terminal gave me this 
```
stream@stream-nT-330i:~$ gksudo gedit mms.cfg

(gedit:1756): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1756): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DZ7V1V': No such file or directory

(gedit:1756): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1756): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.07ZZ1V': No such file or directory

(gedit:1756): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

3. I have had the sync on in the x server settings and still see lag, lines or flickering.

4. For some reason, my bios has it set to auto mode and it shows 256mb. I cannot change anything. It will not let me change from auto mode....maybe this is the issue?

Edit: could this have something to do with it?

[http://ubuntuforums.org/showthread.php?t=1666931](http://ubuntuforums.org/showthread.php?t=1666931)

Edit2: Is it possible that I need a 4gb stick in order to enable the 512mb video? If so, that is crazy. I read about it in a thread, but cannot remember where. Do you think there would be a way to bypass this?

---

### Post by papibe on 2011-09-16
Try to test some 720p videos to see if at least acceleration is working on a lower resolution.

Regards.

---

### Post by guod5 on 2011-09-16
the fantastic 4 sample I downloaded was 720 and it lags too. I also tried 720 on youtube with no success. At 360 on youtube, it kind of plays smoothly, but there is flickering and pixelization

---

### Post by papibe on 2011-09-16
I'm almost run out of ideas...

Let's take the sound out of the equation and test FPS on those 2 videos. Run this command from the command line:
```
$ mplayer -benchmark -nosound -ao null -vo vdpau The\ Bourne\ Ultimatum\ -\ Trailer.mp4 
```
Post the lines at the end. The ones that looks like this:
```
BENCHMARKs: VC:  57.444s VO:   6.543s A:   1.482s Sys:  23.507s =   88.977s
BENCHMARK%: VC: 64.5608% VO:  7.3541% A:  1.6657% Sys: 26.4193% = 100.0000%

```
Do the same for the 720p video.

Regards.

Note: mplayer will write log messages on the terminal, but display the movie in a windows without any menu.

Useful shortcuts:
[INDENT]f to switch back and forth fullscreen.
q to stop playback.[/INDENT]

---

### Post by guod5 on 2011-09-19
> **papibe said:**
> I'm almost run out of ideas...

Let's take the sound out of the equation and test FPS on those 2 videos. Run this command from the command line:
```
$ mplayer -benchmark -nosound -ao null -vo vdpau The\ Bourne\ Ultimatum\ -\ Trailer.mp4 
```
Post the lines at the end. The ones that looks like this:
```
BENCHMARKs: VC:  57.444s VO:   6.543s A:   1.482s Sys:  23.507s =   88.977s
BENCHMARK%: VC: 64.5608% VO:  7.3541% A:  1.6657% Sys: 26.4193% = 100.0000%

```
Do the same for the 720p video.

Regards.

Note: mplayer will write log messages on the terminal, but display the movie in a windows without any menu.

Useful shortcuts:
[INDENT]f to switch back and forth fullscreen.
q to stop playback.[/INDENT]


thanks for this man. I will try to get it going today.

---

### Post by guod5 on 2011-09-21
i have not had a chance to try your FPS test out, but i will do it after work today.

If this does not prove anything to us, should I try maybe ubuntu lucid or another distro?

thanks man

---

### Post by guod5 on 2011-09-21
This is for the Bourne trailer

```
BENCHMARKs: VC:  91.669s VO:  22.672s A:   0.000s Sys:   0.905s =  115.245s
BENCHMARK%: VC: 79.5426% VO: 19.6724% A:  0.0000% Sys:  0.7850% = 100.0000%

```

This is for Fantastic 4
```
BENCHMARKs: VC:  91.669s VO:  22.672s A:   0.000s Sys:   0.905s =  115.245s
BENCHMARK%: VC: 79.5426% VO: 19.6724% A:  0.0000% Sys:  0.7850% = 100.0000%

```

And just a thought, could my SSD have anything to do with this? Do I need a driver for my ssd hard drive in linux?

---

### Post by papibe on 2011-09-21
Unfortunately those are not very good results. For a 89secs clip, it's taken 115 secs to decode it and play it. So the video card is doing little to none to help decode the stream.

I don't know if going back to 10.04 is going to be better, but you don't loose anything by trying.

Last resort before reinstalling: install XBMC. It has a custom mplayer that may be produce better results. In this [thread]("http://ubuntuforums.org/showthread.php?t=1766855&highlight=xbmc") we discuss 2 ways of installing it on 11.04.

Regards.

---

### Post by guod5 on 2011-09-21
i installed XBMC on  it and still have terrible lag. is is possible my unit is defective? it makes not sense. I made sure vdpau was selected in XMBC and still tons of lag

---

### Post by guod5 on 2011-09-21
is there a way to get the chipset drivers in linux? I installed windows 7 on the computer and had the same issues I had in linux. I downloaded the latest nvidia video driver and still had issues. I thought i had a defective unit, but in the device manager, it showed there was something with a driver error called "coprocessor"

I went to foxconn website and downloaded their chipset driver which installed 3 nvidia drivers and then restarted the computer. After doing this, the computer handles 1080p pretty well and seems decent. With ubuntu, i never got close to this smoothness and think the chipset may have something to do with it.

any ideas?

---

### Post by papibe on 2011-09-22
Wow, very interesting.

Was it a BIOS update? or a firmware update?

I remember when I setup my brother's HTPC (a Zotac Mag) that we upgrade the BIOS, and that was it. Anything else worked just fine.

If you updated the BIOS or the firmware, it maybe possible that Ubuntu/vdpau may work now. However, if it was a software/driver update, there will be no change.

Anyway, I'd say if it is working on Windows 7, let it be.

Enjoy your HTPC!
Regards.

---

### Post by guod5 on 2011-09-23
> **papibe said:**
> Wow, very interesting.

Was it a BIOS update? or a firmware update?

I remember when I setup my brother's HTPC (a Zotac Mag) that we upgrade the BIOS, and that was it. Anything else worked just fine.

If you updated the BIOS or the firmware, it maybe possible that Ubuntu/vdpau may work now. However, if it was a software/driver update, there will be no change.

Anyway, I'd say if it is working on Windows 7, let it be.

Enjoy your HTPC!
Regards.

I think it was just the windows driver for the motherboard and nvidia chipset. I also updated to their experimental bios and noticed no change. BUT I am sending the unit back to newegg, as I think the ION chipset could have been defective. Things kind of played smoothly in windows, but then if I tried flash or anything else, the CPU usage went to 99% and it was unusable. Sometimes it would freeze when trying to play the videos too. I downloaded the same test videos that I had on Ubuntu and saw pretty smooth playback. Then I would try the videos again, and noticed tons of lag and choppy frames. So I would think this is beyond a software issue. 

The new unit should be here in a couple of days. I am going to give ubuntu another shot, as I can just go over everything we talked about in this thread haha

---

### Post by papibe on 2011-09-23
[-o< I hope the new one would work better!

Tell us how it goes,
Regards.

---

