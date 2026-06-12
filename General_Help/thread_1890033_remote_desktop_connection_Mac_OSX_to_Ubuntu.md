---
title: "remote desktop connection Mac OSX to Ubuntu"
date: 2011-12-02
forum: General Help
---

### Post by citizenmilton on 2011-12-02
**Total n00b here.**
Trying to use Chicken of the VNC to connect to my Ubuntu desktop which has remote connection enabled.

Lucid Lynx 10.4.

**Remote desktop GUI settings:**

Allow others to view your desktop - Checked.
Allow others to control your desktop - Checked.
Others can acess your computer using this address: it says my main static IP address, the addy of my router. When I copy/paste the clickable link, it adds this format: vnc://A.B.C.D::0

You must confirm access to this machine - Unchecked
Require the user to use this password - Checked
Configure Network to automatically accept connections - Checked.

**My router settings:**

external port: 5900
internal port: 5900
protocol: (both) (options are TCP and UDP)
Forward to IP address: 192.168.1.136

**Chicken of the VNC settings:**

I've tried several, all failing.

In the HOST field, I've tried all of the following, with my router's static public IP being represented by A.B.C.D

=====

vnc://A.B.C.D::0

error - could not find a server with the name "vnc"

A.B.C.D::0

error message - "could not connect to server A.B.C.D::0 - can't assign requested address: connect()"

A.B.C.D:0

error message - "could not connect to server A.B.C.D:0 - can't assign requested address: connect()"

A.B.C.D:5900

nothing happens. the connection window disappears.

A.B.C.D::5900

 error message - "could not connect to server A.B.C.D:0 - can't assign requested address: connect()"

A.B.C.D::163

  error message - "could not connect to server A.B.C.D:0 - can't assign requested address: connect()"

and the most promising error message comes when I try this:

A.B.C.D:163

connection refused: connect ()

======

Does this final error message mean that I've finally got the correct pattern in the HOST field, and that now I need to debug something on my Ubuntu desktop?

As you can see, I'm thoroughly confused.

Thanks for your patience if you've made it this far.

-n00b


EDIT - I realize I've done a bit of dyslexic numbering with the 136 and 163.... i've tried both, BTW :)

---

