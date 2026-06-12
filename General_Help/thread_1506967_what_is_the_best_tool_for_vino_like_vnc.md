---
title: "what is the best tool for vino?? like vnc"
date: 2010-06-11
forum: General Help
---

### Post by gabak on 2010-06-11
i dont see the way to change vino ports i dont want to use 5900
i need other port.

i mean some good tool replacement or an easy way to change the ports.

---

### Post by anglican on 2010-06-11
> **gabak said:**
> i dont see the way to change vino ports i dont want to use 5900
i need other port
Why? What are you trying to achieve? More detail is needed before suggestions can be made.

H

---

### Post by gabak on 2010-06-11
scenario
two computer and one router at office.
one computer at home.
i have to have access to one or the other.

or i need a better thing than vino a good replacement

---

### Post by anglican on 2010-06-11
> **gabak said:**
> scenario
two computer and one router at office.
one computer at home.
i have to have access to one or the other.

or i need a better thing than vino a good replacement
Then it sounds like ssh tunnelling is for you. To quote from the man page for x11vnc (which is what I use for this):
 > In brief:

       % ssh -t -L 5900:localhost:5900 far-host 'x11vnc -localhost  -display :0'

       % vncviewer -encodings 'copyrect tight zrle hextile' localhost:0

       Also,  use of a VNC password (-rfbauth or -passwdfile) is strongly recommended.

       For   additional   info   see:   [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)   and
       [http://www.karlrunge.com/x11vnc/faq.html](http://www.karlrunge.com/x11vnc/faq.html)
H

---

### Post by gabak on 2010-07-18
i found the solution
aptitude install vncviewer

that will install x11vnc server that is most likely VNC and it is so easy to manage all ports and everythings
i think vino should be removed from ubuntu.

here it is an screen shot.

---

