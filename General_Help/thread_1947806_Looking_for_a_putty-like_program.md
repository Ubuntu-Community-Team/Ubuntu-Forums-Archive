---
title: "Looking for a putty-like program"
date: 2012-03-27
forum: General Help
---

### Post by hiro24 on 2012-03-27
Question for you guys.  I know putty is available for Linux, and I have it installed, it's working good.  What I'm looking for, really, is a way to import saved sessions into the unity button for putty, or a similar program.  Much like right clicking the chrome icon in the unity bar will offer a few different options, as will terminal, I'd like to find something that allows me to save pre-defined ssh connections in a way that they are accessed via right clicking the icon, to save some time.  I'm not sure if this exists, or how to set it up.  I'm a bit new to unity.  Anybody have any suggestions?

---

### Post by hiro24 on 2012-03-27
nevermind, figured it out... much like changing the home button around to display different areas on right click.  Edited /usr/share/applications/putty.desktop and added in the needed lines.

---

### Post by Paqman on 2012-03-27
Glad you've sorted it.

Btw, did you know that on Ubuntu you can connect over SSH by default. Opening a terminal and typing:
```
ssh username@IPaddress
```
...will connect you easy peasy. If you wanted to save the details you can just create an [alias]("http://ubuntuforums.org/showthread.php?t=89732").

---

