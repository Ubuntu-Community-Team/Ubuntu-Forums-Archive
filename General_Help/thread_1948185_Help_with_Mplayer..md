---
title: "Help with Mplayer."
date: 2012-03-27
forum: General Help
---

### Post by MikeVaughanG on 2012-03-27
I have a .avi that I'm trying to play, when I open it in Movie Player I get:

```
An Error Occurred: Could not determine type of Stream
```

When I open it with mplayer from Terminal, the output is 

```

mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing So Live.avi.
MPEG-ES file format detected.
FPS seems to be: 0.642409
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Audio: no sound
Starting playback...
[mpeg4 @ 0x7f763b3cc020]hmm, seems the headers are not complete, trying to guess time_increment_bits
[mpeg4 @ 0x7f763b3cc020]my guess is 5 bits ;)
[mpeg4 @ 0x7f763b3cc020]looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 2062x3231 => 2062x3231 Planar YV12 
Source image dimensions are too high: 2062x3231 (maximum is 2048x2048)
FATAL: Cannot initialize video driver.
[mpeg4 @ 0x7f763b3cc020]warning: first frame is no keyframe
[mpeg4 @ 0x7f763b3cc020]Error at MB: 572
[mpeg4 @ 0x7f763b3cc020]concealing 25541 DC, 25541 AC, 25541 MV errors
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 2062x3231 => 2062x3231 Planar YV12 
Source image dimensions are too high: 2062x3231 (maximum is 2048x2048)
FATAL: Cannot initialize video driver.
[mpeg4 @ 0x7f763b3cc020]low_delay flag incorrectly, clearing it
[mpeg4 @ 0x7f763b3cc020]warning: first frame is no keyframe
[mpeg4 @ 0x7f763b3cc020]illegal MB_type
[mpeg4 @ 0x7f763b3cc020]Error at MB: 963
[mpeg4 @ 0x7f763b3cc020]marker does not match f_code
[mpeg4 @ 0x7f763b3cc020]concealing 26058 DC, 26058 AC, 26058 MV errors
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 2062x3231 => 2062x3231 Planar YV12 
Source image dimensions are too high: 2062x3231 (maximum is 2048x2048)
FATAL: Cannot initialize video driver.
[mpeg4 @ 0x7f763b3cc020]warning: first frame is no keyframe
[mpeg4 @ 0x7f763b3cc020]illegal MB_type
[mpeg4 @ 0x7f763b3cc020]Error at MB: 966
[mpeg4 @ 0x7f763b3cc020]marker does not match f_code
[mpeg4 @ 0x7f763b3cc020]marker does not match f_code
[mpeg4 @ 0x7f763b3cc020]marker does not match f_code
[mpeg4 @ 0x7f763b3cc020]marker does not match f_code
[mpeg4 @ 0x7f763b3cc020]marker does not match f_code
[mpeg4 @ 0x7f763b3cc020]concealing 26058 DC, 26058 AC, 26058 MV errors
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 2062x3231 => 2062x3231 Planar YV12 
Source image dimensions are too high: 2062x3231 (maximum is 2048x2048)
FATAL: Cannot initialize video driver.
[mpeg4 @ 0x7f763b3cc020]concealing 25092 DC, 25092 AC, 25092 MV errors
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 2062x3231 => 2062x3231 Planar YV12 
Source image dimensions are too high: 2062x3231 (maximum is 2048x2048)
FATAL: Cannot initialize video driver.

FATAL: Could not initialize video filters (-vf) or video output (-vo).
```


Any ideas? Any help is appreciated.

---

### Post by yetiman64 on 2012-03-27
Have you tried from the command line to specify other drivers, rather than xv ? Your choices should include vdpau, x11, gl and gl2. Use the code "mplayer -vo help" (without the quotes) to see them all. If you specify vdpau it is best to also specify the video codec as well.

Generally speaking on 11.10 here I get good results specifying the gl2 driver on most file types. This is done in the file ~/.mplayer/config. If a certain file runs better with another driver/codec then I will create a launcher for that, specifically calling the driver and codec (this will override the config file for mplayer).

Some suggestions, first right click the media file and look at the file properties in particular the codec details on the audio/video tab, then try the commands (the first one assumes the .avi file is using h264 encoding, alter this to suit: h264 =  ffh264vdpau; mpeg1,2 = ffmpeg12vdpau; divx/xvid/mpeg4 = ffodivxvdpau; vc1 = ffvc1vdpau; wmv = ffwmv3vdpau)

```
mplayer -vo vdpau -vc ffh264vdpau 'So Live.avi'
```This assumes you are in the same directory as 'So Live.avi', also that the codec in use in the file is h264, try the other codecs that look suitable if not h264.

```
mplayer -vo x11 'So Live.avi'
``` for x11 output.
```
mplayer -vo gl 'So Live.avi'
``` for gl output.
```
mplayer -vo gl2 'So Live.avi'
```for gl2 output. And so on for any other drivers you may want to check out.

It may be the file is an unusual encoding type and you may need to experiment a bit to get it working. If at any time a file plays audio only with no video, open a tab in the terminal running it (right click > new tab) and issue the command,
```
killall -15 mplayer
```this will allow you to move on to testing the next driver or codec without waiting for the file to finish. Good luck.

---

### Post by Jose Catre-Vandis on 2012-03-28
Run ffmpeg on the file to help identify the codec required or issues with file:
```
ffmpeg -i "So Live.avi"
```

Try other players: VLC, ffplay (if configured)

Try encoding with ffmpeg to alternative format:
```
ffmpeg -i "So Live.avi" -qscale 4 So_Live.mp4
```
or just run through ffmpeg:
```
ffmpeg -i "So Live.avi" -acodec copy -vcodec copy So_Live.avi
```

---

### Post by MikeVaughanG on 2012-03-28
I ran

```
ffmpeg -i "So Live.avi" -acodec copy -vcodec copy So_Live.avi
```

As Jose suggested, it worked perfectly, thank you.

Marking as solved.

---

### Post by Jose Catre-Vandis on 2012-03-28
:)

---

