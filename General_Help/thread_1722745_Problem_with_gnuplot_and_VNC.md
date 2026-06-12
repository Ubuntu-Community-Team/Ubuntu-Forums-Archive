---
title: "Problem with gnuplot and VNC"
date: 2011-04-06
forum: General Help
---

### Post by Polines on 2011-04-06
Hello,

I have such two problems:

After the opening of VNC viewer a terminal inside passed out.
I see only white field.

Here is the log:

Tue Apr  5 14:32:40 2011
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5904
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option Window manager warning: Log level 32: could not find XKB extension.

Tue Apr  5 14:33:23 2011
 Connections: accepted: 0.0.0.0::59744
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

Tue Apr  5 14:33:26 2011
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) rgb max 3,3,3 shift 4,2,0
 VNCSConnST:  Client pixel format depth 16 (16bpp) little-endian rgb565

Tue Apr  5 14:38:44 2011
 Connections: closed: 0.0.0.0::59744 (Clean disconnection)
 SMsgWriter:  framebuffer updates 151
 SMsgWriter:    copyRect rects 52, bytes 832
 SMsgWriter:    hextile rects 299, bytes 126143
 SMsgWriter:    ZRLE rects 2, bytes 1746
 SMsgWriter:    raw bytes equivalent 3728504, compression ratio 29.154220



Other problem I have with gnuplot.
For example when I want to plot the graph:
f(x) = x
plot f(x)

I did not get the plot.

I think these two  problems are connected with X server,
but how to resolve it?

Thanks

---

### Post by Polines on 2011-04-06
Please help, guys!

---

### Post by safarin on 2011-04-06
> **Polines said:**
> Please help, guys!

gnuplot:

have you try the solution according to Gnuplot FAQ
[http://www.gnuplot.info/faq/faq.html#SECTION00092000000000000000]("http://www.gnuplot.info/faq/faq.html#SECTION00092000000000000000")

---

### Post by Polines on 2011-04-13
> **safarin said:**
> gnuplot:

have you try the solution according to Gnuplot FAQ
[http://www.gnuplot.info/faq/faq.html#SECTION00092000000000000000]("http://www.gnuplot.info/faq/faq.html#SECTION00092000000000000000")
No it doesn't work.

It seems that problem is with x11.
But I don't know what to do.

---

