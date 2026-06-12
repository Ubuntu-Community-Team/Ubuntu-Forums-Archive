---
title: "Gmote not working on ubuntu"
date: 2009-12-09
forum: General Help
---

### Post by bigDs54 on 2009-12-09
hey guys was wondering if i could get some help running gmote on my ubuntu, i have successfully ran it on the xp side of my dual boot, but when i try on karmic i keep getting "connection problem" error on my phone this is what shows up on terminal

Starting GmoteServer 2.0 ... 
GmoteServer started.
rafael@rafael-laptop:~/GmoteServerLinux2.0.0$ Dec 9, 2009 5:07:10 PM org.gmote.server.GmoteServerUi sharedMain
WARNING: Gmote Version: 2.0.0
Dec 9, 2009 5:07:10 PM org.gmote.server.GmoteServerUi sharedMain
WARNING: OperatingSystem: Linux
Dec 9, 2009 5:07:11 PM org.gmote.server.settings.SupportedFiletypeSettings <init>
INFO: Initializing supported file types settings.
Dec 9, 2009 5:07:11 PM org.gmote.server.settings.SupportedFiletypeSettings <init>
INFO: Done initializing supported file types settings.
Dec 9, 2009 5:07:11 PM org.gmote.server.media.MediaPlayerManager createNewMediaPlayerInstance
INFO: Creating media player with name: org.gmote.server.media.vlc.VlcMediaPlayer
Dec 9, 2009 5:07:11 PM org.gmote.server.MulticastServerThread run
INFO: Listening for udp packets on 9901
[0x8f329838] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x8f329838] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x8f329838] main libvlc debug: translation test: code is "C"
[0x8f329838] main libvlc debug: checking plugin modules
[0x8f329838] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x8f329838] main libvlc debug: module bank initialized (375 modules)
[0x8f329838] main libvlc debug: opening config file (/home/rafael/.config/vlc/vlcrc)
[0x8f329838] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x8f329838] main libvlc debug: looking for memcpy module: 3 candidates
[0x8f329838] main libvlc debug: using memcpy module "memcpymmxext"
[0x8d282520] main input debug: Creating an input for 'Media Library'
[0x8d282520] main input debug: Input is a meta file: disabling unneeded options
[0x8d282520] main input debug: using timeshift granularity of 50 MBytes
[0x8d282520] main input debug: using timeshift path '/tmp'
[0x8d282520] main input debug: `file/xspf-open:///home/rafael/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/rafael/.local/share/vlc/ml.xspf'
[0x8d282520] main input debug: creating demux: access='file' demux='xspf-open' path='/home/rafael/.local/share/vlc/ml.xspf'
[0x8d278330] main demux debug: looking for access_demux module: 1 candidate
[0x8d278330] main demux warning: no access_demux module matching "file" could be loaded
[0x8d278330] main demux debug: TIMER module_need() : 0.162 ms - Total 0.162 ms / 1 intvls (Avg 0.162 ms)
[0x8d282520] main input debug: creating access 'file' path='/home/rafael/.local/share/vlc/ml.xspf'
[0x8d283f48] main access debug: looking for access module: 3 candidates
[0x8d283f48] access_file access debug: opening file `/home/rafael/.local/share/vlc/ml.xspf'
[0x8d283f48] main access debug: using access module "access_file"
[0x8d283f48] main access debug: TIMER module_need() : 0.305 ms - Total 0.305 ms / 1 intvls (Avg 0.305 ms)
[0x8d2784a8] main stream debug: Using AStream*Stream
[0x8d2784a8] main stream debug: pre buffering
[0x8d2784a8] main stream debug: received first data after 0 ms
[0x8d2784a8] main stream debug: pre-buffering done 363 bytes in 0s - 14179 kbytes/s
[0x8d284848] main stream debug: looking for stream_filter module: 4 candidates
[0x8d284848] main stream debug: TIMER module_need() : 0.123 ms - Total 0.123 ms / 1 intvls (Avg 0.123 ms)
[0x8d284818] main stream debug: looking for stream_filter module: 1 candidate
[0x8d284818] main stream debug: using stream_filter module "stream_filter_record"
[0x8d284818] main stream debug: TIMER module_need() : 0.100 ms - Total 0.100 ms / 1 intvls (Avg 0.100 ms)
[0x8d282520] main input debug: creating demux: access='file' demux='xspf-open' path='/home/rafael/.local/share/vlc/ml.xspf'
[0x8d284978] main demux debug: looking for demux module: 1 candidate
[0x8d284978] playlist demux debug: using XSPF playlist reader
[0x8d284978] main demux debug: using demux module "playlist"
[0x8d284978] main demux debug: TIMER module_need() : 0.120 ms - Total 0.120 ms / 1 intvls (Avg 0.120 ms)
[0x8d282520] main input debug: `file/xspf-open:///home/rafael/.local/share/vlc/ml.xspf' successfully opened
[0x8d287860] main xml debug: looking for xml module: 2 candidates
[0x8d287860] main xml debug: using xml module "xtag"
[0x8d287860] main xml debug: TIMER module_need() : 0.114 ms - Total 0.114 ms / 1 intvls (Avg 0.114 ms)
[0x8d284978] playlist demux debug: parsed 0 tracks successfully
[0x8d287860] main xml debug: removing module "xtag"
[0x8d282520] main input debug: EOF reached
[0x8d284978] main demux debug: removing module "playlist"
[0x8d284818] main stream debug: removing module "stream_filter_record"
[0x8d283f48] main access debug: removing module "access_file"
[0x8d282520] main input debug: TIMER input launching for 'Media Library' : 7.385 ms - Total 7.385 ms / 1 intvls (Avg 7.385 ms)
[0x8d2723f0] main playlist debug: Activated
[0x8d2723f0] main playlist debug: rebuilding array of current - root Playlist
[0x8d2723f0] main playlist debug: rebuild done - 0 items, index -1
[0x8d2846b8] main interface debug: looking for interface module: 1 candidate
[0x8d2846b8] main interface debug: using interface module "hotkeys"
[0x8d2846b8] main interface debug: TIMER module_need() : 0.211 ms - Total 0.211 ms / 1 intvls (Avg 0.211 ms)
[0x8d2846b8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8d2846b8] main interface debug: thread started
[0x8d286760] main interface debug: looking for interface module: 1 candidate
[0x8d286760] main interface debug: using interface module "hotkeys"
[0x8d286760] main interface debug: TIMER module_need() : 0.208 ms - Total 0.208 ms / 1 intvls (Avg 0.208 ms)
[0x8d286760] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8d286760] main interface debug: thread started
[0x8d287ff0] main interface debug: looking for interface module: 1 candidate
[0x8d287ff0] main interface debug: using interface module "inhibit"
[0x8d287ff0] main interface debug: TIMER module_need() : 1.668 ms - Total 1.668 ms / 1 intvls (Avg 1.668 ms)
[0x8d287ff0] main interface debug: thread started
[0x8d287ff0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8d2781b0] main interface debug: looking for interface module: 1 candidate
[0x8d2781b0] main interface debug: using interface module "screensaver"
[0x8d2781b0] main interface debug: TIMER module_need() : 0.130 ms - Total 0.130 ms / 1 intvls (Avg 0.130 ms)
[0x8d2781b0] main interface debug: thread started
[0x8d2781b0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
Dec 9, 2009 5:07:11 PM org.gmote.server.GmoteServer startServer
INFO: Waiting for TCP connection on port: 8889
Waiting for a connection on port: 8889
Dec 9, 2009 5:07:45 PM org.gmote.server.MulticastServerThread handleServiceDiscoveryRequest
INFO: Received an ip request
Dec 9, 2009 5:07:48 PM org.gmote.server.MulticastServerThread handleServiceDiscoveryRequest
INFO: Received an ip request
Dec 9, 2009 5:07:51 PM org.gmote.server.MulticastServerThread handleServiceDiscoveryRequest
INFO: Received an ip request

any ideas? thanks

---

### Post by bigDs54 on 2009-12-09
ps the phone is a G1 running dwangs 1.13 rom and the laptop is a dual boot running XP and Ubuntu 9.10

---

### Post by bigDs54 on 2009-12-10
:( no one?

---

### Post by bigDs54 on 2009-12-12
???

---

### Post by Maheriano on 2010-03-17
Did you try connecting via your phone? The application just sits there waiting for information from your phone so try that.

I just got mine running:

[http://www.youtube.com/watch?v=3QzfRSACDlc](http://www.youtube.com/watch?v=3QzfRSACDlc)

---

