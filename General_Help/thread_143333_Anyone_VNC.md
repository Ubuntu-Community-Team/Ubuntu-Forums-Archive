---
title: "Anyone VNC?"
date: 2006-03-12
forum: General Help
---

### Post by Cth on 2006-03-12
What is a good match to VNC from Ubuntu to Window XP?

Chris.[COLOR="Navy"]****[/COLOR]

---

### Post by 5-HT on 2006-03-12
Are you looking for a nice VNC client for Ubuntu, or VNC alternatives?

If you're looking for a viewer, there should be one already installed by default (vncviewer).

If you're trying to connect to a box outside your own network, I'd suggest tunnelling VNC through SSH.

 On linux, this is a trivial task:
```
 vncviewer -via <user>@<host> localhost:<display> 
``` 
'man vncviewer' will display the manual.

HTH

---

### Post by ronmarley1 on 2006-03-12
If I understand your question, you're looking to connect to an XP box from Ubuntu.  As long as Remote Desktop is enable on XP, you can use the Terminal Server Client Applet in Ubuntu.  One way you can add it is by right clicking on a panel and then click "Add to Panel."  Scroll through the list, or use the Search bar to find Terminal Server Client Applet (it's under the System and Hardware group).  It's very similar to MSTSC in Windows.  You can also use it to connect to systems using VNC protocol.  I use it to connect to both our Red Hat servers and our Windows servers.

---

### Post by aysiu on 2006-03-12
I use *xtightvncviewer* to access my work Windows XP computer.

---

