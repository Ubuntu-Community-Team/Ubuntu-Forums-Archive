---
title: "Gimp and XSane command-line"
date: 2010-04-04
forum: General Help
---

### Post by Flexico on 2010-04-04
OK, I want to reduce "Open Gimp, File>>Create>>XSane>>[my_scanner]" into a command-line ... line of command. XD So I can bind it to a key combo with Compiz-config. I just don't know how to find the commands to make Gimp and XSane do that.

---

### Post by ajgreeny on 2010-04-04
Using the command *man xsane* quickly produced this:-
> RUNNING UNDER THE GIMP
       To  run xsane under the gimp(1), you should at first make sure that xsane is compiled with gimp support by entering "xsane -v" on a shell.  If xsane is compiled with gimp support then  simply  set  a symbolic  link  from  the xsane-binary to one of the gimp(1) plug-ins directories.  For example, for gimp-1.0.x the command

              ln -s /usr/bin/xsane ~/.gimp/plug-ins/

       for gimp 1.2.x the command:

              ln -s /usr/bin/xsane ~/.gimp-1.2/plug-ins/

       and for gimp 2.0.x the command:

              ln -s /usr/bin/xsane ~/.gimp-2.0/plug-ins/

       adds a symlink for the xsane binary to the user's plug-ins directory.  After creating this  symlink, xsane  will  be  queried  by gimp(1) the next time it's invoked.  From then on, xsane can be invoked through "Xtns->XSane->Device dialog..." (gimp-1.0.x) or through  "File->Acquire->XSane->Device  dialog..." (gimp-1.2.x and 2.0.x) menu entry.


       SANE devices that were available at the time the xsane was queried.  Note that gimp(1) caches  these short-cuts in ~/.gimp/pluginrc.  Thus, when the list of available devices changes (e.g., a new scanner is installed or the device of the scanner has  changed),  then  it  is  typically  desirable  to rebuild  this  cache.
To  do  this,  you  can  either  touch(1)  the  xsane  binary  (e.g., "touch /usr/bin/xsane") or delete the plugin cache (e.g., "rm  ~/.gimp/pluginrc").   Either  way, invoking gimp(1) afterwards will cause the pluginrc to be rebuilt.

       When xsane is started from the gimp then it is not possible to add a devicename explicitly. You have to make the devices known to the system by configuring sane-dll, sane-net and saned.

I don't know if this helps, but it's a start, though I have to say, it all seems a rather academic exercise to me, and much easier to start gimp normally.  I do see your point about using a keybinding, however, so will keep an eye on this thread for the answer.

---

### Post by Flexico on 2010-04-04
Thank you ... you're right, that's a bit more trouble than it's worth. =P I'll keep an eye open here, too.

---

