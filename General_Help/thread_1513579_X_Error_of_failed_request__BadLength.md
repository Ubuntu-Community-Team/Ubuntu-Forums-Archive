---
title: "X Error of failed request:  BadLength"
date: 2010-06-19
forum: General Help
---

### Post by neonic on 2010-06-19
Hello, I'm new to ubuntu.

When I try to start a certain application from the terminal, I get the following message:

> 
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14
If I try to run the application from the panel, it just doesn't start.

This application used to run until recently.
I think it's caused by the fact that I've tried to install fglrx. It didn't work, so I removed it again, but since then I get this Error.

My "/etc/X11/xorg.conf" file isn't present, if I fill it with

[quote]

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

[quote]

Then the error doesn't appear, but 3d applications run slow.

Also, according to this page : [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), I shouldn't need a xorg.conf file for my radeon 1600XP driver

Does anyone know how to solve this?

Thanks!

---

### Post by Winged Owl on 2011-10-19
Hello,
  I am also suffering from a highly similar error.  in c++, g++, I am trying to compile opengl/glut code and here is the compiler error I get:

X Error of failed request: BadLength (poly request too large or internal xlib length error)
    Major opcode of failed request: 152 (GLx)
    Minor opcode of failed request: 17 (X_glXVendorPrivateWithReply)
    Serial number of failed request: 27
    Current serial number in output stream: 27

I am pretty sure that I compiled this earlier, and it worked, and now it won't work.
I used tracking cout statements and it seems to crash at a glut function call of :
glutCreateWindow( filename );    

I would really appreciate help in this subject, thanks in advance!

---

### Post by fatigue on 2011-10-20
I'm having same issues.
I use molecular dynamic software like avogadro,viewmol.
It was working last week but it suddenly stopped working.
Please help us out

---

