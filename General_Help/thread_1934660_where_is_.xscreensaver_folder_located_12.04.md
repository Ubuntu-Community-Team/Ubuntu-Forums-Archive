---
title: "where is .xscreensaver folder located? 12.04"
date: 2012-03-02
forum: General Help
---

### Post by Bill Gates Foundation on 2012-03-02
12.04

i need to edit a file for matrixview to work in xscreensaver........

[https://bugs.launchpad.net/ubuntu/+source/rss-glx/+bug/537011](https://bugs.launchpad.net/ubuntu/+source/rss-glx/+bug/537011)
> 
Okay, Reading the documentation for rss-glx, there is a README.xscreensaver file with the following information in it:
 EITHER ------------------------------------------------------------------------
    Run /usr/bin/rss-glx_install, which will look at your existing
~/.xscreensaver and add any missing entries. You probably want to back that
file up as the script is only lightly tested :)
 OR ----------------------------------------------------------------------------
     Manually add the following lines after the line that starts with "programs:"
in ~/.xscreensaver.
 -- Cut Here --
  GL:                "Cyclone"  cyclone --root                              \n\
  GL:               "Euphoria"  euphoria --root                             \n\
  GL:             "Fieldlines"  fieldlines --root                           \n\
  GL:                 "Flocks"  flocks --root                               \n\
  GL:                   "Flux"  flux --root                                 \n\
  GL:                 "Helios"  helios --root                               \n\
  GL:             "Hyperspace"  hyperspace --root                           \n\
  GL:                "Lattice"  lattice --root                              \n\
  GL:                 "Plasma"  plasma --root                               \n\
  GL:              "Skyrocket"  skyrocket --root                            \n\
  GL:             "Solarwinds"  solarwinds --root                           \n\
  GL:              "Colorfire"  colorfire --root                            \n\
  GL:           "Hufo's Smoke"  hufo_smoke --root                           \n\
  GL:          "Hufo's Tunnel"  hufo_tunnel --root                          \n\
  GL:             "Sundancer2"  sundancer2 --root                           \n\
  GL:                   "BioF"  biof --root                                 \n\
  GL:            "BusySpheres"  busyspheres --root                          \n\
  GL:            "SpirographX"  spirographx --root                          \n\
  GL:             "MatrixView"  matrixview --root                           \n\
  GL:                 "Lorenz"  lorenz --root                               \n\great, i got everything i need,.,.,., except where is the .screensaver folder??????????

edit...

never mind.......home folder, hit ctl-h to show hidden files, not a folder btw

edit II

> EITHER ------------------------------------------------------------------------
    Run /usr/bin/rss-glx_install, which will look at your existing
~/.xscreensaver and add any missing entries. You probably want to back that
file up as the script is only lightly tested :)

OR ----------------------------------------------------------------------------

    Manually add the following lines after the line that starts with "programs:"
in ~/.xscreensaver.

-- Cut Here --
  GL:                "Cyclone"  cyclone --root                              \n\
  GL:               "Euphoria"  euphoria --root                             \n\
  GL:             "Fieldlines"  fieldlines --root                           \n\
  GL:                 "Flocks"  flocks --root                               \n\
  GL:                   "Flux"  flux --root                                 \n\
  GL:                 "Helios"  helios --root                               \n\
  GL:             "Hyperspace"  hyperspace --root                           \n\
  GL:                "Lattice"  lattice --root                              \n\
  GL:                 "Plasma"  plasma --root                               \n\
  GL:              "Skyrocket"  skyrocket --root                            \n\
  GL:             "Solarwinds"  solarwinds --root                           \n\
  GL:              "Colorfire"  colorfire --root                            \n\
  GL:           "Hufo's Smoke"  hufo_smoke --root                           \n\
  GL:          "Hufo's Tunnel"  hufo_tunnel --root                          \n\
  GL:             "Sundancer2"  sundancer2 --root                           \n\
  GL:                   "BioF"  biof --root                                 \n\
  GL:            "BusySpheres"  busyspheres --root                          \n\
  GL:            "SpirographX"  spirographx --root                          \n\
  GL:             "MatrixView"  matrixview --root                           \n\
  GL:                 "Lorenz"  lorenz --root                               \n\
  GL:               "Drempels"  drempels --root                             \n\
  GL:               "Feedback"  feedback --root                             \n\
  GL:             "Pixel City"  pixelcity --root                            \n\
-- End Here --
this text works

edit IIII

> ok, i cant cut and paste the correct text, this forum is messing it up cause it has too many spaces

rss-glx is a GLX port of the Really Slick Screensavers collection by
Terry Welsh ([http://www.reallyslick.com/](http://www.reallyslick.com/)). Also included are several
other OpenGL screensavers ported from other platforms.

The screensavers can either be run as stand-alone applications or get
integrated into XScreenSaver's list of active screensavers. [COLOR=Red]More
information about using these with xscreensaver can be found in
/usr/share/doc/rss-glx.[/COLOR]

Screensavers included in this package are: Biof, Busy Spheres,
Colorfire, Cyclone, Drempels, Euphoria, Feedback, Fieldlines, Flocks, Flux,
Helios, Hufo's Smoke, Hufo's Tunnel, Hyperspace, Lattice, Lorenz Attractor,
MatrixView, Plasma, Pixel City, Skyrocket, Solarwinds, SpirographX, and
Sundancer2.

---

### Post by howefield on 2012-03-02
It is in your /home folder by the looks of it.

Open the file manager (Nautilus) which will most likely open at your /home folder and press Ctrl + H to show hidden files. The period in the path signifies a hidden file or folder.

PS. Obfuscating profanity in your postings isn't a great idea.

---

