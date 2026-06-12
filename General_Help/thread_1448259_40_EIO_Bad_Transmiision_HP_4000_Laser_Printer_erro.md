---
title: "40 EIO Bad Transmiision HP 4000 Laser Printer error"
date: 2010-04-06
forum: General Help
---

### Post by sdowney717 on 2010-04-06
[https://bugs.launchpad.net/hplip/+bug/521174](https://bugs.launchpad.net/hplip/+bug/521174)

This bug affects me too.
In Karmic-Lucid, The printer prints the page ok, but this error appears.
In Vista, this error does not appear on the printer message board.

Anyone have a solution?

[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/229981](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/229981)
Ok, this fixed it. I simply added a new printer and told it to find it and then selected connection type to APPSocket/HP JetDirect

> 

I'm using 9.04 - the Jaunty Jackalope

I had the same problem with a hp 4050 tn printer and every other driver worked except the HP Laserjet 4050 Series Postscript [en] (recommended)
This was great no errors but couldn't setup duplexer or 3rd tray for the printer.

this was using the default HP Linux Imaging and Printing (HPLIP)

I changed the connection type to APPSocket/HP JetDirect

and off it went no errors and no problems accessing duplexer or 3rd tray.

not a fix but maybe a workaround for the problem so people can use trays or duplex units.


---

