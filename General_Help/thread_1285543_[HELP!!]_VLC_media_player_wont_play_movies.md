---
title: "[HELP!!] VLC media player wont play movies"
date: 2009-10-07
forum: General Help
---

### Post by Jedi_Knight on 2009-10-07
Hey people. Im a ubuntu noob, and im running ubuntu off a new computer. 

When I open VLC media player or the standard Ubuntu Media Player, and try to play a file, the program closes immediatly. When I open VLC using Terminal, this comes up.
_____________________________

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  80
  Current serial number in output stream:  81
Segmentation fault

**I have no idea what this means, if anyone could translate it into english that would be great. Im thinking that it may be a problem with my video card (I have a new computer and unsure what type or how good it is) What is a good way to find out my video card specs? Thanks in advance for any help ;)**

---

### Post by 3rdalbum on 2009-10-07
What graphics card do you have? If it's an ATI or Nvidia, do you have a proprietary driver loaded for it?

---

### Post by lindsay7 on 2009-10-07
Here is a link to another post.  See my first post, there is a lot of info on adding codecs and VLC and Medibuntu, etc. that you may want to add to your system.


[http://ubuntuforums.org/showthread.php?t=1285431](http://ubuntuforums.org/showthread.php?t=1285431)

---

### Post by jbrown96 on 2009-10-07
1) Check your video card model. ```
lspci | grep VGA
``` If it's Nvidia or ATI, you should make sure the drivers are installed (but they wouldn't be causing this error), System-->Administration-->Hardware Drivers. 

Are you opening a file which launches VLC, or does this happen even if just the program is launched? You may want to delete your profile. ```
rm .config/vlc/vlcrc
```

If that still doesn't work, try removing and reinstalling vlc.
```
sudo apt-get remove vlc && sudo apt-get autoclean && sudo apt-get install vlc
```

---

