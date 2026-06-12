---
title: "black screen when I try to take a screen shot"
date: 2010-05-15
forum: General Help
---

### Post by trollger on 2010-05-15
When I try and take a screen shot of my work space all I get is a black screenwith a cursror. This happens with Ubuntu's inbuilt screen shot app and with shutter.:confused:

---

### Post by mario.kemper on 2010-05-16
Could you please start Shutter in debug-mode via terminal and attach/post the output here?
shutter --debug

---

### Post by CuXe on 2010-07-09
I'll start by saying that I am an ubuntu noob so bare with me pls :)

I am having the very same problem.  When I try to take a screenshot the preview pane shows a black image and when I go to the location where the screenshot should have been saved all I see is a black image....

Any ideas? Any1?

EDIT:

Following the request above here is the output from Shutter:

> 
INFO: checking installed components...

WARNING: gnome-web-photo is missing --> screenshots of websites will be disabled!

WARNING: Goo::Canvas/libgoocanvas is missing --> drawing tool will be disabled!

INFO: command debug recognized!


INFO: gathering system information...

Linux ivan-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

Ubuntu 10.04 LTS \n \l


Glib 1.222 
Gtk2 1.221 

Glib built for 2.22.2, running with 2.24.0
Gtk2 built for 2.20.0, running with 2.20.0

3D rotate - /usr/share/shutter/resources/system/plugins/perl/sp3drotate/sp3drotate
Barrel Distortion - /usr/share/shutter/resources/system/plugins/perl/spbardistortion/spbardistortion
Negate - /usr/share/shutter/resources/system/plugins/perl/spnegate/spnegate
Polaroid - /usr/share/shutter/resources/system/plugins/perl/sppolaroid/sppolaroid
Resize - /usr/share/shutter/resources/system/plugins/perl/spresize/spresize
Sepia - /usr/share/shutter/resources/system/plugins/perl/spsepia/spsepia
Watermark - /usr/share/shutter/resources/system/plugins/perl/spwatermark/spwatermark
Shutter Branding - /usr/share/shutter/resources/system/plugins/shell/spaddlogo/spaddlogo
Grayscale - /usr/share/shutter/resources/system/plugins/shell/spgrayscale/spgrayscale
Jigsaw Piece 1 - /usr/share/shutter/resources/system/plugins/shell/spjigsaw1/spjigsaw1
Jigsaw Piece 2 - /usr/share/shutter/resources/system/plugins/shell/spjigsaw2/spjigsaw2
Offset - /usr/share/shutter/resources/system/plugins/shell/spoffset/spoffset
PDF Export - /usr/share/shutter/resources/system/plugins/shell/sppdf/sppdf
Raise Border - /usr/share/shutter/resources/system/plugins/shell/spraise/spraise
Hard Shadow - /usr/share/shutter/resources/system/plugins/shell/spshadow/spshadow
Reflection - /usr/share/shutter/resources/system/plugins/shell/spsimplemirror/spsimplemirror
Soft Edges - /usr/share/shutter/resources/system/plugins/shell/spsoftedges/spsoftedges
Sunk Border - /usr/share/shutter/resources/system/plugins/shell/spsunk/spsunk
Torned Paper - /usr/share/shutter/resources/system/plugins/shell/sptornedpaper/sptornedpaper
shutter_wrksp_direct_compiz0x0
shutter_wrksp_direct_compiz1920x0
shutter_wrksp_direct_compiz3840x0
shutter_wrksp_direct_compiz5760x0

type_changed was emitted by widget Gtk2::ComboBox=HASH(0x9232c00)

cursor_toggled was emitted by widget Gtk2::CheckButton=HASH(0x921eca8)

cursor_status_toggled was emitted by widget Gtk2::CheckButton=HASH(0xa689b78)

progname_toggled was emitted by widget Gtk2::CheckButton=HASH(0xa6e4050)

im_colors_changed was emitted by widget Gtk2::ComboBox=HASH(0xa6e40a0)

im_colors_toggled was emitted by widget Gtk2::CheckButton=HASH(0xa6e3f50)

thumbnail_changed was emitted by widget Gtk2::HScale=HASH(0xa6e4160)

thumbnail_toggled was emitted by widget Gtk2::CheckButton=HASH(0xa711e48)

menu_delay_changed was emitted by widget Gtk2::SpinButton=HASH(0xa6e43d0)

keybinding_toggled was emitted by widget Gtk2::CheckButton=HASH(0xa6e4490)

keybinding_sel_toggled was emitted by widget Gtk2::CheckButton=HASH(0xa71f2c0)

keybinding_sel_toggled was emitted by widget Gtk2::CheckButton=HASH(0xa71f2c0)

hide_time_changed was emitted by widget Gtk2::SpinButton=HASH(0xa71f320)



---

