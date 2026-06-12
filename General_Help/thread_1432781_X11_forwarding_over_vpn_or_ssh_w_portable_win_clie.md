---
title: "X11 forwarding over vpn or ssh w/ portable win client:"
date: 2010-03-18
forum: General Help
---

### Post by klepto on 2010-03-18
I'm looking to setup X11 forwarding on my machine and secure it either with a vpn or ssh. A portable x11 client is need for access on the go. I am not sure if I am over complicating the issue but security is a must and some app I can run in windows on a thumb drive is a must.

---

### Post by cjhabs on 2010-03-18
> **klepto said:**
> I'm looking to setup X11 forwarding on my machine and secure it either with a vpn or ssh. A portable x11 client is need for access on the go. I am not sure if I am over complicating the issue but security is a must and some app I can run in windows on a thumb drive is a must.

You'll want to use xming with portable putty.
xming is the x server and putty will provide the ssh transport layer. The portable version does not write to the windows registry and can be run from a thumb drive.

---

### Post by klepto on 2010-03-18
I have everything setup nicely but I'd like to run some sort of launcher after connected instead of running gnome-terminal then running firefox or something in the terminal. That way I have a wide range of apps that I can run without guessing what the name of the executable is and where it is. 

Thanks much. 

A portable X11 client was right my alley.

---

### Post by cjhabs on 2010-03-19
> **klepto said:**
> I have everything setup nicely but I'd like to run some sort of launcher after connected instead of running gnome-terminal then running firefox or something in the terminal. That way I have a wide range of apps that I can run without guessing what the name of the executable is and where it is. 

Thanks much. 

A portable X11 client was right my alley.

The Xming Xlaunch allows you to do that - everything from a full desktop using xdmcp to just individual applications.

---

### Post by HermanAB on 2010-03-19
Howdy,

The 'standard' way to manage Unix machines from Windows is with Xmingw and PuTTY.  There is a link to Putty on the Xmingw web site.  Google will find it.

---

