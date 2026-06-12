---
title: "My VNC doesn't work again."
date: 2009-11-21
forum: General Help
---

### Post by eaglepeng on 2009-11-21
[SIZE=4]This is getting frustrating now. My VNC service doesn't work again after I upgrade to 9.1 from 8.1. I got the gray screen on the vncviewer, even the local query get the grey screen.

My Vncserver is hooked to Xinetd server so that it can start up after boot up, and can be reused. I know I need to enable the XDMCP. In 8.1, I can enable it in the login screen. But it's not there in 9.1. and I can not find the gdm.conf to enable the XDMCP neither. Why does it keep changing? Now where can I enable the XDMCP in 9.1? There's no smooth upgrade for Ubuntu ever. That sucks! :mad:
[/SIZE]

---

### Post by eaglepeng on 2009-11-21
OK, I finnally find where to enable the xdmcp. 
 
/etc/gdm/gdm.schemas
 
search for xdmcp, it is disabled by default. change the false to be true to enable the xdmcp.
 
bing! no gray screen any more!
 
Still, why keep changing the UI to mess up the user?

---

