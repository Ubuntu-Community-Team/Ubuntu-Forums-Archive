---
title: "vlc TagLib errors nvlc"
date: 2009-10-21
forum: General Help
---

### Post by Esthellin on 2009-10-21
I am running vlc from the command line in Jaunty and playing all music from it. However, some output keeps appearing, no matter what verbosity I set in the vlc preferences (even checking the "Be quiet" checkbox does not get rid of the messages).
The output is like this:

Note: music is a symbolic link to my music folder.

10:50{~} vlc --random music
VLC media player 0.9.9a Grishenko
00000001 main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
00000001 main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
00000001 main libvlc debug: translation test: code is "C"
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/althalus/.dvdnav/.map'
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type TDAT.  It will be discarded from the tag.
TagLib: MPEG::Header:: parse() -- Invalid sample rate.

1. Why is it always trying to open the folder as a dvd?
2. What are all these "frame types" that VLC can't support and the invalid sample rates? The music files all work fine, but these errors always appear.

---

### Post by Esthellin on 2010-03-16
Hooray for cheating! Only posting for those who look at this post.

Because vlc is broken in jaunty and the only new version are in ppas (which dont seem to work too well - too many seg faults) i found a way of just redirecting the error output to the 'black hole' of the computer.

vlc --random music 2>/dev/null

This will get all those stupid TagLib errors or any errors and basically get rid of them. This is very handy for those who use nvlc, as it messes up the interface.
Be sure that you don't accidently write:

nvlc music >/dev/null

as this will redirect ALL output to /dev/null, which results in a black screen. This is because the normal ouput is used to create the interface.

Happy listening!

---

