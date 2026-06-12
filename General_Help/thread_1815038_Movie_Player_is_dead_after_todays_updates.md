---
title: "Movie Player is dead after todays updates"
date: 2011-07-30
forum: General Help
---

### Post by sammiev on 2011-07-30
After today's updates on 11.04 movie player stop working and loading. Went to remove it to re-install again and I could not find it in the software list. Any idea folks? Should add that VLC works fine. :)

---

### Post by IWantFroyo on 2011-07-30
Did you search for 'Totem' or 'Movie Player'?

---

### Post by sammiev on 2011-07-30
Did that and deleted just about everything possible and reinstalled. If I delete anything else I would only have windows7 left on my HD.

---

### Post by varx on 2011-08-01
I got the same problem and attempted the same fixes (uninstall, reinstall -- totem and all known components). Still no go.

Any ideas, anyone?

Like the OP, I'm running 11.04. Looks like the version of totem is 3.0.1.

---

### Post by varx on 2011-08-01
This is the screen output I get when I try to launch totem from a terminal:

$ totem
`menu_proxy_module_load': totem: undefined symbol: menu_proxy_module_load
(totem:29786): Gtk-WARNING **: Failed to load type module: (null)

I get a dozen or so of these with each failed attempt.

---

### Post by garvinrick4 on 2011-08-01
That version 3.0.1 I believe is an oneiric package for Totem I am running Natty
and do not have a few packages required for this version. This is README file from
tarball: 
```
Totem is movie player for the GNOME desktop based on GStreamer.
It features a playlist, a full-screen mode, seek and volume controls,
as well as complete keyboard navigation.

Apart from a movie player, it also includes a Mozilla plugin, and a
Nautilus thumbnailer and properties page.

News
====

See NEWS file

Dependencies
============
[COLOR=Black]
[/COLOR] [COLOR=Black]GStreamer 0.10.6, and gstreamer-plugins-base 0.10.7[/COLOR]
    http://gstreamer.freedesktop.org

GNOME 2.6 development platform
    http://www.gnome.org

gromit 20041213, for the Telestrator mode:
    http://www.home.unix-ag.org/simon/gromit/

Controls
========

Ctrl+H:
    Hide/Show controls in windowed mode
P, Ctrl+Space:
    Play/Pause
Escape (in full screen mode):
    Switch to windowed mode
Ctrl+F:
    Toggle full screen
0/½, 1, 2:
    Zoom respectively to 50%, 100% and 200% of the video's original size
Left arrow:
    Go back 15 seconds
Right arrow:
    Go forward 60 seconds
Shift+Left arrow:
    Go back 5 seconds
Shift+Right arrow:
    Go forward 15 seconds
Ctrl+Left arrow:
    Go back 3 minutes
Ctrl+Right arrow:
    Go forward 10 minutes
Up Arrow:
    Increase the volume by 8%
Down Arrow:
    Decrease the volume by 8%
Keypad Up / Keypad 8:
    DVD Action Up
Keypad Down / Keypad 2:
    DVD Action Down
Keypad Left / Keypad 4:
    DVD Action Left
Keypad Right / Keypad 6:
    DVD Action Right
B, Alt+Left arrow, Minus key:
    Previous stream (Back)
N, Alt+Right arrow, Plus key:
    Next stream (Next)
Ctrl+Q:
    Quit
Ctrl+R, Ctrl+T:
    Zoom in and zoom out, respectively
Ctrl+0:
    Reset the zoom level
Ctrl+K:
    Show the "Skip to" dialog
Ctrl+D:
    Toggle drawing using Gromit
Ctrl+E:
    Erase drawing using Gromit
Mouse button 1 double-click:
    Toggle full screen
Middle mouse button click:
    Play/Pause

Copyright
=========

Nifty media player icon by Jakub Steiner <jimmac@ximian.com>

UI help by Seth Nickell <snickell@stanford.edu>

Automatic GStreamer codec installation (optional)
================================================================
- requires GStreamer core and [COLOR=Black]gst-plugins-base >= 0.10.12[/COLOR]
- calls (via GStreamer) a predefined external helper script (which is to be
  installed by the distro and can be defined via gst-plugins-base's configure
  script when building gst-plugins-base) with details of missing GStreamer
  plugins. See
  http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-libs/html/gst-plugins-base-libs-gstpbutilsinstallplugins.html#id511743
  for more information on how this all works together.

BUGS
====

Bugs should be filed in GNOME's Bugzilla:
http://bugzilla.gnome.org/enter_bug.cgi?product=totem

To get a better debug output, run:
# totem --debug

Or for the stand-alone applications:
# gsettings set org.gnome.totem debug true
then run your application and capture its output

Contact
=======

Bastien Nocera <hadess@hadess.net>
http://www.gnome.org/projects/totem/
```EDIT: Is not running in oneiric either: Will run in Natty with version I have in repository now: 
```
Package: totem                           
State: installed
Automatically installed: no
Version: 2.32.0-0ubuntu10
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 1,733 k
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.2.4),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libfontconfig1 (>=
         2.8.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.31.1),
         libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0),
         libgstreamer-plugins-base0.10-0 (>= 0.10.30), libgstreamer0.10-0 (>=
         0.10.30), libgtk2.0-0 (>= 2.22.0), libice6 (>= 1:1.0.0),
         liblaunchpad-integration1 (>= 0.1.17), libnautilus-extension1 (>=
         2.30), libpango1.0-0 (>= 1.14.0), libpython2.7 (>= 2.7), libsm6,
         libtotem-plparser17 (>= 2.30.3), libunique-1.0-0 (>= 1.0.0), libx11-6,
         libxml2 (>= 2.6.27), libxrandr2, libxtst6, libxxf86vm1,
         gstreamer0.10-plugins-base (>= 0.10.30), gstreamer0.10-alsa |
         gstreamer0.10-audiosink, gstreamer0.10-plugins-good (>= 0.10.7),
         gstreamer0.10-x, gnome-icon-theme (>= 2.15.90), totem-common (>= 2.32),
         totem-common (< 2.33)
Recommends: totem-mozilla (>= 2.32.0-0ubuntu10), totem-plugins (>=
            2.32.0-0ubuntu10)
Suggests: gnome-codec-install, gstreamer0.10-pulseaudio (>= 0.10.16-5),
          gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad,
          gstreamer0.10-ffmpeg
Conflicts: gnome-control-center (< 2.15.90), totem (< 0.99.12-2),
           totem-gstreamer (< 2.27.1), totem-mozilla (< 2.20.0-3), totem-xine (<
           2.27.1)
Replaces: totem-common (< 2.28.1-1), totem-gstreamer (< 2.27.1), totem-xine (<
          2.27.1)
Provides: totem-gstreamer, totem-xine
Description: A simple media player for the GNOME desktop based on GStreamer
 Totem is a simple yet featureful media player for GNOME which can read a large
 number of file formats. It features : 
 
 * Shoutcast, m3u, asx, SMIL and ra playlists support 
 * DVD (with menus), VCD and Digital CD (with CDDB) playback 
 * TV-Out configuration with optional resolution switching 
 * 4.0, 5.0, 5.1 and stereo audio output 
 * Full-screen mode (move your mouse and you get nice controls) with Xinerama,
   dual-head and RandR support 
 * Aspect ratio toggling, scaling based on the video's original size 
 * Full keyboard control 
 * Simple playlist with repeat mode and saving feature 
 * GNOME, Nautilus and GIO integration 
 * Screenshot of the current movie 
 * Brightness and Contrast control 
 * Visualisation plugin when playing audio-only files 
 * Video thumbnailer for nautilus 
 * Nautilus properties page 
 * Works on remote displays 
 * DVD, VCD and OGG/OGM subtitles with automatic language selection 
 * Extensible with plugins
Homepage: http://www.gnome.org/projects/totem/

rick@rick-HP:~$ 

```
I imagine wait for fixes for the oneiric version 3.0.1 and or try to seek out and install dependencies on your own if at all possible.

---

