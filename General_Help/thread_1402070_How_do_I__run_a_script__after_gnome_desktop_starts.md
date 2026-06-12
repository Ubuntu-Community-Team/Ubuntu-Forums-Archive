---
title: "How do I  run a script  after gnome desktop starts?"
date: 2010-02-08
forum: General Help
---

### Post by sr_guy on 2010-02-08
How do I  run a script  after gnome desktop starts? I want to run asterisk -rx reload as a command or a script AFTER gnome desktop (gui) loads, not during the boot process. 

For some reason my trunks are not loading in asterisk. If I set asterisk -rx reload in a script and run update-rc.d I can see the script run as everything boots but my trunks don't load. If I run the command after the gui loads the trunks reload and go online. Any help would be appreciated

---

### Post by Brandon Williams on 2010-02-09
If you have a script that can be run to do the initialization that you want, then you can simply create a 'Startup Application' to run your script as part of your user login session initialization. I'm not sure where that shows up in the Gnome menu structure. In Xubuntu, it's "Settings -> Session and Startup -> Application Autostart". It's probably something similar in Ubuntu.

---

