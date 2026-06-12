---
title: "Various software troubles."
date: 2009-12-25
forum: General Help
---

### Post by Marvin666 on 2009-12-25
1: I can't get flash to work in firefox.
2: Supertuxkart won't run smoothly, and the laptimer is slowed way down.
3: VLC won't play a dvd.
4: Ksirk crashes
5: Knetwalk locks up.

---

### Post by infinitejones on 2009-12-25
What have you tried doing already to solve these problems?

Just asking so that people don't waste your time or their own by suggesting ways of solving these problems that you've found and tried already. By searching Google or Ubuntu Forums, for example.

---

### Post by Marvin666 on 2009-12-25
I've done the install restricted extras fix said to make youtube videos work, but no 
I think vlc is having a copy-protection issue. I found out how to play a dvd from a terminal, and the screen is filled with the following: ```

marvin@Local-Machine:~$ vlc dvd:\\
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Could not open input: No such file or directory
libdvdread: Can't open dvd:\ for reading
libdvdnav: vm: failed to open/read the DVD
[00000413] access_directory access error: dvd:\: No such file or directory
[00000413] access_file access error: cannot open file dvd:\ (No such file or directory)
[00000407] main input error: open of `dvd:\' failed: could not create access: no suitable access module
^C[00000402] signals interface error: Caught Interrupt signal, exiting...
marvin@Local-Machine:~$ cls
bash: cls: command not found
marvin@Local-Machine:~$ clear

marvin@Local-Machine:~$ vlc dvd://
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: DETHKLOK
libdvdnav: DVD Serial Number: 3affbe08
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/marvin/.dvdnav/DETHKLOK.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

```EDIT: Tried the following fix I found, but it had no effect. sudo chmod 666 /dev/dvd
Kirsk gives the following the follwing error:   p, li { white-space: pre-wrap; }  A Fatal Error Occurred
 The application KsirK (ksirk) crashed and caused the signal 11 (SIGSEGV).
Under a box for what I assume is the stacktrace, it says unable to create valid stacktrace.

---

### Post by infinitejones on 2009-12-26
OK, the output from VLC shows that you don't have the packages installed to decrypt the DVDs. Medibuntu should help you here...

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Have a good read through - the main sections you'll want to look at are "Adding the Repository" and then scroll down a bit for "Playing Encrypted DVDs". Should be nice and straightforward.

With a bit of luck, that might solve the Firefox/Flash problem too. I've never really had that problem so I haven't ever had to solve it - however if you do some Googling I'm sure you'll find details of how other people have.

The other three - personally I can't help you! There must be other people who can though... just try and post as much detail as possible about what's going wrong, what the terminal output is, etc etc.

---

### Post by Leppie on 2009-12-26
1. did you check the plugin is actually enabled? in ff, go to Tools>Add-ons, click the Plugins tab and scroll down to Shockwave Flash, click the button if it states "Enable".

2. is this only with tuxracer, or do you have other general graphics issues? this may have something to do with your driver.

3. run the following script:
```
$sudo /usr/share/doc/libdvdread4/install-css.sh
```
some dvd's require css2, you can install it from the medibuntu repo.

4. sorry, i'm not familiar with Ksirk

5. nor with knetwalk, but could be related to 2?

---

### Post by 4Orbs on 2009-12-26
To fix some of your issues, [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=766683") should be your first stop after a new install of any ^buntu. In the two years I've been using Ubuntu and its spinoffs, the Multimedia and Video how-to has worked every time (for dozens of different installations).

---

### Post by Marvin666 on 2009-12-26
Thanks for the link, now I have vlc and flash working.
I played with the settings more on supertuxkart, and payed attention to heat and fan speed. I think it's using too much cpu time. Is there a setting in one of it's config files for frames per second, or quality?

---

