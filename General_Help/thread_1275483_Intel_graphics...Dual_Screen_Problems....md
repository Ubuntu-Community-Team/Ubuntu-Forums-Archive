---
title: "Intel graphics...Dual Screen Problems..."
date: 2009-09-25
forum: General Help
---

### Post by BarefootSoul83 on 2009-09-25
I had dual screen working @ one point... I dont see anything in my xorg.conf that indicates the driver.  I am on a Toshiba Satellite with Intel graphics... any suggestions? (xorg.conf ....below)

-------------------------------------------------------------------------

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2720 1924
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "false"

---

### Post by Woody1987 on 2009-09-26
try using the display configuration tool in system->preferences to setup dual screen.

---

