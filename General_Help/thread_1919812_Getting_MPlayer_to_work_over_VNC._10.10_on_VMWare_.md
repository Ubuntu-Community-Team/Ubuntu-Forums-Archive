---
title: "Getting MPlayer to work over VNC. 10.10 on VMWare Fusion"
date: 2012-02-03
forum: General Help
---

### Post by defferoo on 2012-02-03
I'm having trouble getting MPlayer to play videos over VNC on Maverick. The OS is installed on VMWare (this is for a research project).

When I try to open MPlayer on a VNC display, i get the following error. I'm trying to use XVideo as the video output.

> mplayer -display :1 mplayer/corolla.mpeg 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mplayer/corolla.mpeg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[B][VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.[/B]
[gl] no GLX support present
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 352x288 => 384x288 Planar YV12 
[B]X server image format not supported, please contact the developers
FATAL: Cannot initialize video driver.

FATAL: Could not initialize video filters (-vf) or video output (-vo).[/B]


Exiting... (End of file)

I know you can specify -vo xv, but that doesn't work either, if nothing is specified, it tries other drivers as well.

When I run xvinfo to see if I have any adaptors, I get

> xvinfo -display :1
X-Video Extension version 2.2
screen #0
 no adaptors present

However, I believe the XVideo module is loaded, since running xdpyinfo gives me

> xdpyinfo -display :1
name of display:    :1.0
version number:    11.0
vendor string:    The XFree86 Project, Inc
vendor release number:    40300000
XFree86 version: 4.3.0
maximum request size:  4194300 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    2
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x40000f, revert to PointerRoot
number of extensions:    24
    BIG-REQUESTS
    DEC-XTRAP
    DOUBLE-BUFFER
    Extended-Visual-Information
    FontCache
    GLX
    LBX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RECORD
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    VNC-EXTENSION
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFree86-Bigfont
    XTEST
    **XVideo**
default screen number:    0
number of screens:    1... etc etc

I've installed VMWare tools, but I'm running a custom kernel so I don't have a window manager running, just CLI.

---

