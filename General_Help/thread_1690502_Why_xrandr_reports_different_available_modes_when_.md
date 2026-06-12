---
title: "Why xrandr reports different available modes when changing Ubuntu version?"
date: 2011-02-18
forum: General Help
---

### Post by GeoMX on 2011-02-18
I have minimal Ubuntu Karmic and Lucid installations, they both use Fluxbox as window manager (no Gnome nor other desktop environment), I have a script that launches fluxbox when X starts, this script also sets screen resolution, but I have a problem with the Lucid installation, it can't set resolution to 1024x768. The problem is that it is not listed as a supported mode, but it is under Karmic.

When executing xrandr --query under Karmic I get this:
[FONT="Courier New"]Screen 0: minimum 320x240, current 1024 x 768, maximum 1280 x 768
default connected 1024x768+0+0 0mm x 0mm
1280x720  60.0
1024x768  70.0*  60.0
832x624   75.0
800x600   75.0   72.0  60.0  56.0
720x450   60.0
640x480   75.0   73.0  67.0  60.0
720x400   70.0
680x384   60.0
576x432   60.0
512x384   70.0   60.0
416x312   75.0   72.0  60.0  56.0
320x240   75.0   73.0  60.0
1280x768  60.0[/FONT]

Xorg 1.6.4
xrandr 1.3.0

But under Lucid (same CPU and monitor):
[FONT="Courier New"]Screen 0: minimum 320x200, current 832 x 624, maximum 4096 x 4096
VGA-1 connected 832x624+0+0 0mm x 0mm (normal left inverted right x axis y axis) 340mm x 270mm
1280x720  59.9  60.0
832x624   74.6*
800x600   72.2  75.0  60.3  56.2
640x480   72.8  75.0  66.7  60.0
720x400   70.1

[/FONT]Xorg 1.7.6
xrandr 1.3.2

Does anybody know why do I have more modes available under Karmic? And how could I enable those "extra" modes under Lucid?

Thanks in advance for your help

---

