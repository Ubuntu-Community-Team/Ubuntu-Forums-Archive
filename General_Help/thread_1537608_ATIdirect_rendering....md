---
title: "ATI/direct rendering..."
date: 2010-07-23
forum: General Help
---

### Post by Zorgoth on 2010-07-23
I can't get direct rendering to work with my mobility radeon hd 5470 (Dell Studio 15).  Compiz works and glxgears gives ~25000 fps, but even in metacity I don't get direct rendering.  I am using the proprietary drivers from "Hardware Drivers."  Any suggestions?

---

### Post by Zorgoth on 2010-07-26
I am getting around it by using launchers like this one:

screen -d -m bash -c "unset LIBGL_ALWAYS_INDIRECT && do_whatever"

screen is a program which will basically allow me to view the terminal output and stuff without having a terminal window open all the time.  If you are not afraid of the command line and do not know hat screen is, find out; it's worth it.  If you don't feel like you need screen you could also just use

bash -c "unset LIBGL_ALWAYS_INDIRECT && do_whatever"

---

