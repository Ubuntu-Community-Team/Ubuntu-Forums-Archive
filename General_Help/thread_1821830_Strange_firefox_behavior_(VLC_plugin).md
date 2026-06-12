---
title: "Strange firefox behavior (VLC plugin)"
date: 2011-08-09
forum: General Help
---

### Post by Pooky5 on 2011-08-09
Hi,

I have little problem with firefox, when I use mozilla vlc plugin firefox always crash. There is funny think, i use firefox Aurora (7.0a2) from repository ppa bat when i download aurora from official site mozilla and run it, everythink works just fine :-O

I have no idea why, i try uninstall and reinstall firefox bat it is still the same...:confused:

Thanks for any help

There is log from terminal:
```

worker@Worker:~$ firefox

(firefox:14131):  LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut:  assertion `gtk_accelerator_valid(key, modifier)' failed
[0xa1704e7c] main libvlc debug: VLC media player - 1.1.11 The Luggage
[0xa1704e7c] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0xa1704e7c] main libvlc debug: revision exported
[0xa1704e7c]  main libvlc debug: configured with ./configure  '--enable-static'  '--build=i686-linux-gnu' '--config-cache' '--disable-maintainer-mode'  '--disable-silent-rules' '--disable-update-check'  '--enable-fast-install' '--prefix=/usr' '--sysconfdir=/etc'  '--with-binary-version=1~lffl~natty~ppa' '--enable-a52' '--enable-aa'  '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dirac'  '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad'  '--enable-flac' '--enable-fluidsynth' '--enable-freetype'  '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack'  '--enable-kate' '--enable-libass' '--enable-libmpeg2'  '--enable-libproxy' '--enable-libxml2' '--enable-lirc'  '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod'  '--enable-mozilla' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg'  '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse'  '--enable-qt4' '--enable-realrtsp' '--enable-schroedinger'  '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb'  '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora'  '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx'  '--enable-vorbis' '--enable-x264' '--enable-zvbi'  '--with-kde-solid=/usr/share/kde4/apps/' '--with-mozilla-pkg=libxul'  '--disable-dxva2' '--disable-gnomevfs' '--disable-goom'  '--disable-osso_screensaver' '--disable-portaudio' '--disable-projectm'  '--disable-sqlite' '--disable-telx' '--enable-alsa' '--enable-atmo'  '--enable-dc1394' '--enable-dv' '--enable-libva' '--enable-pvr'  '--enable-udev' '--enable-v4l' '--enable-v4l2' '--enable-svgalib'  'build_alias=i686-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed'  'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0xa1704e7c] main libvlc debug: translation test: code is "cs"
[0xa1704e7c] main libvlc debug: checking plugin modules
[0xa1704e7c] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins-04041e-3e8.dat
[0xa1704e7c] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0xa1704e7c] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins-04041e-3e8.dat
[0xa1704e7c] main libvlc debug: module bank initialized (394 modules)
[0xa1704e7c] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 FPU 
[0xa1704e7c] main libvlc debug: looking for memcpy module: 3 candidates
[0xa1704e7c] main libvlc debug: using memcpy module "memcpymmxext"
[0xa0cd0a4c] main interface debug: looking for interface module: 1 candidate
[0xa0cd0a4c] main interface debug: using interface module "hotkeys"
[0xa0cd0afc] main interface debug: looking for interface module: 1 candidate
[0xaa521ffc] main playlist debug: Activated
[0xa0cd0afc] main interface debug: using interface module "inhibit"
[0xaa521ffc] main playlist debug: rebuilding array of current - root Seznam skladeb
[0xaa521ffc] main playlist debug: rebuild done - 0 items, index -1
[0xaa3d817c] main input debug: Creating an input for 'http://www.revolunet.com/static/download/labo/VLCcontrols/bunny.mp4'
[0xaa3d817c] main input debug: thread (input) created at priority 10 (input/input.c:220)
[0xaa3d817c] main input debug: thread started
[0xaa3d817c] main input debug: using timeshift granularity of 50 MiB
[0xaa3d817c] main input debug: using timeshift path '/tmp'
[0xaa3d817c]  main input debug:  `http://www.revolunet.com/static/download/labo/VLCcontrols/bunny.mp4'  gives access `http' demux `' path  `www.revolunet.com/static/download/labo/VLCcontrols/bunny.mp4'
[0xaa3d817c]  main input debug: creating demux: access='http' demux=''  path='www.revolunet.com/static/download/labo/VLCcontrols/bunny.mp4'
[0xaca6170c] main demux debug: looking for access_demux module: 0 candidates
[0xaca6170c] main demux debug: no access_demux module matched "http"
[0xaa3d817c] main input debug: creating access 'http' path='www.revolunet.com/static/download/labo/VLCcontrols/bunny.mp4'
[0xb176fc9c] main access debug: looking for access module: 2 candidates
[0xb176fc9c]  access_http access debug: asking libproxy about url  'http://www.revolunet.com/static/download/labo/VLCcontrols/bunny.mp4'
[0xb176fc9c] access_http access debug: libproxy suggest to use 'direct://'
[0xb176fc9c]  access_http access debug: http: server='www.revolunet.com' port=80  file='/static/download/labo/VLCcontrols/bunny.mp4'
[0xb176fc9c] main access debug: net: connecting to www.revolunet.com port 80
[0xb176fc9c] main access debug: connection succeeded (socket = 60)
[0xb176fc9c] access_http access debug: protocol 'HTTP' answer code 206
[0xb176fc9c] access_http access debug: Server: Apache/2.2.3 (Debian) PHP/5.2.0-8+etch16 mod_wsgi/2.1-BRANCH Python/2.4.4
[0xb176fc9c] access_http access debug: this frame size=13011802
[0xb176fc9c] access_http access debug: stream size=13011802,pos=0,remaining=13011802
[0xb176fc9c] access_http access debug: Content-Type: video/mp4
[0xb176fc9c] main access debug: using access module "access_http"
[0xa18eae3c] main stream debug: Using AStream*Stream
[0xa18eae3c] main stream debug: pre buffering
[0xa18eae3c] main stream debug: received first data after 0 ms
[0xa18eae3c] main stream debug: pre-buffering done 1024 bytes in 0s - 33333 KiB/s
[0xa18eaefc] main stream debug: looking for stream_filter module: 5 candidates
[0xa18eaefc] main stream debug: no stream_filter module matching "any" could be loaded
[0xa18eaefc] main stream debug: looking for stream_filter module: 1 candidate
[0xa18eaefc] main stream debug: using stream_filter module "stream_filter_record"
[0xaa3d817c]  main input debug: creating demux: access='http' demux=''  path='www.revolunet.com/static/download/labo/VLCcontrols/bunny.mp4'
[0xaca6170c] main demux debug: looking for demux module: 53 candidates
[0xaca6170c] mp4 demux warning: MP4 plugin discarded (not fastseekable)
[0xaca6170c] lua demux debug: Trying Lua scripts in /home/worker/.local/share/vlc/lua/playlist
[0xaca6170c] lua demux debug: Trying Lua scripts in /usr/lib/vlc/lua/playlist
[0xaca6170c] lua demux debug: Trying Lua playlist script /usr/lib/vlc/lua/playlist/anevia_streams.luac
Neoprávn&#283;ný p&#345;ístup do pam&#283;ti (SIGSEGV)

```

---

