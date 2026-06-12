---
title: "screen resolution stuck"
date: 2006-04-15
forum: General Help
---

### Post by not_yet on 2006-04-15
screen resolution stuck at 640 x 480?

system/preferences/screen resolution is set at 640x480 and there are no other options

help:confused:

---

### Post by Ramses de Norre on 2006-04-15
Are higher values enabled in /etc/X11/xorg.conf?
Look for lines like this ```
SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

```

---

### Post by sands on 2006-04-15
Yeah I too need a sol..
My friens sys gone this way...
there is also no sound..
His graphics card is some intel one..

---

### Post by sands on 2006-04-15
Yeah the lines are enabled..

---

