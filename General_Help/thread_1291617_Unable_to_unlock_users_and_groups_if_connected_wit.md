---
title: "Unable to unlock users and groups if connected with vnc"
date: 2009-10-14
forum: General Help
---

### Post by CharlesA on 2009-10-14
Seems I need to have physical access to the box to edit these with the GUI. Command line works fine.

Any way around this?

I'm using tightvnc tunneled over SSH.

---

### Post by jbrown96 on 2009-10-15
When you need to authenticate, it probably opens up a special window for security that doesn't work through vnc. The best way around this would be to either use command line tools or launch the program from the command line. Usermod is a great tool to use. ```
man usermod
``` will show you how to use the command. the other option is to find the command and then execute it with sudo. The easiest method to find the command is to drag the 'users and groups' icon to the top bar (where the firefox icon is by default), then right click on it and select properties. This will show you the command, then just run ```
sudo COMMAND-THAT-YOU-FOUND
``` in a terminal. Now that you know the command, you can delete the shortcut you just created.

---

