---
title: "XGL Radeon 9800 - No direct rendering"
date: 2006-03-23
forum: General Help
---

### Post by risp on 2006-03-23
Hi!

Sorry for the new thread, I couldn't find where to post this thing.

I upgraded to Dapper, and installed ati driver with apt-get, and the followed [this]("http://www.tectonic.co.za/view.php?id=916") howto to get xgl/compiz working, so I only edited ~/.Xsession, I'll copy it to the end of my post.

It works fine, but the problem is now I don't have direct rendering enabled, though I think I somewhere saw that I should be able to use it with this card. (I saw it here: [http://gentoo-wiki.com/HOWTO_XGL#Cards_found_to_be_supported]("http://http://gentoo-wiki.com/HOWTO_XGL#Cards_found_to_be_supported"), unability for direct rendering is not pointed out, or it doesn't mean anything?)

Now with xgl I can't watch movies and tv, and can't play Elastomania & Total Soccer with wine.

What might be the problem?

Thank you

**_My files:_**

_My glxinfo says:_

risp@dusk:~$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
[...]
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 SE Generic
OpenGL version string: 1.2 (2.0.5695 (8.23.7))


_My .Xsession looks like:_

 #!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME 
exec gnome-session

_My xorg.conf's modules:_

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

---

