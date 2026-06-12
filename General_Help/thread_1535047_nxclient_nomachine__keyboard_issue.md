---
title: "nxclient nomachine  keyboard issue"
date: 2010-07-20
forum: General Help
---

### Post by faugeras on 2010-07-20
Hi,
I used to work under ubuntu 9.04 on a dell latitude D830 laptop. I installed nomachine nxclient to work remotely on a server.  At that time a bug was clearly identified by nomachine, the keyboard did not map correctly and for exemple the up-arrow key gave a screen-print. The solution for this issue was to add in the xorg.conf of the laptop:
Section "ServerFlags"
    Option "AutoAddDevices" "false"
EndSection

Indeed this worked quite fine (for the keyboard at least, but the sound control was screwed).
Recently I upgraded to ubuntu 10.04, modified my xorg.conf in the same way to fix the keyboard issue when using nomachine, restarted the X server, and what happened then... the keyboard was completely deactivated. 
I've been looking around on google for a solution to this issue but haven't found much. I believe this is partly due to the new xserver-xorg-input-evdev package. Does any body have a solution to propose?
Thanks
Blaise

---

### Post by faugeras on 2010-07-26
Anybody for this issue? Am  I alone with this?

---

### Post by Murz on 2010-07-27
I have the same problem but can't find the solution at now.
Subscribe to bug: [https://bugs.launchpad.net/ubuntu/+bug/361903](https://bugs.launchpad.net/ubuntu/+bug/361903)

---

### Post by iceback on 2010-09-19
I'm using nx server 3.4.0-14 on an ubuntu-10.4 and Suse-11.2(?)

The problem I have with clients on both servers is that I cannot swap ctrl and capslock keys.  Against the Suse server the nxclient doesn't start the control panel tool to do the swap (glib/gnome failure) and against the ubuntu server (client connecting to localhost in this case) neither "swap ctrl, capslock" nor "capslock as a control key" take effect).

---

