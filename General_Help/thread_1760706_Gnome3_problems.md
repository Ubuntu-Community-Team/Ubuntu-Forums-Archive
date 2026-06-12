---
title: "Gnome3 problems"
date: 2011-05-17
forum: General Help
---

### Post by jon.reeve on 2011-05-17
I'm using gnome3 from the ppa (gnome3-team) and recently it hasn't been starting--I get the sad computer icon with "something is wrong and you have to log out"--so specific, I know. Anyway I tried running gnome-shell from a terminal and this is what I get. Any ideas? 

jon@jon-laptop:~$ gnome-shell --replace
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)

GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.extensions.user-theme' is not installed

aborting...
Aborted
jon@jon-laptop:~$ gnome-shell-calendar-server[2722]: Got HUP on stdin - exiting

---

### Post by ratcheer on 2011-05-17
Sorry I cannot answer your question, but occasionally when I start my system, my Gnome 3 theme does not load. If I restart it once or twice, it usually comes back. I do not run Gnome shell extensions, though.

Strange goings on. I hope you get it worked out.

Tim

---

