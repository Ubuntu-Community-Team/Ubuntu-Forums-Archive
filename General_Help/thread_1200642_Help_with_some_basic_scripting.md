---
title: "Help with some basic scripting"
date: 2009-06-30
forum: General Help
---

### Post by eyeJ on 2009-06-30
Here's a script i use to start 3dx driver and run maya, and when maya closes it stops the 3dx driver so that the 3dx window doesn't bother me.

Basically i just need to run and kill the 3dx driver with sudo but not maya or other commands.

here's the script:

---------------------------------------
#!/bin/bash

/etc/3DxWare/daemon/3dxsrv -d usb &
export MAYA_MMSET_DEFAULT_XCURSOR=1;
maya;
killall -15 3dxsrv
---------------------------------------

so the question is how can i use sudo for these two commands in the script without running the whole script as sudo:

/etc/3DxWare/daemon/3dxsrv -d usb &
killall -15 3dxsrv

it would be great if i can set this as a launcher and not have to input the password every time :|

Thank you for helping in advance! :)

---

