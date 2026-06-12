---
title: "vino: access prompt control via config editing"
date: 2011-05-13
forum: General Help
---

### Post by Lexus45 on 2011-05-13
Hi guys.
After searching the forum and getting no results, I'd like to ask here.

_The idea_: vino: access prompt control via config editing.

_The situation_:
I have a remote access via SSH and VNC to a Ubuntu PC. We know that in vino-preferences there's a checkbox wich controls if anybody can connect via VNC to this machine or not. When our clients are in front of their PCs, it's OK.

But sometimes I need access to their desktop even when they are away from PC. So, nobody can press the button and let me "log in".

But I have a full access to the PC via SSH. I tried to edit [COLOR=Green]~/.gconf/desktop/gnome/remote_access/%gconf.xml[/COLOR] where I've found the line [COLOR=Green]<entry name="prompt_enabled" mtime="1305104364" type="bool" value="**true**"/>[/COLOR] but when I've changed 'true' to 'false', nothing changed.

How can I activate/deactivate the prompt via SSH-access?

Best regards, Lexus45

---

