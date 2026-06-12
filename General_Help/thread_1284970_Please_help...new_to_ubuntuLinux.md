---
title: "Please help...new to ubuntu/Linux"
date: 2009-10-07
forum: General Help
---

### Post by Jedi_Knight on 2009-10-07
I purchased a computer for $9 at an online auction recently, and im on it now. Although extremely cheap, its not a bad computer. However, when i open a movie with VLC media player or the default media player, the program closes immediately. Why?

Also, this may sound silly, but how do i exit fullscreen in firefox?

---

### Post by mac9416 on 2009-10-07
> Also, this may sound silly, but how do i exit fullscreen in firefox? 

I'll let better men handle the first question. I can answer this one real quick, though. Hit F11. That toggles fullscreen.

---

### Post by howefield on 2009-10-07
> **Jedi_Knight said:**
> ...when i open a movie with VLC media player or the default media player, the program closes immediately. Why?

Try opening the file via a terminal and post any error(s) here.

> Also, this may sound silly, but how do i exit fullscreen in firefox?

Try the F11 key.

---

### Post by Jedi_Knight on 2009-10-07
I feel like an idiot, thanks F11 worked fine :D
Yeah i tried that, didnt work. Maybe its an issue with my video card? I really appreciate your help guys

---

### Post by abhilashm86 on 2009-10-07
> **Jedi_Knight said:**
> I feel like an idiot, thanks F11 worked fine :D
Yeah i tried that, didnt work. Maybe its an issue with my video card? I really appreciate your help guys

post the output of this command, tells details of pci, other devices with your system, 
```
lspci

```

---

### Post by Jedi_Knight on 2009-10-07
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by Vaphell on 2009-10-07
running totem or vlc from terminal doesn't produce any output at crash?

---

### Post by Jedi_Knight on 2009-10-07
Unfortuntatly i dont have my external hard drive (which has all my media on it, i.e movies) so i cant test VLC or totem. BUt when i try to open TVTime (a program for watching tv through a tv card) in terminal, tis comes up
Cannot allocate enough off-screen video memory.  This may be fixed by:

      1. Closing or restarting large X applications.
      2. Lowering the input width of tvtime (--inputwidth parameter).
      3. Lowering your colour depth or highest configured resolution.
      4. Increasing the amount of video memory in your X config file
         (for example, if you are using the i810 XFree86 driver.)

    See [http://tvtime.net/](http://tvtime.net/) for more information.


    Cannot allocate enough off-screen video memory.  This may be fixed by:

      1. Closing or restarting large X applications.
      2. Lowering the input width of tvtime (--inputwidth parameter).
      3. Lowering your colour depth or highest configured resolution.
      4. Increasing the amount of video memory in your X config file
         (for example, if you are using the i810 XFree86 driver.)

    See [http://tvtime.net/](http://tvtime.net/) for more information.

---

### Post by t0p on 2009-10-07
> **Jedi_Knight said:**
> Unfortuntatly i dont have my external hard drive (which has all my media on it, i.e movies) so i cant test VLC or totem.
You could download a video file from Youtube in order to produce the output we need. The tvtime error message may very well be related. But to diagnose the vlc/totem problem for sure, we need to see vlc/totem output.

---

### Post by artesian_spring on 2009-10-10
I'm experiencing a similar problem.
Here is the output of 'vlc dvd:///dev/dvd':

```
******@***:~$ vlc dvd:///dev/dvd
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: THE_LAST_SAMURAI_DISC_1
libdvdnav: DVD Serial Number: 30629A9A
libdvdnav: DVD Title (Alternative): THE_LAST_SAMURAI_DISC_1
libdvdnav: Unable to find map file '/home/daniel/.dvdnav/THE_LAST_SAMURAI_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000be76
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000461] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
Segmentation fault
```

---

### Post by artesian_spring on 2009-10-10
It looks like this is related to [Bug #374258]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/374258").
The final comment there suggests modifying /etc/X11/xorg.conf; haven't tried it yet myself.
This [thread]("http://ubuntuforums.org/archive/index.php/t-1134283.html") also looks promising. I followed the advice from the following comment and the test feature in the Multimedia Systems Selector worked--haven't retested playing a DVD yet.
> ellgor                                April 26th, 2009, 02:01 PM
Hi,

If you are still having problems try this:

Goto>System>Preferences>Multimedia Systems Selector (it may not be enabled in your menu, enable if not)
Choose Video, under default output change this to X Window System (No Xv), it may need a reboot to take effect, hope this helps.

Regards, Ellgor.

From the two threads listed above, it seems like this is a problem with integrated Intel graphics cards. The output of lspci on my machine includes the line:

```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

---

### Post by artesian_spring on 2009-10-11
I made the changes to Multimedia Systems Selector mentioned in the quote in my comment above and Totem works now.

---

