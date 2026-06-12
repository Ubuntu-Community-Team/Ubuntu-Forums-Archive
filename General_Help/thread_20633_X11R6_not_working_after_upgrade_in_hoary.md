---
title: "X11R6 not working after upgrade in hoary"
date: 2005-03-17
forum: General Help
---

### Post by andyk on 2005-03-17
yesterday i did a clean install of hoary with no issues on my compaq laptop.  got everything working, and shut it down last night.  today when i turned it on i had updates to be installed so i went ahead and did that.  after reboot load ing got hung up and i got the "X could not start" screen.

i logged in and tried to startx manually.  it didn't work and this is the output:

/usr/X11R6/lib/modules/extensions/libGlcore.a:m_debug_clip.o_sym

"                                  "                            "                         norm.o_sym

"                                  "                             "                        xform.o_sym

the quotes are for the same output, only the last word changed.  it also said something to the effect of not being able to make a sym link and skipping.  before the update my screen worked fine, and i made no adjustments to X11 between install and upgrade.

any help/hints ?

andy

---

### Post by alastair on 2005-03-17
X logs? .....

/var/log/Xorg.0.log

and perhaps the config :

/etc/X11/xorg.conf

---

### Post by andyk on 2005-03-17
so this is odd.  when i  type in  "vi /var/log/Xorg.o.log"  and  "vi /etc/x11/Xorg.conf"

i get a run of blue tildes down half of the screen, then it says the/path/to/file and New File in brackets.  do i not have the files i'm trying to list ?

andy

---

### Post by andyk on 2005-03-17
ok tried it again and here is what i got

using config: /etc/X11/xorg.conf

using default layout
using default screen
using generic monitor
Device: ATI Technologies, Inc. Radeon 320m (RS200IGP)

goes through a whole bunch of files for xorg then at the end i get the errors

(EE) Radeon (0) the given depth (1) is not supported by the Radeon Driver.
Unload ATI
Unload Radeon
Unloading /usr/X11R6/lib/modules/drivers/radeon.drv.o

screens found none of these have usable config

FATAL Error: no screens found

edit: here is xorg.conf :

Device
  Identifier: ATI Technologies, Inc. Radeon 320m (RS200IGP)
  Driver: ati
  BusID: PCI:1:5:0

Monitor
  Identifier: Generic Monitor
  Options: DPMs

Screen
  Identifier: Default
  Device: ATI
  Monitor: Generic
  Default Depth: 1

DRI
  Mode: 0666

does this help ?


andy    ](*,)

---

