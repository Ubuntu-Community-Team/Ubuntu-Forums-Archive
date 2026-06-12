---
title: "gconftool-2 changes value only locally"
date: 2011-07-13
forum: General Help
---

### Post by ohme on 2011-07-13
In order to use vnc to access a computer at work I used to have the following alias :
slogin USR@HOST gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true ; vncviewer -via USR@HOST localhost:0 ; slogin USR@HOST gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false

upon upgrading to ubuntu 11.04 the behavior of gconftool-2 seems to have changed. The /desktop/gnome/remote_access/enabled flag now changes only locally inside the ssh session, without influencing its value on the remote open session (so running : 
gconftool-2 -g /desktop/gnome/remote_access/enabled
from within an ssh session returns true, but running the same line physically on the host returns false
)

is there a way to bypass this new behavior?
thanks...

---

